# Employee Data ETL Pipeline

A PySpark-based ETL pipeline built on Databricks to ingest, clean, validate, and analyze HR employee data.

## Overview
This project processes a dataset of 3,400+ employee records (20 attributes including department, income, tenure, performance, and attrition) through a full ETL workflow, surfacing real workforce insights via SQL.

## Pipeline Steps
1. **Ingest** – Load raw CSV data into a Spark DataFrame
2. **Explore** – Profile the dataset to detect nulls, duplicates, and invalid values
3. **Clean** – Resolve 272 null values across 4 columns, remove 15 duplicate records, fix 4 negative income values and 4 invalid age entries, standardize inconsistent text formatting
4. **Validate** – Automated assertions confirm zero nulls in key fields, zero duplicate IDs, and zero invalid values before saving
5. **Transform** – Derive new features: Income Band (Low/Mid/High) and Attrition Risk Flag
6. **Store** – Write cleaned data (3,400 records) to Delta Lake
7. **Analyze** – Run SQL queries to surface workforce trends

## Key Findings
| Insight | Result |
|---|---|
| Highest avg. income department | HR (₹5,181/month) |
| Lowest avg. income department | Marketing (₹5,038/month) |
| Highest attrition rate | Finance & Sales (51.2%) |
| Lowest attrition rate | Marketing (50.1%) |
| Job satisfaction by income band | Fairly flat (2.99–3.11), suggesting income alone isn't a strong driver of satisfaction |

## Tech Stack
- **Databricks** (compute + workspace)
- **PySpark** (data processing)
- **Delta Lake** (storage)
- **SQL** (analytics)

## Files
- `employee_etl_pipeline.py` (or `.ipynb`) – the full notebook
- `HR_Dataset_dirty.csv` – sample dataset with intentionally injected data quality issues (nulls, duplicates, invalid values) used to simulate real-world messy data

## How to Run
1. Upload the dataset to a Databricks Volume or DBFS
2. Open the notebook in a Databricks workspace and attach it to a cluster
3. Run cells sequentially — the notebook ingests, cleans, validates, stores, and analyzes the data end-to-end
