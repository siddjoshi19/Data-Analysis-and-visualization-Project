# Data-Analysis-and-visualization-Project
## International Debt Analysis

<p> This Data Analysis focuses on the datasets that are followed. Here Datasets contain the information about the international debts that each contry has to the different countries. So we are going to analyze the data and find out some basic information from the data. The question set contain the begginer and intermidiate level questions.</p>

### Data sources
Kaggle: https://www.kaggle.com/datasets/siddjoshisidd/international-debt

### Tools
  <li>MySQL - Workbench 8.0</li>
  <li>Excel</li>

### Exploratory Data Analysis

EDA invloved exploring the debt data to answer key questions, such as:
  <li>The World Bank's international debt data</li>
  <li>Finding the number of distinct countries</li>
  <li>Finding out the distinct debt indicators</li>
  <li>Totaling the amount of debt owed by the countries</li>
  <li>Country with the highest debt</li>
  <li>Average amount of debt across indicators</li>
  <li>The most common debt indicator</li>
  <li>Other viable debt issues and conclusion</li>

# SQL Qurey

1. The World Bank's international debt data
```SQL
SELECT * FROM international_debt
LIMIT 10;
```

2. Finding the number of distinct countries
```SQL
SELECT COUNT(DISTINCT(country_name)) AS total_distinct_countries
FROM international_debt;
```
3. Finding out the distinct debt indicators
```SQL
SELECT DISTINCT(indicator_code) AS distinct_debt_indicators
FROM international_debt
ORDER BY 1;
```
4. Totaling the amount of debt owed by the countries
```SQL
SELECT 
ROUND(SUM(debt)/1000000, 2) AS total_debt
FROM international_debt;
```

5. Country with the highest debt
```SQL
SELECT 
country_name , SUM(debt) AS total_debt
FROM international_debt
GROUP BY country_name
ORDER BY total_debt DESC
LIMIT 1;
```
6. Average amount of debt across indicators
```SQL
SELECT 
    indicator_code  AS debt_indicator,
    indicator_name ,
    AVG(debt) AS average_debt
FROM international_debt
GROUP BY debt_indicator, indicator_name
ORDER BY average_debt DESC
LIMIT 10;
```

7. The highest amount of principal repayments
```SQL
SELECT 
    country_name, 
    indicator_name
FROM international_debt
WHERE debt = (SELECT 
                 MAX(debt)
             FROM international_debt
             WHERE indicator_code LIKE 'DT.AMT.DLXF.CD');
```
8. The most common debt indicator---
```SQL
SELECT indicator_code, COUNT(indicator_code) AS indicator_count
FROM international_debt
GROUP BY indicator_code
ORDER BY indicator_count DESC, indicator_code DESC
LIMIT 20;
```
9. Other viable debt issues and conclusion
```SQL
SELECT country_name, indicator_name, MAX(debt) AS maximum_deb
FROM international_debt
GROUP BY country_name, indicator_nam
```

