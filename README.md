# Ship Fuel Efficiency & Emissions Dashboard

## Task objective
Analyze ship fuel efficiency data and build an interactive Streamlit dashboard that surfaces key performance indicators (KPIs) around fuel consumption, CO2 emissions, and engine efficiency — with filters for ship type, route, and fuel type — so a user can explore the fleet's environmental and operational performance.

## Your approach
1. **Data loading**: Loaded `ship_fuel_efficiency.csv`, containing 1,440 records with columns for ship ID, ship type, route, month, distance, fuel type, fuel consumption, CO2 emissions, weather conditions, and engine efficiency.
2. **Initial inspection**: Used `head()`, `info()`, and `describe()` to understand the structure, data types, and summary statistics (e.g. average engine efficiency ~82.6%, average fuel consumption ~4,844 liters per trip).
3. **Data cleaning**:
   - Checked for and removed duplicate rows (none were found — all 1,440 rows were unique).
   - Converted the `month` column from a plain object/string type to an ordered categorical type (Jan–Dec), ensuring charts and filters sort chronologically instead of alphabetically.
4. **KPI calculation**: Computed the core metrics needed for the dashboard:
   - Total fuel consumption
   - Total CO2 emissions
   - Average engine efficiency
   - Top 5 ships by fuel consumption
   - Top 5 routes by CO2 emissions
5. **Data aggregation**: Grouped the cleaned data by `ship_type`, `route_id`, `fuel_type`, and `month` to produce a summarized table (fuel consumption, CO2 emissions, and average efficiency per group) that powers the dashboard's interactive filtering and time-series views.
6. **Dashboard build**: Wrote a Streamlit app (`app.py`) that:
   - Loads and cleans the data the same way as the notebook.
   - Displays the three headline KPIs as metric cards.
   - Provides sidebar multiselect filters for ship type, route, and fuel type.
   - Recomputes KPIs dynamically based on the selected filters.
   - Renders Altair line charts of monthly fuel consumption and CO2 emissions, sorted in proper calendar order.
7. **Dependencies**: Installed `streamlit` and `altair` to support the dashboard and its charts.

## Results and findings
- **Dataset**: 1,440 trip records, no duplicates, 10 columns, no missing values.
- **Fleet-wide totals**:
  - Total fuel consumption: **6,975,715.01 liters**
  - Total CO2 emissions: **19,246,255.03 kg**
  - Average engine efficiency: **82.58%**
- **Top 5 ships by fuel consumption**: NG012, NG071, NG037, NG048, and NG016 lead the fleet, each consuming between roughly 152,900 and 163,700 liters.
- **Top 5 routes by CO2 emissions**: Lagos–Apapa (5.52M kg), Port Harcourt–Lagos (5.14M kg), Escravos–Lagos (5.05M kg), and Warri–Bonny (3.55M kg) are the highest-emitting routes, suggesting these routes are the best targets for efficiency improvements or fuel-type changes.
- **Deliverable**: A working Streamlit dashboard (`app.py`) that lets a user filter by ship type, route, and fuel type and see KPIs and monthly trend charts update in real time — ready to run locally via `streamlit run app.py`.
