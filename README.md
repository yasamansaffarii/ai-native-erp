# AI-Native ERP for a Small Trading Organization

**An AI-powered ERP prototype built, operated, and extended with free-tier AI services.**

This project explores a different approach to Enterprise Resource Planning (ERP): instead of treating AI as an add-on, AI is integrated into the system's core architecture—from natural-language data access and organizational knowledge retrieval to operational analytics, procurement support, and AI-assisted software development.

The prototype runs in Google Colab using free-tier resources, SQLite, open-source embedding models, and free-tier LLM APIs. It requires no GPU, model fine-tuning, or paid infrastructure for the intended demonstration workflow.

---

## Overview

The system provides a unified AI-powered interface for querying business data, retrieving organizational knowledge, generating analytical insights, supporting procurement decisions, and extending the ERP through AI-generated plugins.

The project uses the Northwind SQLite database, a publicly available ERP-style sample dataset representing a fictitious trading company.

### Key Features

- **ERP Copilot:** Natural-language interface supporting English and Persian, with automatic routing to specialized tools.
- **Text-to-SQL Agent:** Converts natural-language questions into SQL queries, validates them, executes them safely, and attempts self-repair when necessary.
- **Retrieval-Augmented Generation (RAG):** Retrieves relevant information from business records, organizational documents, policies, and verified SQL examples.
- **Business Forecasting:** Forecasts revenue using classical time-series methods and backtesting.
- **Inventory Replenishment:** Identifies products requiring replenishment and estimates suggested order quantities.
- **Anomaly Detection:** Detects unusual transaction patterns using Isolation Forest.
- **Customer Segmentation:** Performs RFM-based customer segmentation using K-means clustering.
- **Procurement Agent:** Drafts purchase orders and supporting justifications, with human approval required before approval status is granted.
- **AI Dev Studio:** Generates new analytical modules, creates tests, executes test suites, attempts bounded self-repair, performs AI-assisted review, and registers successful modules as plugins.
- **Governance and Auditability:** Includes SQL safety checks, read-only analytical access, static code guards, regression testing, and audit logging.

---

## Architecture

The system is organized into five main layers:

1. **Data Layer** — Northwind SQLite database and AI-owned operational tables.
2. **Semantic and Retrieval Layer** — Schema-adaptive SQL views, organizational profile, and vector index.
3. **AI Tool Layer** — Specialized agents and analytical tools.
4. **Copilot Router** — LLM-based routing of user requests to the appropriate tool.
5. **User Interface** — Gradio-based interface for interacting with the ERP.

### AI Components

| Component | Purpose |
|---|---|
| Text-to-SQL | Natural-language business queries |
| RAG | Context-grounded knowledge retrieval |
| Forecasting | Revenue forecasting and backtesting |
| Replenishment | Inventory monitoring and reorder planning |
| Anomaly Detection | Identification of unusual order-line patterns |
| Customer Segmentation | RFM-based segmentation |
| Procurement Agent | Purchase-order drafting and approval workflow |
| AI Dev Studio | AI-generated, tested, reviewed, and registered ERP plugins |

---

## Technology Stack

- **Runtime:** Google Colab
- **Database:** SQLite
- **LLM APIs:** Gemini API and/or Groq API
- **Embeddings:** Sentence Transformers
- **Vector Search:** NumPy cosine similarity
- **Data Analysis:** Pandas, NumPy
- **Forecasting:** Statsmodels
- **Machine Learning:** Scikit-learn
- **Testing:** Pytest
- **Interface:** Gradio

---

## Dataset

The project uses the Northwind SQLite database from:

