# Fraud Detection & Risk Analytics – Financial Transactions
Analyzing fraud patterns and building a risk scoring system to support real-time fraud prevention using SQL & Databricks.

## 📌 Table of Contents
- <a href="#overview">Overview</a>
- <a href="#business-problem">Business Problem</a>
- <a href="#dataset">Dataset</a>
- <a href="#tools--technologies">Tools & Technologies</a>
- <a href="#project-structure">Project Structure</a>
- <a href="#data-cleaning--preparation">Data Cleaning & Preparation</a>
- <a href="#exploratory-data-analysis-eda">Exploratory Data Analysis (EDA)</a>
- <a href="#research-questions--key-findings">Research Questions & Key Findings</a>
- <a href="#dashboard">Dashboard</a>
- <a href="#final-recommendations">Final Recommendations</a>
- <a href="#author--contact">Author & Contact</a>

---

<h2><a class="anchor" id="overview"></a>Overview</h2>
Financial institutions process millions of digital transactions every day. Detecting fraudulent transactions within this large volume of activity is a critical challenge for banks and payment platforms.
This project demonstrates how SQL-based analytics can be used to identify suspicious transaction patterns and evaluate fraud risk using SQL in Databricks. The analysis focuses on identifying behavioural anomalies, statistical irregularities, and high‑risk transaction characteristics.
By combining transaction pattern analysis, customer behaviour analysis, and anomaly detection techniques such as Benford’s Law, this project develops a rule‑based fraud risk scoring approach that highlights transactions requiring further investigation.

---

<h2><a class="anchor" id="business-problem"></a>Business Problem</h2>
Financial institutions process millions of transactions daily. Fraud is rare but high-impact. This project aims to:

- Identify when fraud happens most (time-based patterns)
- Determine which transaction types are riskiest
- Build a risk scoring model to flag suspicious transactions
- Analyze recipient accounts for fraud exposure
- Statistically validate fraud indicators like Benford's Law

---

<h2><a class="anchor" id="dataset"></a>Dataset</h2>

- Source: PaySim synthetic financial transactions dataset (Kaggle)
- Size: 6.3 million transactions
- Key fields: transaction_type, amount, time_period, isFraud, customer_id, recipient_id, oldbalance, newbalance

---

<h2><a class="anchor" id="tools--technologies"></a>Tools & Technologies</h2>

- Databricks - Interactive Visualizations & (SQL for ETL and feature engineering)
- SQL (Common Table Expressions, Window Functions, Aggregations)
- GitHub

---

<h2><a class="anchor" id="project-structure"></a>Project Structure</h2>

```
fraud-detection-project/
│
├── README.md
├── .gitignore
├── Fraud_Project (1).py # Databricks notebook with all SQL code
├── fraud_risk_analytics_databricks_project_updated.docx
│
├── dashboard/ # Power BI dashboard file
│ └── fraud_dashboard.pbix
│
├── screenshots/ # Visual outputs
│ ├── fraud_by_time.png
│ ├── fraud_by_risk.png
│ ├── risk_score_scatter.png
│ └── fraud_vs_normal.png
```



---

<h2><a class="anchor" id="data-cleaning--preparation"></a>Data Cleaning & Preparation</h2>

- Removed invalid transactions (amount ≤ 0) 
- Standardized column names for readability 
- Created transaction size categories (Small, Medium, Large, Very Large) 
- Added time-based dimensions: 
  - hour_of_day 
  - day_number 
  - day_of_week 
  - time_period (Morning, Afternoon, Evening, Late Night) 
- Identified recipient type (Merchant vs Customer) 
---

<h2><a class="anchor" id="exploratory-data-analysis-eda"></a>Exploratory Data Analysis (EDA)</h2>

**Class Imbalance:**
- **99.87%** Normal Transactions
- **0.13%** Fraudulent Transactions
- Reflects real-world financial systems

**Fraud by Transaction Type:**
- **CASH_OUT** and **TRANSFER** account for nearly all fraud
- **PAYMENT**, **DEBIT**, and **CASH_IN** show zero fraud

**Time-Based Patterns:**
- Afternoon (12-17): ~6,000 fraud cases (peak)
- Evening (18-23): ~5,500 fraud cases
- Morning & Late Night: Under 2,000 cases

**Benford's Law Analysis:**
- Fraud rates higher for amounts starting with digits 7, 8, 9
- Confirms statistical anomaly detection works

---

<h2><a class="anchor" id="research-questions--key-findings"></a>Research Questions & Key Findings</h2>

**When does fraud happen most?**
- Afternoon and evening hours see the highest fraud activity
- Late night and early morning are quieter

**Which transaction types are riskiest?**
- **CASH_OUT** and **TRANSFER** = High risk
- Other types = Low/No risk

**Can we score risk effectively?**
- **Critical-risk recipients** (5+ fraud transactions received) = **1,407 fraud cases**
- **Medium-risk recipients** = **943 fraud cases**
- Fraud clusters at **risk scores 8+** , regardless of amount

**Why does "high-risk" show zero fraud?**
- Possible model tuning issue—needs investigation
- May indicate misclassified risk thresholds

**Does Benford's Law detect fraud?**
- Yes—fraud rates are higher for unusual first digits (7,8,9)

---

<h2><a class="anchor" id="dashboard"></a>Dashboard</h2>
Visualizations created directly in Databricks using SQL and display functions:

- **Fraud vs Normal Transactions** (99.87% / 0.13%)
- **Fraud by Transaction Type** – Bar chart showing CASH_OUT and TRANSFER as highest risk
- **Fraud by Time Period** – Bar chart showing afternoon/evening peaks
- **Fraud by Risk Level** – Bar chart confirming critical-risk recipients drive most fraud
- **Risk Score vs Amount** – Scatter plot showing fraud clusters at higher risk scores

*All screenshots available in /screenshots folder*

---

<h2><a class="anchor" id="final-recommendations"></a>Final Recommendations</h2>

1. **Focus fraud prevention** on afternoon and evening hours
2. **Prioritize monitoring** of CASH_OUT and TRANSFER transactions
3. **Flag critical-risk recipients** immediately for review
4. **Investigate** why high-risk transactions show zero fraud—tune the model
5. **Use risk score** as primary fraud indicator (stronger than amount)
6. **Review medium-risk recipients**—they still account for significant fraud
7. **Apply Benford's Law** as an ongoing monitoring tool

---

<h2><a class="anchor" id="author--contact"></a>Author & Contact</h2>

**Vipin Kumar Rahate**  
Data Analytics Project – Fraud Risk Analysis using SQL in Databricks  
Linkdin - https://www.linkedin.com/in/vipin-rahate/
