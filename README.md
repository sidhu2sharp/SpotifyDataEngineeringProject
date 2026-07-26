# SpotifyDataEngineeringProject

## Overview

Designed and implemented a scalable, metadata-driven ETL pipeline on Microsoft Azure to ingest Spotify data into a Medallion Architecture using Azure Data Factory, Azure Databricks, Delta Live Tables, and Delta Lake. The project automates incremental data ingestion, data transformation, and gold-layer dimensional modeling while ensuring data quality and pipeline reliability.

## Architecture

Spotify API
      │
      ▼
Azure Data Lake Storage (Bronze)
      │
      ▼
Azure Data Factory
(Incremental CDC Pipeline)
      │
      ▼
Azure Databricks
(Silver Transformations)
      │
      ▼
Delta Live Tables
(Gold Layer)
      │
      ▼
Analytics Ready Star Schema

## Key Features

- End-to-end Azure Data Engineering pipeline
- Metadata-driven incremental data ingestion
- Change Data Capture (CDC) using watermark tracking
- Azure Data Factory orchestration with ForEach loops and conditional execution
- PySpark-based data transformations
- Delta Live Tables (DLT) pipeline for Gold layer
- Star schema dimensional modeling
- Automated pipeline execution and monitoring
- Built-in data quality expectations using Delta Live Tables

## Tech Stack

- PySpark
- SQL
- Azure Data Factory
- Azure Data Lake Storage Gen2
- Azure Databricks
- Delta Lake
- Delta Live Tables (DLT)
- Git & GitHub

## Pipeline Workflow
### 1. Bronze Layer (Incremental Ingestion)

Azure Data Factory retrieves the last processed CDC value for each source table and performs incremental ingestion instead of full refreshes.

The pipeline uses:

Lookup Activity
Set Variable
Copy Data
ForEach Activity
If Condition
SQL Script Activity

to dynamically process multiple datasets.

### 2. Silver Layer

Raw Spotify data is cleaned, standardized, and transformed using PySpark notebooks before being stored as Delta tables.

### 3. Gold Layer

Delta Live Tables builds analytics-ready Gold tables from the Silver layer.

The Gold layer includes:

dimUser
dimDate
dimTrack
FactStream

Each dimension passes through staging tables before final publication, enabling modular transformations and improved maintainability.

## Data Quality

Implemented Delta Live Table Expectations to validate incoming data and improve pipeline reliability before publishing Gold tables.

## Highlights

- Automated incremental ETL pipeline using Azure Data Factory
- Metadata-driven orchestration supporting multiple tables
- Built scalable PySpark transformation logic in Azure Databricks
- Implemented Delta Live Tables for managed streaming ETL
- Created dimensional model for downstream analytics
- Reduced unnecessary data movement through CDC-based incremental loading
- Designed reusable, production-inspired Azure data engineering workflows

  
