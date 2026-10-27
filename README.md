#  Global Video Game Sales Analysis

An end-to-end data analytics project that cleans, analyzes, and visualizes historical video game sales data using **Python** and **Power BI**. The goal is to understand sales trends over time, the best-performing genres, platforms, and publishers, and how player preferences differ across regions.

![Power BI Dashboard](images/FDVAproject.png)

---

##  Aim

To clean, analyze, and visualize global video game sales data using Python and Power BI to identify sales trends, top genres, platforms, and publishers, and regional differences in buying behaviour across North America, Europe, Japan, and the rest of the world.

##  Domain

Gaming Industry Analytics · Sales Analytics · Business Intelligence

##  Problem Statement

The video game industry spans dozens of platforms, hundreds of publishers, and very different regional markets. Publishers and retailers need to know which genres and platforms drive revenue, how sales have changed over the years, and how preferences vary by region. This project turns raw sales data into insights that support data-driven decisions.

---

##  Dataset

**Video Game Sales (vgsales)**: every game that sold more than 100,000 copies.

| Property | Value |
|---|---|
| Records | 16,598 |
| Fields | 11 |
| Platforms | 31 |
| Genres | 12 |
| Publishers | 577 |
| Years | 1980 – 2020 |
| Unit | Millions of copies sold |

| Column | Description |
|---|---|
| `Rank` | Overall rank by global sales |
| `Name` | Game title |
| `Platform` | Console or system (PS2, Wii, X360, DS, …) |
| `Year` | Year of release |
| `Genre` | Game genre (Action, Sports, Shooter, …) |
| `Publisher` | Publishing company |
| `NA_Sales` | North America sales |
| `EU_Sales` | Europe sales |
| `JP_Sales` | Japan sales |
| `Other_Sales` | Rest of the world sales |
| `Global_Sales` | Total worldwide sales |

---

## 🛠️ Tech Stack

- **Python**: Pandas, NumPy, Matplotlib, Seaborn
- **Power BI**: interactive dashboard
- **ReportLab**: PDF report generation

---

##  Project Structure

```
├── data/
│   └── vgsales.csv                          # Raw dataset
├── charts/                                  # Python-generated charts
├── images/
│   └── FDVAproject.png                      # Power BI dashboard screenshot
├── build.py                                 # Cleaning, analysis, charts and PDF report
├── Video_Game_Sales_Analysis_Report.pdf     # Final project report
└── README.md
```

---

##  Data Cleaning

- Checked structure, dimensions, and data types
- Found missing values: **271** records with no `Year` and **58** with no `Publisher`
- Trimmed extra spaces from text fields
- Converted `Year` to an integer field
- Filled missing `Publisher` with `"Unknown"`
- Kept records with missing `Year` in totals but excluded them from year-wise analysis
- Removed **2** duplicate records (same game, platform, and year)
- Checked that no sales values are zero or negative
- Checked that NA + EU + JP + Other matches `Global_Sales` (within 0.02M rounding)
- Noted that 2017 and 2020 have very few records and are incomplete

**Final dataset:** 16,596 records

##  Feature Engineering

| Feature | Logic |
|---|---|
| Regional Sales Share | `Regional Sales / Global Sales` |
| Dominant Region | Region with the highest sales for each game |
| Decade | `(Year // 10) * 10` |
| Sales Category | Niche (<0.1M) · Moderate (0.1–1M) · Hit (1–5M) · Blockbuster (>5M) |
| Target Sales | Calculated measure in Power BI, compared with actual sales in a KPI visual |

---

##  Power BI Dashboard

The dashboard includes:

- **Global Sales by Year and Genre**: line chart of sales trends per genre
- **Count of Titles by Platform**: number of games released on each platform
- **Global Sales by Platform**: treemap of platform sales share
- **Sales by Genre**: separate bar charts for Global, NA, EU, JP, and Other regions
- **Global Sales vs Target**: KPI comparing actual sales to the goal
- **Regional Sales Breakdown**: pie chart of total sales by region

---

##  Key Insights

-  **Total global sales** are about **8,920 million** copies. North America is the biggest market (**49.3%**), followed by Europe (27.3%), Japan (14.5%), and other regions (8.9%).
-  Sales **peaked in 2008** (~679M) and declined after 2011.
-  **Action** is the top genre (1,751M), followed by Sports (1,331M) and Shooter (1,037M).
- 🇯🇵 **Japan is different**: Role-Playing is its top genre (27.3% of Japanese sales), while Shooter games sell very little there.
-  **PS2** is the best-selling platform (1,256M), followed by X360 and PS3. DS and PS2 have the most titles (2,100+ each).
-  **Nintendo** leads publishers by sales (1,787M). Electronic Arts has the most titles.
-  **Wii Sports** is the best-selling game (82.7M), and most of the top 10 are Nintendo titles.
-  NA sales correlate most strongly with global sales (0.94); Japan has the weakest correlation (0.61).
-  About **87%** of titles sold under 1 million copies, so a small number of blockbusters drive most revenue.

---

##  How to Run

1. Clone the repository
   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   cd <repo-name>
   ```
2. Install dependencies
   ```bash
   pip install pandas numpy matplotlib seaborn reportlab pillow
   ```
3. Run the analysis
   ```bash
   python build.py
   ```
   The charts are saved to `charts/` and the report is generated as `Video_Game_Sales_Analysis_Report.pdf`.
4. Open the `.pbix` file in **Power BI Desktop** to explore the dashboard.

---

## Result

This project turns the raw video game sales dataset into a clean analytical dataset with Python and presents the insights through an interactive Power BI dashboard. It shows how the market grew and declined over the years, which genres, platforms, and publishers drive sales, and how player preferences in Japan differ from those in North America and Europe.

---

##  Author

Varneka K
