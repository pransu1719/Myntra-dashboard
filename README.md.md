<div align="center">

# -- ! Myntra Sales & Product Analytics Dashboard ! --
### *Interactive Power BI Report for Order, Revenue & Product Performance Analysis*

[![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-Measures%20%26%20KPIs-E91E63?style=for-the-badge&logo=powerbi&logoColor=white)](https://learn.microsoft.com/en-us/dax/)
[![Data Model](https://img.shields.io/badge/Data%20Model-6%20Tables-4CAF50?style=for-the-badge&logo=databricks&logoColor=white)](https://powerbi.microsoft.com/)
[![Dashboard](https://img.shields.io/badge/Dashboard-2%20Pages-FF3F6C?style=for-the-badge&logo=powerbi&logoColor=white)](https://powerbi.microsoft.com/)

<br/>

> *"Data tells you what happened — a good dashboard tells you what to do next."*

</div>

---

## 📋 Table of Contents

- [📌 Overview](#-overview)
- [🎯 Problem Statement](#-problem-statement)
- [✨ Key Features](#-key-features)
- [🏗️ Project Structure](#️-project-structure)
- [🗃️ Data Model](#️-data-model)
- [🔄 Project Workflow](#-project-workflow)
- [📊 Page 1 — Sales Overview](#-page-1--sales-overview)
- [🛍️ Page 2 — Product Analysis](#️-page-2--product-analysis)
- [🧮 DAX Measures](#-dax-measures)
- [🛠️ Tech Stack](#️-tech-stack)
- [🚀 How to Run](#-how-to-run)
- [📈 Results & Insights](#-results--insights)
- [🏆 Advantages](#-advantages)
- [📄 License](#-license)
- [👤 Author](#-author)
- [🙏 Acknowledgements](#-acknowledgements)

---

## 📌 Overview

The **Myntra Sales & Product Analytics Dashboard** is an interactive, two-page **Power BI** report that analyses e-commerce order data for the fashion platform Myntra. It combines order volumes, revenue, order status, brand performance, category mix, and city-tier distribution into a single, filter-driven view built on a **1920 × 1080** canvas with the **Fluent 2** theme and Myntra-style branding.

This project is designed to:
- Track **Total Orders** and **Total Revenue** at a glance through KPI cards
- Compare performance across **Brands**, **Categories**, and **City Tiers**
- Break down orders by **Order Status** to understand fulfilment outcomes
- Identify the **Top 10 products by revenue** and the product mix per category
- Let users slice the whole page dynamically using Brand, Category, and City Tier filters

---

## 🎯 Problem Statement

> **Objective:** Build an interactive business-intelligence dashboard that turns raw Myntra order data into clear, actionable sales and product insights.

You are building a reporting solution for a business or analytics team that needs to monitor sales health and spot top-performing brands, categories, products, and regions — without writing queries every time. The dashboard must summarise key metrics, support drill-down through slicers, and highlight what drives revenue.

| 📂 Page | 📄 Type | 🔍 Description |
|---------|---------|----------------|
| Sales Overview | Summary Dashboard | KPIs, order status by brand & category, city-tier split |
| Product Analysis | Deep-Dive Dashboard | Revenue by brand and city tier, product distribution, Top 10 products |
| Slicers | Interactivity | Filter by Brand, Category, and City Tier |
| KPI Cards | Metrics | Total Orders and Total Revenue |
| Data Model | Backend | Orders master plus seasonal order and catalog tables |

The goal is to demonstrate **end-to-end Power BI skills** — data modelling, DAX measures, visual design, and interactive report building.

---

## ✨ Key Features

| Feature | Description |
|--------|-------------|
| 📄 **2-Page Report** | *Sales Overview* for the big picture, *Product Analysis* for the deep dive |
| 🔢 **KPI Cards** | Headline **Total Orders** and **Total Revenue** values |
| 🎛️ **Dynamic Slicers** | Brand (dropdown), Category (dropdown), and City Tier (list) filters |
| 📦 **Order Status Breakdown** | Orders by brand and by category, split by order status |
| 🏙️ **City-Tier Analysis** | Order share (donut) and revenue (column) by city tier |
| 🏷️ **Brand Revenue Ranking** | Bar chart of Total Revenue by brand |
| 🥇 **Top 10 Products** | Table limited to the 10 highest-revenue products via a Top N filter |
| 🍩 **Product Distribution** | Donut showing product counts by category |
| 🧭 **Sidebar Navigation** | Left-hand icon panel for page navigation and filters |
| 🎨 **Branded Design** | Myntra logo header, custom icons, and the Fluent 2 theme |

---

## 🏗️ Project Structure

```
📦 myntra-dashboard/
│
├── 📄 Mayntra_dashboard.pbix     ← Power BI report (data model + 2 report pages)
│
└── 📄 README.md                  ← Project documentation
```

> 💡 *Optional:* add a `screenshots/` folder with page previews (see [Results & Insights](#-results--insights)).

---

## 🗃️ Data Model

The report is built on **six tables** loaded into the Power BI data model:

| Table | Role |
|-------|------|
| 🧾 `myntra_orders_master` | **Main fact table** — drives all KPIs, slicers, and most visuals |
| 🎉 `myntra_festive_orders` | Festive-season orders (used for order status and product distribution) |
| ☀️ `myntra_summer_orders` | Summer-season orders |
| ❄️ `myntra_winter_orders` | Winter-season orders |
| 👗 `myntra_product_catalog` | Product catalog reference table |
| 🌐 `myntra_web_catalog` | Web catalog reference table |

**Key fields used in the report:**

| Field | Table | Used For |
|-------|-------|----------|
| `Brand Name` | `myntra_orders_master` | Brand slicer, brand charts, product table |
| `Category` | `myntra_orders_master` | Category slicer, category chart, product distribution |
| `City Tier` | `myntra_orders_master` | City-tier slicer, donut, revenue column chart |
| `Order Status` | `myntra_orders_master` / `myntra_festive_orders` | Status breakdown in charts |
| `Order_ID` | `myntra_orders_master` | Order counts |
| `Product Name` | `myntra_orders_master` | Top 10 products table |

---

## 🔄 Project Workflow

```
Raw Myntra Order Data
      │
      ▼
┌─────────────────────────────┐
│   Load Data into Power BI   │  ← 6 tables (orders, seasonal, catalogs)
└────────────┬────────────────┘
             │
             ▼
┌─────────────────────────────┐
│   Build Data Model          │  ← Tables + relationships
└────────────┬────────────────┘
             │
             ▼
┌─────────────────────────────┐
│   Create DAX Measures       │  ← Total orders, Total Revenue
└────────────┬────────────────┘
             │
     ┌───────┴────────┐
     ▼                ▼
┌─────────────┐   ┌──────────────────┐
│   Page 1    │   │     Page 2       │
│   Sales     │   │     Product      │
│   Overview  │   │     Analysis     │
└──────┬──────┘   └────────┬─────────┘
       │                   │
       ▼                   ▼
┌─────────────────────────────┐
│  Slicers + Cross-filtering  │  ← Brand / Category / City Tier
└────────────┬────────────────┘
             │
             ▼
      Insights & Decisions ✅
```

---

## 📊 Page 1 — Sales Overview

### 📝 1. What does this page show?

The **Sales Overview** page is the executive summary. It gives a quick read on how many orders were placed, how much revenue was generated, and how orders are distributed by brand, category, order status, and city tier.

---

### 🗺️ 2. Visuals — Overview

| # | Visual | Type | Fields Used |
|---|--------|------|-------------|
| 1️⃣ | **Total Orders** | Card | Measure: `Total orders` |
| 2️⃣ | **Total Revenue** | Card | Measure: `Total Revenue` |
| 3️⃣ | **Order ID by City Tier** | Donut Chart | `City Tier`, count of `Order_ID` |
| 4️⃣ | **Orders by Category** | Column Chart | `Category`, `Order Status`, order count |
| 5️⃣ | **Orders by Brand** | Clustered Bar Chart | `Brand Name`, `Order Status`, order count |
| 6️⃣ | **Brand** | Slicer (Dropdown) | `Brand Name` |
| 7️⃣ | **Category** | Slicer (Dropdown) | `Category` |
| 8️⃣ | **City Tier** | Slicer (List) | `City Tier` |

---

### 🔢 3. KPI Cards

> Large headline cards showing the two most important numbers for the current filter selection.

- **Total Orders** — number of orders in scope
- **Total Revenue** — revenue generated by those orders

Both cards update instantly when any slicer is changed.

---

### 🍩 4. Order ID by City Tier

> Donut chart showing how orders split across city tiers (e.g., Tier 1, Tier 2, Tier 3).

Useful for understanding where demand comes from geographically.

---

### 📊 5. Orders by Category & Orders by Brand

> Two charts that break order counts down by **Order Status**.

- **Column chart** → orders per product category
- **Clustered bar chart** → orders per brand

Splitting by status shows not just *how many* orders there are, but *how many were successfully fulfilled vs. cancelled, returned, or pending*.

---

### 🎛️ 6. Slicers

> Three slicers on the left side let users narrow every visual on the page.

| Slicer | Style | Filters By |
|--------|-------|------------|
| Brand | Dropdown | Brand Name |
| Category | Dropdown | Category |
| City Tier | List | City Tier |

---

## 🛍️ Page 2 — Product Analysis

### 🔍 7. What does this page show?

The **Product Analysis** page goes deeper into *what* is selling and *where* the revenue comes from — by brand, by city tier, by category mix, and by individual product.

---

### 🗺️ 8. Visuals — Overview

| # | Visual | Type | Fields Used |
|---|--------|------|-------------|
| 1️⃣ | **Product Distribution** | Donut Chart | `Category`, count of festive `Product name` |
| 2️⃣ | **Revenue by Brand** | Bar Chart | `Brand Name`, `Total Revenue` |
| 3️⃣ | **City Tier Analysis** | Column Chart | `City Tier`, `Total Revenue` |
| 4️⃣ | **Total Orders** | Card | Measure: `Total orders` |
| 5️⃣ | **Festive Order Status** | Donut Chart | festive `Order Status`, count of `Order_ID` |
| 6️⃣ | **Top 10 Products by Revenue** | Table | `Product Name`, `Brand Name`, `Category`, `Total orders`, `Total Revenue` |

---

### 🥇 9. Top 10 Products by Revenue

> A table listing the best-performing products with their brand, category, order count, and revenue.

The table uses a **Top N filter** (Top 10 by `Total Revenue`), so it always shows the ten highest-earning products for the current context.

---

### 🏷️ 10. Revenue by Brand & City Tier

> Bar and column charts that rank **brands** and **city tiers** by `Total Revenue`.

These answer two core business questions: *which brands drive the most revenue?* and *which city tiers contribute the most?*

---

### 🍩 11. Product Distribution & Festive Order Status

> Two donut charts that show the **category mix** of products and the **order-status split** for festive-season orders.

---

## 🧮 DAX Measures

Two core measures are defined on the `myntra_orders_master` table and reused across both pages:

| Measure | Purpose |
|---------|---------|
| 🔢 `Total orders` | Counts the orders in the current filter context |
| 💰 `Total Revenue` | Sums revenue in the current filter context |

```dax
-- Reference definitions (adjust column names to match your model)
Total orders  = DISTINCTCOUNT ( myntra_orders_master[Order_ID] )
Total Revenue = SUM ( myntra_orders_master[<Revenue Column>] )
```

> 📝 *The snippet above is an illustrative definition. Open the `.pbix` and check the Model view for the exact expressions.*

---

## 🛠️ Tech Stack

| Tool | Version | Purpose |
|------|---------|---------|
| 📊 **Power BI Desktop** | 2026.10+ | Report authoring and data modelling |
| 🧮 **DAX** | Built-in | Calculated measures (Total orders, Total Revenue) |
| 🔄 **Power Query** | Built-in | Data loading and transformation |
| 🎨 **Fluent 2 Theme** | CY26SU10 | Report theme and styling |
| 🖼️ **Custom Images** | PNG | Myntra logo and navigation icons |
| 📁 **PBIR Format** | v3.x | Report definition format used by the project |

---

## 🚀 How to Run

1. **Download** or clone this repository.
2. Install **[Power BI Desktop](https://powerbi.microsoft.com/desktop/)** (free, Windows).
3. Double-click **`Mayntra_dashboard.pbix`** to open it.
4. Use the **left sidebar** to switch between *Sales Overview* and *Product Analysis*.
5. Use the **Brand**, **Category**, and **City Tier** slicers to filter, and click any chart element to cross-filter the rest of the page.

> ⚠️ Power BI Desktop is Windows-only. On macOS/Linux, use Power BI Service (web) after publishing the report.

---

## 📈 Results & Insights

After exploring the dashboard, users can:

- ✅ **Monitor Headline KPIs** — Total Orders and Total Revenue update with every filter
- 🏷️ **Rank Brands** — see which brands lead in both order volume and revenue
- 📦 **Judge Fulfilment Health** — compare order-status mix across brands and categories
- 🏙️ **Compare City Tiers** — see which tiers generate the most orders and revenue
- 🥇 **Spot Best-Sellers** — the Top 10 table surfaces the highest-revenue products
- 🎉 **Understand Festive Performance** — festive order status and product mix at a glance

### 🖼️ Dashboard Preview

<!-- Add your screenshots to a /screenshots folder and uncomment the lines below -->
<!--
| Sales Overview | Product Analysis |
|:--------------:|:----------------:|
| ![Sales Overview](screenshots/sales-overview.png) | ![Product Analysis](screenshots/product-analysis.png) |
-->

> 📸 *Screenshots coming soon — export each page from Power BI via **File → Export → PDF** or take a screenshot, then add them to `screenshots/`.*

---

## 🏆 Advantages

| Advantage | Detail |
|-----------|--------|
| 🎓 **Portfolio Ready** | Showcases data modelling, DAX, and dashboard design in one project |
| 🔄 **Interactive** | Slicers and cross-filtering let users explore data without writing queries |
| 📚 **Clear Structure** | Summary page first, deep-dive page second — a natural analysis flow |
| 🎨 **Polished Design** | Branded header, custom icons, and consistent Fluent 2 styling |
| ⚡ **Fast Insights** | Key KPIs and top products visible within seconds |
| 🧪 **Extensible** | Easy to add pages such as Seasonal Trends, Returns, or Customer Analysis |
| 🗃️ **Scalable Model** | Separate seasonal and catalog tables make future expansion simple |
| 📖 **Readable Layout** | Logical grouping and consistent spacing across both pages |

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for full details.

```
MIT License — Free to use, modify, and distribute with attribution.
```

> ⚠️ *This is an educational/portfolio project. Myntra name and logo are trademarks of their respective owners and are used here for illustrative purposes only.*

---

## 👤 Author

<div align="center">

### Your Name

[![GitHub](https://img.shields.io/badge/GitHub-yourhandle-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/yourhandle)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/your-profile/)

> *"Every great dashboard starts with a single question."*

**🎓 Role:** Data Analyst | Power BI Enthusiast \
**📍 Location:** India\
**🛠️ Skills:** Power BI · DAX · Data Modelling · Data Visualization · Business Analytics

</div>

---

## 🙏 Acknowledgements

Special thanks to the following resources and communities that made this project possible:

- 📚 [Power BI Documentation](https://learn.microsoft.com/en-us/power-bi/) — Official Microsoft Power BI reference
- 🧮 [DAX Guide](https://dax.guide/) — Complete DAX function reference
- 🎨 [Power BI Community](https://community.fabric.microsoft.com/) — Questions, answers, and design inspiration
- 🎥 [Guy in a Cube](https://www.youtube.com/@GuyInACube) — Power BI tutorials and tips
- 📖 [SQLBI](https://www.sqlbi.com/) — Data modelling and DAX best practices
- 💬 [Stack Overflow Community](https://stackoverflow.com/) — Problem-solving support

---

<div align="center">

---

*Made with ❤️ and ☕ — Last updated: 4 November, 2026*

</div>