[Northwind SQLite3 – GitHub](https://github.com/jpwhite3/northwind-SQLite3)

The dataset includes business entities and transactions such as:

- Customers
- Suppliers
- Products and categories
- Employees
- Orders and order lines
- Inventory attributes
- Sales and delivery information

> **Data note:** Northwind is a fictitious sample company. It is a publicly available dataset used for educational, demonstration, and software development purposes—not actual production-company data.

The database is downloaded at runtime. A schema-adaptive semantic layer maps variations in database naming conventions into canonical ERP views.

---

## Getting Started

### 1. Open the Notebook

Open the project notebook in Google Colab.

### 2. Configure API Keys

The notebook supports free-tier API access through Gemini and/or Groq.

Set the API keys in Colab Secrets:

- `GEMINI_API_KEY`
- `GROQ_API_KEY`

At least one provider should be configured for LLM-powered features.

### 3. Run the Notebook

Execute the notebook cells in order, or use:

**Runtime → Run all**

The notebook will:

1. Install required dependencies.
2. Download the Northwind database.
3. Build the semantic layer.
4. Create the retrieval index.
5. Initialize the AI agents and analytical tools.
6. Bootstrap verified SQL examples.
7. Run module smoke tests.
8. Demonstrate the AI Dev Studio.
9. Execute the evaluation workflow.
10. Launch the Gradio interface.

### 4. Explore the ERP

Example queries:

**Business Data**
- Which five customers generated the highest revenue?
- What is the total revenue by product category?
- Which suppliers provide the products with the lowest stock?

**Persian Queries**
- مجموع درآمد هر دسته‌بندی محصول چقدر است؟
- کدام محصولات نیاز به سفارش مجدد دارند؟

**Analytics**
- Forecast revenue for the next three months.
- Identify unusual transactions.
- Segment customers based on their purchasing behavior.

**Procurement**
- Draft purchase orders for critical inventory items.

**AI Development**
- Build a report of customers who have not ordered in the last 60 days, including their lifetime revenue.

---

## Evaluation

The notebook includes an evaluation workflow that generates an `evaluation_report.json` file.

The evaluation protocol covers:

| Metric | Evaluation |
|---|---|
| Text-to-SQL execution accuracy | 10 gold questions |
| English RAG hit@3 | 40 randomly selected product queries |
| Persian RAG hit@3 | Persian retrieval queries |
| Forecasting | Hold-out backtest against a naive baseline |
| AI Dev Studio | Two benchmark feature requests |
| Core regression | Platform-level regression checks |

The notebook is designed to measure these metrics when executed with live API access.

**No live LLM performance results are claimed in advance.** Actual results depend on the models available, API quotas, and execution conditions at the time of running the notebook.

---

## Security and Governance

The prototype incorporates several safeguards:

- SQL execution restricted to permitted analytical queries.
- Read-only database connections for AI analytical tools.
- SQL validation and forbidden-keyword checks.
- Static analysis of AI-generated modules.
- Test execution with timeouts.
- Bounded self-repair iterations.
- Protection against weakening generated test suites during self-repair.
- Human approval required for purchase-order approval.
- Audit logging of procurement-related actions.

These mechanisms are intended for prototyping and demonstration. They do not constitute a production-grade security boundary.

---

## Limitations

- Northwind is a small and relatively clean sample dataset.
- The system is a prototype rather than a production ERP.
- Free-tier API quotas, model availability, and rate limits may change.
- Google Colab sessions are ephemeral unless persistence is configured.
- The prototype does not include full authentication or role-based access control.
- Finance, payroll, and manufacturing modules are outside the current scope.
- AI-generated code requires additional security controls before production deployment.

---

## Project Structure

```text
ai-native-erp/
│
├── AI_Native_ERP_Colab.ipynb
├── AI_Native_ERP_Report.docx
├── README.md
└── LICENSE
```

*Adjust the filenames above to match the files actually uploaded to the repository.*

---

## Future Work

Potential extensions include:

- PostgreSQL support for larger deployments
- FAISS or Chroma for scalable vector retrieval
- Production-grade authentication and role-based access control
- Container-based sandboxing for generated modules
- Additional ERP modules such as finance, payroll, and manufacturing
- User feedback and continuous evaluation
- Local open-weight LLM integration for sensitive data

---

## References

- Lewis, P. et al. (2020). *Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks.*
- Reimers, N., & Gurevych, I. (2019). *Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks.*
- Liu, F. T., Ting, K. M., & Zhou, Z.-H. (2008). *Isolation Forest.*
- Hyndman, R. J., & Athanasopoulos, G. *Forecasting: Principles and Practice.*
- Yao, S. et al. (2023). *ReAct: Synergizing Reasoning and Acting in Language Models.*
- [Northwind SQLite3 Dataset](https://github.com/jpwhite3/northwind-SQLite3)
---

**Project Status:** Prototype / Research & Development

This project demonstrates how an AI-native ERP architecture can combine language models, retrieval, classical analytics, automated software development, and governance mechanisms within a low-cost environment.
