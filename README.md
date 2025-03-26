# Medallion ETL Project

## Overview
This project implements an ETL pipeline using the **Medallion Architecture** (Bronze, Silver, and Gold layers) to process and analyze an online retail dataset. The pipeline includes data ingestion, cleaning, transformation, and warehousing for efficient reporting and analytics.

## Project Structure
```
retail-sales/
|── src
  │── 01 - Data Ingest.ipynb                              # Code to ingest raw data and store it in Bronze layer
  │── 02 - Clean Data.ipynb                               # Cleans the dataset and stores it in Silver layer; Also contains Data Quality Monitoring and Alerts scripts
  │── 03 - Data Transformation and Aggregation.ipynb/     # Transforms and aggregates the dataset and stores it in Gold layer
  │── 04 - Create Data Warehouse.ipynb                    # Dimensional model
  │── 05 - Metadata Management.ipynb                      # Metadata repository
│── README.md
```

## ETL Pipeline
The ETL pipeline follows these stages:

### 01 - Data Ingest
- Reads data from a CSV file (`data/raw/online_retail.csv`).
- Stores it in the databricks unity catalog's **Bronze Layer** (`online_retail.bronze.raw_data`).

### 02 - Clean Data
- Removes duplicates and handles missing values.
- Saves cleaned data to the **Silver Layer** (`online_retail.silver.cleaned_data`).
- Also contains Data Quality Monitoring and Alerts scripts.

### 03 - Data Transformation and Aggregation
- Converts data types, standardizes formats, and calculates new columns.
- Saves processed data to the **Gold Layer** (`online_retail.gold.aggregated_data`).

### 04 - Create Data Warehouse
- Creates structured tables:
  - `dim_product` (dim_product_id, product_code, product_description, unit_price)
  - `dim_customer` (dim_customer_id, customer_id, country)
  - `fct_sale` (fct_sale_id, invoice_number, invoice_date, dim_product_id, dim_customer_id, quantity)
- Establishes relationships between tables for analytical queries.

![](/Volumes/online_retail/bronze/raw/online_retail_erd.JPG)
draw.io link - [](/Volumes/online_retail/bronze/raw/online_retail_erd.drawio)

### 5. Metadata Management
- Maintains `metadata.json` with row counts for each processing stage.

## Author
Sree Spoorthy G