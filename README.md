
# Road Safety Data Pipeline

A Big Data project implementing an Apache Spark-based data pipeline to process and analyze historical traffic accident data using Descriptive Analytics.

## Project Overview

This project implements an end-to-end Big Data pipeline for processing and analyzing historical traffic accident records.

The pipeline consists of data ingestion, data profiling, data cleaning, standardization, validation, storage, aggregation, and visualization using Apache Spark (PySpark).

The project uses a local development environment with Visual Studio Code and Python to demonstrate distributed data processing and generate meaningful insights from traffic accident records.

## Objectives

- Implement a data processing pipeline using Apache Spark.
- Perform data ingestion and exploratory data profiling.
- Identify and handle duplicate records.
- Standardize and validate dataset attributes.
- Compare CSV and Parquet storage formats.
- Analyze traffic accident patterns through data aggregation.
- Present analytical findings through data visualization.

## Analytics Approach

**Descriptive Analytics**

The analysis focuses on identifying historical traffic accident patterns, distributions, and trends through data processing, aggregation, and visualization.

## Technologies

- Python 3.12.4
- Apache Spark (PySpark 4.3.0)
- Java JDK 21.0.2
- Hadoop 3.5.0
- Spark SQL
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Visual Studio Code
- Jupyter Notebook

## Dataset

The project uses a historical traffic accident dataset stored in CSV format.

Dataset characteristics:

- Original records: 209,306 rows
- Original attributes: 24 columns
- Date coverage: 2016–2024
- Missing values: None detected
- Exact duplicate records: 31

The raw dataset is not included in this repository. The cleaned dataset in Parquet format is provided for subsequent processing.

## Project Pipeline

| Stage | Notebook | Description | Status |
|---|---|---|---|
| Data Ingestion | `01_data_ingestion.ipynb` | Load raw dataset and perform initial profiling | Completed |
| Data Cleaning & Storage | `02_data_cleaning_storage.ipynb` | Remove exact duplicates, standardize, validate, and save cleaned data | Completed |
| Data Aggregation | `03_data_aggregation.ipynb` | Aggregate cleaned data to identify accident patterns | In Progress |
| Data Visualization | `04_data_visualization.ipynb` | Visualize and interpret analytical results | In Progress |

## Repository Structure

```text
road-safety-data-pipeline/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   ├── raw/
│   ├── cleaned/
│   │   └── traffic_accidents_clean.parquet/
│   └── aggregated/
├── notebooks/
│   ├── 01_data_ingestion.ipynb
│   ├── 02_data_cleaning_storage.ipynb
│   ├── 03_data_aggregation.ipynb
│   └── 04_data_visualization.ipynb
├── src/
├── outputs/
│   ├── figures/
│   └── reports/
└── docs/
```

## Environment Setup

### Prerequisites

- Python 3.12.4
- Java JDK 21
- Git
- Visual Studio Code

Apache Spark is installed through the PySpark Python package.

### 1. Clone the Repository

```bash
git clone <repository-url>
cd road-safety-data-pipeline
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure Hadoop on Windows

For Windows users, configure Hadoop native binaries if required by the local Spark environment.

The development environment used for this project:

- Hadoop version: 3.5.0
- Hadoop directory: `C:\hadoop`
- Winutils path: `C:\hadoop\bin\winutils.exe`

Set the following environment variables:

```text
HADOOP_HOME=C:\hadoop
```

Add the following directory to the system PATH:

```text
C:\hadoop\bin
```

The Spark session may require the following Java property:

```python
.config(
    "spark.driver.extraJavaOptions",
    "-Dhadoop.home.dir=C:/hadoop"
)
.config(
    "spark.executor.extraJavaOptions",
    "-Dhadoop.home.dir=C:/hadoop"
)
```

Note: Hadoop native configuration is specific to the Windows development environment and may differ on other operating systems.

## Running the Pipeline

Run the notebooks sequentially:

1. `01_data_ingestion.ipynb`
2. `02_data_cleaning_storage.ipynb`
3. `03_data_aggregation.ipynb`
4. `04_data_visualization.ipynb`

### Data Handover for Aggregation

The cleaned dataset is provided in Parquet format at:

```text
data/cleaned/traffic_accidents_clean.parquet/
```

The Parquet directory contains Spark-generated part files and can be read directly using PySpark:

```python
df = spark.read.parquet(
    "data/cleaned/traffic_accidents_clean.parquet"
)
```

The raw CSV and cleaned CSV files are excluded from the repository. Therefore, subsequent processing should use the provided cleaned Parquet dataset.

## Team Responsibilities

**Member 1 — Data Engineering**
- Data ingestion
- Data profiling
- Data cleaning and standardization
- Data validation
- Data storage

**Member 2 — Data Analysis**
- Data aggregation
- Data visualization
- Analytical interpretation

## Team

Analisis Big Data - C  
Universitas Muhammadiyah Malang
