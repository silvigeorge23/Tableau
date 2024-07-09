# Tableau
Aim: Dashboard to help executives analyse sales performance. Present an overview of Sales metrics and trends in performance and understand the Sales Trends
KPI Dashboard: Summary of Total Sales, Profits & Quantity for current year and previous year
Sales Trends: Present Data for each KPI on a monthly basis for both current and previous year. Identify months with highest and lowest sales
Product Subcategory Comparison: compare sales performance by different product subcategories for current and previous year, and comparison of Sales with profit
Weekly Trends for Sales & Profit: Weekly sales and profit data for current year. Display average weekly values. Highlight weeks that are above and below average to draw attention to sales and profit performance

#Calculations
Current Year: [Select year]
Previous Year: [Select year]-1


#SALES
Current Year Sales:
IF YEAR ([Order Date]) = [Select year] THEN [Sales]
END

Previous Year Sales:
IF YEAR ([Order Date]) = [Select year]-1 THEN [Sales]
END

% Diff Sales:
(SUM ([CY Sales]) - SUM([PY Sales]))/SUM([PY Sales])

Min/Max Sales:
IF SUM([CY Sales]) = WINDOW_MAX(SUM([CY Sales]))
THEN SUM([CY Sales])
ELSEIF SUM ([CY Sales]) = WINDOW_MIN(SUM([CY Sales]))
THEN SUM([CY Sales])
END

#PROFIT
Current Year Profit:
IF YEAR([Order Date]) = [Select year] THEN [Profit]
END

Previous Year Profit:
IF YEAR([Order Date]) = [Select year]-1 THEN [Profit]
END

% Diff Profit:
(SUM ([CY Profit]) - SUM ([PY Profit]))/SUM ([PY Profit])

Min/Max Profit:
IF SUM([CY Profit]) = WINDOW_MAX(SUM([CY Profit]))
THEN SUM ([CY Profit])
ELSEIF SUM ([CY Profit]) = WINDOW_MIN(SUM([CY Profit]))
THEN SUM ([CY Profit])
END

#QUANTITY

Current Year Quantity:
IF YEAR ([Order Date]) = [Select year] THEN [Quantity]
END

Previous Year Quantity:
IF YEAR ([Order Date]) = [Select year]-1 THEN [Quantity]
END

% Diff Quantity:
(SUM ([CY Quantity]) - SUM([PY Quantity]))/SUM([PY Quantity])

Min/Max Quantity:
IF SUM([CY Quantity]) = WINDOW_MAX(SUM([CY Quantity]))
THEN SUM([CY Quantity])
ELSEIF SUM ([CY Quantity]) = WINDOW_MIN(SUM([CY Quantity]))
THEN SUM([CY Quantity])
END

KPI CY Less PY:
IF SUM([CY Sales]) < SUM([PY Sales]) THEN '⬤'
ELSE ''
END

KPI Profit Avg:
IF SUM([CY Profit]) > WINDOW_AVG(SUM([CY Profit]))
THEN 'above'
ELSE 'below'
END

KPI Sales Avg:
IF SUM([CY Sales]) > WINDOW_AVG(SUM([CY Sales]))
THEN 'above'
ELSE 'below'
END
