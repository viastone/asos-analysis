This project analyzes a dataset of ASOS retail products to uncover patterns in pricing, brand positioning, and stock availability. The core idea is to estimate "phantom revenue" - potential sales lost due to out of stock sizes - and use that metric to drive several layers of analysis.

Data preparation: The raw CSV is cleaned by coercing prices to numeric values and dropping invalid rows. Brand names are extracted from product descriptions using string parsing, then standardized through a mapping dictionary to merge inconsistent variants (e.g. "New" to "New Look"). Brands with very few listings are filtered out to avoid noisy results.
Stockout metrics: For each product, the size availability string is parsed to count how many sizes are marked "Out of stock" versus the total offered. This produces a Stockout_Count and Stockout_Rate per item, and a Lost_Revenue figure (price times stockout count) representing missed sales potential.

**Visualization 1** - Scatter plot: Brands are plotted by average price versus average stockout rate, with point size representing total lost revenue. Reference lines at price 40 and stockout rate 0.4 highlight a "premium but understocked" quadrant, with those brands labeled directly on the chart.

**Visualization 2** - Bar charts: Two horizontal bar charts rank product categories - one by average stockout rate, the other by total lost revenue - identifying which categories suffer most from availability issues.

**Visualization 3** - Spider (radar) chart: Products are bucketed into price tiers (under 20, 20-50, 50-100, 100-200, over 200), and the average stockout rate per tier is plotted on a polar chart, showing whether cheaper or pricier items run out more often.

Overall, the project tells a story about where ASOS may be leaving money on the table - which brands, categories, and price segments are most affected by inventory shortages relative to demand signals like price point.
