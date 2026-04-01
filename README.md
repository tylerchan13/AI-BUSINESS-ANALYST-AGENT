 # 🚀 AI BUSINESS ANALYST AGENT
## 基于 RAG 技术的智能商业分析系统 (RAG-Powered Business Analysis)

---

## 📌 项目特性
### Intelligent Document Retrieval | 智能文档检索
- 基于FAISS的向量相似度搜索（FAISS-based vector similarity search）
- 支持多种文档格式（TXT, MD, PDF, 等）（Supports multiple document formats）

### LLM-Powered Analysis | 大语言模型驱动分析
- 集成OpenAI GPT-4（OpenAI GPT-4 integration）
- 生成结构化商业报告（Structured business report generation）
- 咨询级输出质量（Consulting-grade output quality）

### Modular Architecture | 模块化架构
- 清晰的模块分离（RAG, Agent, Utils）（Clean separation: RAG, Agent, Utils）
- 易于扩展和定制（Easy to extend and customize）

### Web Interface | Web界面
- 简洁的Streamlit界面（Simple Streamlit UI）
- 实时报告生成（Real-time report generation）

---

## 🏗️ 系统架构
```text
User Query (e.g., "Analyze China's coffee market")
    |
    v
[RAG Module]
  - Document Loader -> Embeddings Generator -> FAISS Index
  - Retrieves: Top-K relevant context chunks
    |
    v
[Agent Module]
  - Query + Context -> LLM (OpenAI GPT-4)
  - Generates: Structured business report
    |
    v
Output:
  - Market Overview
  - Key Players
  - SWOT Analysis
  - Recommendations
```

---

## 🔧 技术栈
| Component | Technology |
|-----------|------------|
| Language  | Python 3.10+ |
| LLM       | OpenAI GPT-4 |
| Embeddings| Sentence Transformers |
| Vector Store | FAISS |
| Web UI    | Streamlit |
| Config    | python-dotenv |

---

## 📦 快速启动
### 1. INSTALLATION | 安装
```bash
git clone <repo-url>
cd <project-dir>

# 创建并激活虚拟环境
python -m venv venv
source venv/bin/activate  # Windows系统: venv\Scripts\activate

# 安装依赖
pip install -r requirements.txt
```

### 2. CONFIGURATION | 配置
```bash
cp .env.example .env

# 编辑.env文件，添加你的OpenAI API密钥
OPENAI_API_KEY=sk-your-key-here
```

### 3. RUN | 运行
```bash
# 命令行模式 (CLI Mode)
python main.py

# Web界面模式 (Web UI)
streamlit run app.py
```

---

## 📂 项目结构
```text
ai-business-analyst/
  app.py                  # Streamlit web界面
  main.py                 # CLI入口文件
  config.py               # 配置管理
  requirements.txt        # 依赖清单
  .env.example           # 环境变量模板

  agent/                  # Agent模块
    agent.py              # 核心Agent类

  rag/                    # RAG组件
    retriever.py          # 文档检索
    embeddings.py         # 嵌入模型(Sentence Transformers)
    vector_store.py       # FAISS向量存储
    processor.py          # 文档处理

  utils/                  # 工具类
    llm_client.py         # OpenAI集成

  data/                   # 文档存储目录
    *.txt                 # 示例文档
    vector_store/         # FAISS索引存储
```

---

## 📖 使用示例
```python
from config import Settings
from agent import create_agent

# 初始化Agent
settings = Settings()
agent = create_agent(settings, data_directory="./data")

# 发起分析查询
result = agent.query("Analyze China's coffee market")

# 打印结构化报告
print(result["report"])
```

---

## 📊 输出示例
```text
==============================================================================
1. MARKET OVERVIEW | 市场概览
==============================================================================
China's coffee market has experienced remarkable growth, reaching
approximately 30 billion RMB in 2023 with a sustained CAGR of 15-20%.
The market is transitioning from niche to mainstream, driven by
urbanization and westernization trends among millennials and Gen Z.

中国市场增长显著，2023年规模约300亿元人民币，年复合增长率15-20%。
在千禧一代和Z世代的城镇化和西化趋势推动下，市场正从小众走向主流。

==============================================================================
2. KEY PLAYERS | 主要参与者
==============================================================================
  Starbucks (6,500+ stores) - Premium positioning, brand prestige
  Luckin Coffee (10,000+ stores) - Tech-enabled, value-focused
  Cotti Coffee - Rapid expansion, budget-friendly
  Manner - Quality-focused, regional strength

==============================================================================
3. SWOT ANALYSIS | SWOT分析
==============================================================================
STRENGTHS | 优势:
  - Growing middle class with disposable income
  - Digital-native consumer behavior

WEAKNESSES | 劣势:
  - Tea remains deeply culturally entrenched
  - Price sensitivity in lower-tier cities

OPPORTUNITIES | 机会:
  - Tier-2 and Tier-3 city expansion
  - Health-conscious product development

THREATS | 威胁:
  - Market saturation in Tier-1 cities
  - Intense price competition

==============================================================================
4. RECOMMENDATIONS | 建议
==============================================================================
1. Prioritize lower-tier city expansion with value-focused offerings
2. Invest in digital capabilities and loyalty programs
3. Develop health-conscious and plant-based product lines
4. Leverage domestic coffee production for "Grown in China" branding
```

---

## ⚙️ 配置选项
| Variable | Description | Default |
|----------|-------------|---------|
| OPENAI_API_KEY | OpenAI API密钥（必填） | - |
| EMBEDDING_MODEL | Sentence Transformers嵌入模型 | all-MiniLM-L6-v2 |
| CHUNK_SIZE | 文档分片大小 | 1000 |
| CHUNK_OVERLAP | 分片重叠度（用于上下文关联） | 200 |
| VECTOR_STORE_PATH | FAISS索引存储路径 | ./data/vector_store |

---

## 📋 依赖要求
- Python 3.10+
- OpenAI API key（需自行申请）

### 主要依赖包
```text
openai>=1.0.0
faiss-cpu>=1.7.4
sentence-transformers>=2.2.0
streamlit>=1.28.0
python-dotenv==1.0.0
```

---

## 📜 许可证
MIT License - 可自由用于学习和生产环境（feel free to use this project for learning and production.）

---

## 🤝 贡献指南
欢迎大家贡献代码！请随时提交Pull Request。（Contributions are welcome! Please feel free to submit a Pull Request.）

---

Built with love using RAG + OpenAI
