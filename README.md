
### **Document Summary: Internship Assignment - Market Sentiment and Trader Behavior Analysis**

This Jupyter Notebook, titled "internship_assignment.ipynb," details a data analysis project aimed at exploring the relationship between market sentiment (specifically the Fear & Greed Index) and trader performance (profitability, leverage use, etc.). The goal is to identify patterns and generate insights for smarter trading strategies.

**1. Strategic Framework (The "Blueprint")**

* **Objective:** To quantify market sentiment as a leading indicator for trader profitability and risk.
* **Hypotheses:**
* **The "Greed Trap":** Retail traders over-leverage during "Extreme Greed" periods, leading to higher liquidation rates.
* **"Smart Money" vs. "Dumb Money":** Top traders ("Smart Money") behave inversely to the herd, buying during fear and selling during greed.


* **Metrics:** The analysis moves beyond simple PnL to use advanced metrics like Win Rate, Risk-Reward Ratio, and Sharpe Ratio (implied).

**2. Data Processing (Phase 2)**

* **Data Sources:**
* `df_trades`: Historical trader data (Account, Coin, Execution Price, Size, Side, Timestamp, PnL, etc.) sourced from a Google Drive link.
* `df_sentiment`: Fear & Greed Index data (timestamp, value, classification, date) sourced from a Google Drive link.


* **Cleaning & Merging:**
* Dates were parsed and standardized (e.g., converting 'Timestamp IST' to datetime objects).
* The datasets were merged using a 'date_key' (Left Join on trades).
* Rows with missing sentiment data were dropped.


* **Feature Engineering:**
* **Implied Capital:** Calculated `Size USD` (replacing 0 with NaN to avoid errors).
* **ROI %:** Calculated as `(Closed PnL / Size USD) * 100` to normalize performance.
* **Win Flag:** Created a binary 'is_win' column (1 if PnL > 0, else 0).
* **Sentiment Score:** Mapped sentiment categories (e.g., 'Extreme Fear', 'Greed') to numerical scores (1-5).



**3. Analysis & Insights (Phase 3)**

* **Insight 1: Market Mood vs. Trader Performance**
* Data was grouped by sentiment classification ('Extreme Fear' to 'Extreme Greed').
* **Findings:**
* **Extreme Greed:** Highest ROI (4.00%) and Win Rate (46%), but also high volume.
* **Fear/Extreme Fear:** Lower ROIs (0.43% - 1.54%) and Win Rates (37% - 42%).
* This partially challenges the "Greed Trap" hypothesis for the *average* trader in this specific dataset, as performance peaked during Greed.




* **Insight 2: Smart Money vs. Retail Behavior**
* Traders were segmented into "Smart Money" (Top 10% by profit) and "Retail".
* **Findings:**
* **Smart Money:** Massive outperformance during "Extreme Greed" (17.74% avg ROI) compared to Retail (2.96%).
* **Divergence:** Smart Money maintains positive and growing ROI across all sentiments, capitalizing significantly more on extreme market conditions than retail traders.





**4. Visualizations**
![Alt Text](visual.png)
* **Chart 1:** Bar plot showing "Average Trader ROI (%) Across Market Sentiments".
* **Chart 2:** Line plot comparing "Smart Money vs. Retail Performance" across sentiment categories.

**Conclusion:** The analysis successfully integrated disparate datasets to reveal that while "Greed" periods are generally profitable, "Smart Money" extracts significantly higher returns during these times compared to retail traders, suggesting superior execution or risk management during high-sentiment periods.
