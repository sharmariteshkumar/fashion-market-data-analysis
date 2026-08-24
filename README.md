# Week 2 – Data Cleaning and Pre-Processing Pipeline

## 📌 Project Overview

This project focuses on cleaning and preprocessing an apparel market dataset collected during Phase 1 of the internship project.

The raw dataset contained qualitative product listings, unstructured price values, duplicate records, missing values, inconsistent whitespace, and variations in brand naming.

The dataset covers five global apparel enterprises:

* Nike
* Adidas
* Zara
* H&M
* UNIQLO

The objective of Week 2 is to transform the raw market dataset into a clean, structured, analysis-ready dataset using Python, Pandas, and NumPy.

---

## 🎯 Objectives

The main objectives of this phase are:

1. **Deduplication** – Identify and remove duplicate product records.
2. **Text Standardization** – Clean whitespace and standardize brand names.
3. **Price Extraction** – Convert text-based INR prices into numerical values.
4. **Missing Value Imputation** – Handle missing prices using brand-level median values.
5. **Data Export** – Generate cleaned datasets and summary files for further analysis.
6. **Reproducibility** – Maintain a clear transformation and audit trail.

---

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Regular Expressions (`re`)
* CSV

---

## 🔄 Data Pre-Processing Pipeline

```text
Raw Data: 52 Rows
        ↓
Whitespace & String Cleaning
        ↓
Deduplication
        ↓
50 Unique Records
        ↓
Regex Price Parsing
        ↓
Missing Value Detection
        ↓
Brand-wise Median Imputation
        ↓
Cleaned Dataset
        ↓
Statistical Summary
        ↓
CSV Export
```

The pipeline reduced the original **52 observations to 50 unique records** after duplicate removal.

---

## 🧹 Data Cleaning Steps

### 1. Ingestion and Text Normalization

Whitespace and formatting inconsistencies were removed from text fields including:

* `Brand`
* `Category`
* `Product_Name`
* `Target_Demographic`

The `.str.strip()` method was applied to remove unnecessary leading and trailing spaces.

Brand names were also standardized, for example:

```text
H & M → H&M
Nike  → Nike
Zara  → Zara
```

This ensures consistent grouping and analysis across the dataset.

---

### 2. Duplicate Removal

Duplicate records were identified using Pandas:

```python
df.duplicated()
```

Duplicate rows were removed using:

```python
df.drop_duplicates()
```

Two redundant records were identified and removed.

```text
Before: 52 records
After:  50 records
```

---

### 3. Price Extraction

The raw price column contained values such as:

```text
₹ 1,295
```

A regular expression was used to remove currency symbols, commas, and other non-numeric characters.

Example:

```python
re.findall(r'\d+', price)
```

The extracted values were converted into numerical `float64` values.

Example:

```text
₹ 1,295 → 1295.0
```

---

### 4. Missing Value Imputation

Two records contained missing price values (`N/A`).

Instead of deleting those records, missing prices were filled using the **median price of the corresponding brand**.

This preserves the dataset size while reducing the potential influence of extreme prices.

---

## 📊 Dataset Transformation

| Feature       | Raw State              | Processed State           | Technique           |
| ------------- | ---------------------- | ------------------------- | ------------------- |
| Row Count     | 52 records             | 50 unique records         | `drop_duplicates()` |
| Brand         | Inconsistent names     | Standardized names        | String replacement  |
| Price         | Text such as `₹ 1,295` | `1295.0`                  | Regex extraction    |
| Missing Price | `N/A`                  | Numerical value           | Brand-wise median   |
| Data Types    | Unstructured strings   | Float / category / string | Explicit casting    |

These transformations were verified as passed in the Week 2 transformation audit.

---

## 📁 Output Files

The preprocessing workflow generates the following files:

```text
raw_data.csv
cleaned_data.csv
brand_summary.csv
```

### `raw_data.csv`

Contains the original dataset before preprocessing.

### `cleaned_data.csv`

Contains the cleaned and standardized 50-record dataset.

### `brand_summary.csv`

Contains aggregated statistical information for each apparel brand.

The report specifies these files as part of the reproducible audit trail and repository version control.

---

## 📈 Brand-Level Statistical Summary

| Brand  | Product Count | Min Price (INR) | Max Price (INR) | Mean Price (INR) | Median Price (INR) | Positioning                               |
| ------ | ------------: | --------------: | --------------: | ---------------: | -----------------: | ----------------------------------------- |
| H&M    |            10 |            ₹610 |          ₹2,470 |           ₹1,560 |             ₹1,875 | Accessible Mass-Market Fashion            |
| UNIQLO |            10 |          ₹1,020 |          ₹4,850 |           ₹3,076 |             ₹3,820 | Functional Everyday Wear / LifeWear       |
| Zara   |            10 |          ₹3,320 |          ₹8,380 |           ₹5,980 |             ₹5,970 | Trendy Contemporary Fast Fashion          |
| Adidas |            10 |          ₹1,410 |          ₹9,310 |           ₹6,031 |             ₹6,625 | Athletic Performance & Cultural Lifestyle |
| Nike   |            10 |          ₹1,560 |         ₹10,550 |           ₹7,038 |             ₹7,760 | Premium Sportswear & Brand Equity         |

The report states that these statistics were computed directly from `cleaned_data.csv`.

---

## ✅ Results

The Week 2 preprocessing workflow successfully:

* Reduced **52 raw records to 50 unique records**
* Removed duplicate observations
* Standardized text fields
* Standardized brand identifiers
* Converted unstructured INR prices into numerical values
* Imputed missing prices using brand-level medians
* Created a structured, analysis-ready dataset
* Generated statistical summaries for the five brands

---

## 🔍 Key Findings

Based on the cleaned dataset:

* **H&M** has the lowest mean price among the five brands.
* **Nike** has the highest mean and maximum price.
* **Zara** occupies a contemporary fast-fashion positioning.
* **UNIQLO** represents functional everyday wear.
* **Adidas** combines athletic performance with lifestyle positioning.
* Each brand contains **10 products** in the cleaned summary.

These results provide a foundation for future descriptive analysis, visualization, and comparative market-positioning work.

---

## 🚀 Next Phase

The cleaned dataset can be used for:

* Descriptive statistical analysis
* Price-distribution visualization
* Brand comparison
* Trend analysis
* Market-positioning analysis
* Comparative dashboards

The Week 2 report identifies the cleaned dataset as the foundation for trend visualization, descriptive statistical modeling, and comparative market positioning in subsequent project phases.

---

## 👤 Author

**Sharma Riteshkumar**

**Program:** Junior Data Analyst – Apparel, Textiles & Fashion
**Target Industry:** International Retail & Fast Fashion E-Commerce
**Week:** 2
**Submission Date:** August 24, 2026
