# 🛒 Customer Purchasing Behavior & Product Performance Analysis

## 📌 Project Overview

This project analyzes customer purchasing behavior and product performance using **SQL and the Instacart-style grocery shopping dataset**.

The objective is to identify purchasing patterns, reorder behavior, popular products, customer activity, department performance, and order trends. The analysis provides actionable insights that can help an e-commerce grocery business improve **product recommendations, inventory planning, customer retention, and marketing strategies**.

---

## 🎯 Objectives

The main objectives of this project are:

* Analyze customer purchasing behavior
* Identify the most popular and frequently reordered products
* Analyze product distribution across departments and aisles
* Understand customer ordering patterns
* Identify peak ordering hours and weekdays
* Calculate average order size
* Analyze product reorder rates
* Identify highly engaged customers
* Compare product and department performance
* Generate business recommendations from the analysis

---

## 🗂️ Dataset

The project uses an Instacart-style grocery shopping dataset consisting of the following tables:

### 1. Aisles

Contains information about grocery product aisles.

| Column     | Description             |
| ---------- | ----------------------- |
| `aisle_id` | Unique aisle identifier |
| `aisle`    | Aisle name              |

### 2. Departments

Contains grocery department information.

| Column          | Description                  |
| --------------- | ---------------------------- |
| `department_id` | Unique department identifier |
| `department`    | Department name              |

### 3. Products

Contains product-level information.

| Column          | Description               |
| --------------- | ------------------------- |
| `product_id`    | Unique product identifier |
| `product_name`  | Product name              |
| `aisle_id`      | Aisle identifier          |
| `department_id` | Department identifier     |

### 4. Orders

Contains customer order information.

| Column                   | Description               |
| ------------------------ | ------------------------- |
| `order_id`               | Unique order identifier   |
| `user_id`                | Customer identifier       |
| `eval_set`               | Dataset category          |
| `order_number`           | Customer's order sequence |
| `order_dow`              | Day of week               |
| `order_hour_of_day`      | Hour of order             |
| `days_since_prior_order` | Days since previous order |

### 5. Order Products

Contains products purchased in each order.

| Column              | Description                                 |
| ------------------- | ------------------------------------------- |
| `order_id`          | Order identifier                            |
| `product_id`        | Product identifier                          |
| `add_to_cart_order` | Position added to cart                      |
| `reordered`         | Indicates whether the product was reordered |

---

## 🛠️ Technologies Used

* **MySQL**
* **MySQL Workbench**
* **SQL**
* **Git & GitHub**

### SQL Concepts Used

* `SELECT`
* `WHERE`
* `GROUP BY`
* `HAVING`
* `ORDER BY`
* `LIMIT`
* `COUNT()`
* `SUM()`
* `AVG()`
* `ROUND()`
* `JOIN`
* `INNER JOIN`
* Subqueries
* Aggregate Functions
* Conditional Analysis

---

## 🔍 Key Analysis Performed

The project includes **20 SQL business analysis tasks**.

### Product & Department Analysis

1. Top 10 aisles with the highest number of products
2. Number of unique departments
3. Product distribution across departments
4. Top 10 products by reorder rate
5. Number of unique customers
6. Average days between orders per customer
7. Peak ordering hours
8. Order volume by weekday
9. Top 10 most ordered products
10. Number of users ordering from each department

### Customer & Order Analysis

11. Average number of products per order
12. Most reordered product in each department
13. Products reordered more than once
14. Average number of products added to cart per order
15. Number of orders by hour
16. Distribution of orders based on order size
17. Average reorder rate by aisle
18. Average order size by weekday
19. Top 10 users by number of orders
20. Number of products available in each aisle and department

---

## 📊 Business Questions

This analysis answers important business questions such as:

* Which products are ordered most frequently?
* Which products have the highest reorder rates?
* Which departments have the largest product variety?
* When are customers most likely to place orders?
* Which weekdays generate the highest order volume?
* Which customers are the most active?
* Which products are frequently purchased again?
* Which aisles have the highest customer retention through reorders?
* What is the average basket size?
* Which departments should receive stronger marketing attention?

---

## 💡 Key Business Insights

The SQL analysis can be used to identify:

### 🛍️ Product Performance

Frequently ordered and highly reordered products can be classified as **high-performing products**.

These products can be prioritized for:

* Product recommendations
* Promotions
* Cross-selling
* Inventory planning
* Personalized offers

### 🔄 Customer Reordering

Products with high reorder rates indicate strong customer loyalty and recurring demand.

