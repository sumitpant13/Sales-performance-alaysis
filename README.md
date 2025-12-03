# Superstore Sales Analysis — Revenue Insights & Outlier Treatment

## Project Overview
This project analyzes a retail Superstore dataset containing around 9,800 sales transaction records across multiple product categories, regions, and customer segments. The objective is to clean the data, detect and treat outliers in the Sales variable, understand sales distribution, and generate business insights using visual and statistical analysis.

## Dataset Summary
The dataset contains 9,800 rows and 18 columns. It includes order-level details such as order dates, shipping dates, customer information, product hierarchy, geographic information, and sales revenue.

### Main Features
- Row_ID: Unique row identifier  
- Order_ID: Unique order identifier  
- Order_Date: Date of order placement  
- Ship_Date: Date the order was shipped  
- Ship_Mode: Shipping method used  
- Customer_ID, Customer_Name: Customer identifiers  
- Segment: Customer segment (Consumer, Corporate, Home Office)  
- Country, City, State, Region: Geographic attributes  
- Postal_Code: Customer postal code  
- Product_ID, Category, Sub_Category, Product_Name: Product information  
- Sales: Revenue generated from the transaction  

## Data Cleaning & Preparation
- Converted `Order_Date` and `Ship_Date` to datetime format.  
- Verified that there were no zero or negative Sales values.  
- Identified 11 missing values in `Postal_Code` (0.11% of data) and dropped those rows.  
- Confirmed there were no duplicate records in the dataset.  
- Created additional fields:
  - `Sales_Capped`: Sales column after outlier treatment.
  - `Month`: Monthly period extracted from Order_Date for trend analysis.

## Outlier Detection & Treatment
- Applied the Interquartile Range (IQR) method on the `Sales` variable:
  - Q1 = 25th percentile of Sales  
  - Q3 = 75th percentile of Sales  
  - IQR = Q3 - Q1  
  - Lower bound = Q1 - 1.5 × IQR  
  - Upper bound = Q3 + 1.5 × IQR  
- Identified 1,141 outliers in Sales.  
- Treated outliers using capping:
  - Values below lower bound set to lower bound.  
  - Values above upper bound set to upper bound.  
- Compared original vs capped Sales distributions using histograms, boxplots, and KDE plots.

## Exploratory Data Analysis (EDA)

### Univariate Analysis
- Distribution of Sales (before and after capping).  
- Frequency of Product Categories and Sub-Categories.  
- Count of orders by Segment and Ship Mode.  
- Region-wise record distribution.

### Bivariate & Multivariate Analysis
- Top 10 Products by total Sales.  
- Sales by Segment using aggregated bar plots.  
- Sales by Region vs Category using a pivot table and heatmap.  
- Monthly Sales trend using a time-series line plot (Sales aggregated by Month).  
- Top 10 Cities by Sales.  
- Sales by Ship Mode (Standard Class, Second Class, First Class, Same Day).

## Key Insights
- Office Supplies is the most frequently sold category, while Furniture and Technology often generate higher revenue per order.  
- The Consumer segment contributes the highest share of sales among all segments.  
- California and New York are among the top revenue-generating states, with cities like New York City contributing significantly.  
- Standard Class is the most commonly used shipping mode, indicating cost-efficient delivery preference.  
- There are a few products and SKUs that repeatedly appear in top-selling lists, indicating strong-performing items worth prioritizing in inventory and marketing.  
- After outlier capping, the Sales distribution becomes less skewed and more suitable for modeling and further statistical analysis.

## Tools & Libraries
- Python  
- Pandas  
- NumPy  
- Matplotlib  
- Seaborn  
- SciPy  
- Jupyter Notebook  

## Repository Structure
- `superstore_final_dataset.csv` — cleaned Superstore dataset used in analysis  
- `superstore_analysis.ipynb` — Jupyter Notebook containing data cleaning, EDA, and visualizations  
- `README.md` — Project documentation and summary

## Author
**Name:** Sumit Pant  
**Email:** sumitpant2004@gmail.com  
**GitHub:** https://github.com/sumitpant13  
**LinkedIn:** https://linkedin.com/in/sumitpant13
