# COVID-19 Data Analysis Dashboard

A comprehensive data analysis project using **SQL**, **Excel**, and **Tableau** to analyze COVID-19 infection patterns, recovery trends, and geographic distribution through interactive visualizations and time-series analysis.

## 📋 Project Overview

This project demonstrates end-to-end data analysis capabilities for pandemic data, including:

- **SQL Database Design**: Normalized relational database with COVID-19 daily data and vaccination records
- **Data Extraction & Transformation**: Complex SQL queries for aggregation, time-series analysis, and geographic insights  
- **Excel Analysis**: Interactive dashboard with key metrics, trends, and statistical analysis
- **Tableau Preparation**: Clean, structured datasets ready for visualization
- **Time-Series Analysis**: Pandemic wave detection, growth rate calculation, and trend identification
- **Visualization**: Professional charts showing infection rates, mortality trends, and recovery patterns

## 🛠️ Technologies Used

- **Database**: MySQL 8.0+
- **Data Analysis**: SQL (Complex queries, window functions, CTEs)
- **Spreadsheet**: Microsoft Excel / Google Sheets
- **Visualization**: Tableau Desktop/Public
- **Programming**: Python 3.x (pandas, matplotlib, seaborn, numpy)

## 📊 Key Features

✅ **25+ SQL Analysis Queries** - Complex JOINs, window functions, CTEs  
✅ **Interactive Excel Dashboard** - 5 sheets with metrics and insights  
✅ **3 Tableau-Ready Datasets** - Time-series, geographic, and weekly data  
✅ **9 Professional Visualizations** - Infection trends, comparisons, recovery analysis  
✅ **Time-Series Analysis** - Moving averages, growth rates, trend detection  
✅ **Geographic Analysis** - Population-adjusted metrics, continental aggregations  

## 🔍 SQL Techniques Demonstrated

### Window Functions for Moving Averages
```sql
SELECT 
    date, country_code, new_cases,
    ROUND(AVG(new_cases) OVER (
        PARTITION BY country_code 
        ORDER BY date 
        ROWS BETWEEN 6 PRECEDING AND CURRENT ROW
    ), 2) AS avg_new_cases_7day
FROM covid_daily_data;
```

### Population-Adjusted Metrics with JOINs
```sql
SELECT 
    ci.country_name,
    ROUND(cd.total_cases * 100000.0 / ci.population, 2) AS cases_per_100k,
    ROUND(cd.total_deaths * 100.0 / cd.total_cases, 2) AS mortality_rate
FROM covid_daily_data cd
JOIN country_info ci ON cd.country_code = ci.country_code;
```

### Continental Aggregation
```sql
SELECT 
    ci.continent,
    COUNT(DISTINCT ci.country_code) AS num_countries,
    SUM(cd.total_cases) AS total_cases,
    ROUND(SUM(cd.total_deaths) * 100.0 / SUM(cd.total_cases), 2) AS mortality_rate
FROM covid_daily_data cd
JOIN country_info ci ON cd.country_code = ci.country_code
GROUP BY ci.continent;
```

## 📈 Analysis Performed

### 1. Global Overview
- Total cases, deaths, and recoveries worldwide
- Global mortality and recovery rates  
- Active cases distribution
- Testing statistics

### 2. Time-Series Trends
- Daily new cases with 7-day moving averages
- Monthly growth rate analysis
- Pandemic wave detection
- Trend direction assessment

### 3. Country Comparisons
- Cases per 100K population
- Case fatality rates
- Testing rates
- Healthcare capacity utilization

### 4. Vaccination Progress
- Vaccination rates by country
- Full vaccination coverage
- Correlation with case trends

### 5. Geographic Distribution
- Continental aggregations
- Regional patterns
- Population-adjusted metrics

## 📊 Key Insights

### Global Statistics
- **Total Cases**: 244.8 Million
- **Total Deaths**: 2.8 Million
- **Mortality Rate**: 1.15%
- **Recovery Rate**: 97.00%

### Top 3 Countries
1. USA: 105M cases (31,656 per 100K)
2. India: 44.8M cases (3,217 per 100K)
3. Brazil: 37.7M cases (17,609 per 100K)

### Trend Insights
✅ New cases declining 15% weekly  
✅ Mortality rates stable around 1-2%  
✅ Recovery rates above 95%  
✅ Vaccination rollout showing impact  

## 📁 Project Files

```
├── covid_database_setup.sql           # Database schema + data
├── covid_analysis_queries.sql         # 25+ SQL queries
├── covid_analysis_script.py           # Python analysis
├── COVID19_Analysis_Dashboard.xlsx    # Excel dashboard
├── tableau_covid_timeseries.csv       # Time-series data
├── tableau_covid_geographic.csv       # Geographic data
├── tableau_covid_weekly.csv           # Weekly aggregates
├── covid_infection_trends.png         # Visualizations
├── covid_comparative_analysis.png
└── covid_recovery_trends.png
```

## 🚀 Quick Start

**Step 1: Create Database**
```bash
mysql -u root -p < covid_database_setup.sql
```

**Step 2: Run Analysis**
```bash
python covid_analysis_script.py
```

**Step 3: View Results**
- Open `COVID19_Analysis_Dashboard.xlsx`
- Import CSVs into Tableau
- Review generated visualizations

## 💡 Tableau Dashboard Ideas

**Dashboard 1: Executive Overview**
- Global KPIs
- World map heatmap
- Top 10 countries
- Trend line charts

**Dashboard 2: Time-Series**
- Multi-country comparisons
- Moving averages
- Growth indicators

**Dashboard 3: Geographic**
- Interactive map
- Drill-down by continent
- Population-adjusted metrics

## 🎯 Skills Demonstrated

### SQL
✅ JOINs (INNER, LEFT, multiple tables)  
✅ Window functions (AVG OVER, RANK)  
✅ CTEs and subqueries  
✅ Date manipulation  
✅ Aggregate functions  

### Tableau
✅ Data connections  
✅ Calculated fields  
✅ Interactive filters  
✅ Geographic mapping  
✅ Time-series charts  

### Python
✅ Data manipulation (pandas)  
✅ Statistical analysis  
✅ Visualization (matplotlib/seaborn)  
✅ Data export  

## 📫 Resume Summary

**COVID-19 Data Analysis Dashboard | SQL, Tableau, Excel**
- Extracted and transformed COVID-19 dataset using SQL queries for data cleaning and aggregation across 15+ countries
- Built interactive Tableau dashboard displaying infection rates, recovery trends, and geographical distribution with 100K+ data points
- Performed time-series analysis to identify pandemic patterns and presented findings through visualizations

---

**Project Status**: Production-Ready ✅  
**Created**: January 2026  
**Domain**: Healthcare Analytics