Businesses can use this information for:

* Reorder reminders
* Subscription-style purchasing
* Personalized recommendations
* Loyalty programs

### ⏰ Ordering Patterns

Analyzing order hour and weekday helps identify periods of high customer activity.

This can support:

* Targeted marketing campaigns
* Staffing decisions
* Delivery capacity planning
* Promotional timing

### 👥 Customer Behavior

Identifying customers with a high number of orders helps businesses recognize highly engaged customers.

These customers can be targeted with:

* Loyalty rewards
* Personalized discounts
* Premium membership programs
* Early access to promotions

---

## 📈 Marketing Recommendations

Based on the analysis, the following strategies can be implemented:

### 1. Personalized Product Recommendations

Recommend frequently purchased and reordered products to customers based on their previous purchases.

### 2. Reorder Reminders

Send notifications when customers are likely to need products they regularly reorder.

### 3. Cross-Selling

Recommend complementary products together.

For example:

> Customers purchasing a particular product can be shown related products from the same department.

### 4. Customer Loyalty Programs

Reward customers with high order frequency using:

* Discount coupons
* Loyalty points
* Free delivery
* Personalized offers

### 5. Peak-Time Promotions

Launch promotions during high-volume ordering hours to maximize conversions.

### 6. Inventory Optimization

Frequently ordered products should receive higher inventory priority to reduce stockouts.

### 7. Department-Level Marketing

Departments with high order volumes and reorder rates can receive greater promotional investment.

---

## 🚀 How to Run the Project

### Step 1: Install MySQL

Install MySQL and MySQL Workbench.

### Step 2: Create the Database

```sql
CREATE DATABASE project_orders;
```

### Step 3: Select the Database

```sql
USE project_orders;
```

### Step 4: Import the Dataset

Import the CSV files into MySQL Workbench and create the required tables.

### Step 5: Verify Tables

```sql
SHOW TABLES;
```

Expected tables:

```text
aisles
departments
products
orders
order_products_train
```

### Step 6: Run SQL Queries

Open:

```text
sql/analysis_queries.sql
```

Run each query in MySQL Workbench to reproduce the analysis.

---

## 🧮 Example SQL Analysis

### Top 10 Most Reordered Products

```sql
SELECT
    p.product_id,
    p.product_name,
    COUNT(*) AS total_orders,
    SUM(op.reordered) AS reorder_count,
    ROUND(
        SUM(op.reordered) / COUNT(*) * 100,
        2
    ) AS reorder_rate_percentage
FROM order_products_train op
JOIN products p
    ON op.product_id = p.product_id
GROUP BY
    p.product_id,
    p.product_name
ORDER BY
    reorder_rate_percentage DESC
LIMIT 10;
```

This query calculates the reorder rate of products and identifies the products with the highest reorder percentage.

---

## 📊 Skills Demonstrated

This project demonstrates practical knowledge of:

* SQL Data Analysis
* Relational Database Management
* Data Cleaning & Preparation
* Exploratory Data Analysis
* Customer Behavior Analysis
* Product Performance Analysis
* Business Intelligence
* Data-Driven Decision Making
* Business Recommendation Generation

---

## 💼 Resume Description

**Customer Purchasing Behavior & Product Performance Analysis | SQL**

* Analyzed grocery shopping data using **MySQL** to identify customer purchasing patterns, product performance, reorder behavior, and order trends.
* Developed **20+ SQL queries** using joins, aggregations, subqueries, grouping, filtering, and ranking techniques to generate business insights.
* Identified high-performing products, customer ordering patterns, peak purchase periods, and department-level performance to support **marketing, inventory, and customer-retention strategies**.

---

## 🎓 Project Learning Outcomes

Through this project, I gained practical experience in:

* Writing complex SQL queries
* Working with multiple relational tables
* Joining datasets using primary and foreign keys
* Performing customer behavior analysis
* Calculating business KPIs
* Analyzing product reorder patterns
* Converting SQL results into business insights
* Developing data-driven recommendations

---

## 👨‍💻 Author

**Vishanth M.S.**

Computer Science Engineering Student

### Areas of Interest

* Data Analytics
* Machine Learning
* Artificial Intelligence
* Business Intelligence
* SQL
* Python

---

## ⭐ Conclusion

This project demonstrates how **SQL-based analytics can transform raw e-commerce transaction data into actionable business insights**.

By understanding customer purchasing behavior, reorder patterns, product performance, and ordering trends, businesses can improve **customer retention, marketing effectiveness, inventory management, and overall decision-making**.
