# London Bike Sharing Data Analysis

## Project Overview  
This project analyzes the **London Bike Sharing Dataset**, performing data cleaning, transformation, and exporting a refined dataset for **Tableau visualization**.

## Features  
- Downloads the dataset from **Kaggle** via the **Kaggle API**.
- Extracts and loads data for processing using **pandas**.
- Cleans and transforms key columns for better readability.
- Saves the final dataset as an **Excel file** for visualization.

## Requirements  
Install the required dependencies using:

```bash
pip install pandas kaggle zipfile
```

## Setup Instructions  

### 1. Obtain a Kaggle API Key  
- Visit your [Kaggle account](https://www.kaggle.com/account).
- Under **API**, click **Create New API Token**.
- Place the downloaded `kaggle.json` file in:
  - Linux/Mac: `~/.kaggle/`
  - Windows: `C:\Users\<YourUser>\.kaggle\`

### 2. Download & Extract Data  
Run the following in your Jupyter Notebook:

```python
import kaggle
import zipfile

# Download dataset from Kaggle
!kaggle datasets download -d hmavrodiev/london-bike-sharing-dataset

# Extract data
zipfile_name = 'london-bike-sharing-dataset.zip'
with zipfile.ZipFile(zipfile_name, 'r') as file:
    file.extractall()
```

### 3. Load Dataset  
```python
import pandas as pd

bikes = pd.read_csv("london_merged.csv")
```

## Data Processing Steps  

1. **Exploration**  
   - Counts unique values in `weather_code` and `season` columns.

2. **Cleaning & Transformation**  
   - Renames columns for clarity.
   - Converts humidity values to **percentages**.
   - Maps numeric **season codes** (0-3) to actual season names.
   - Maps numeric **weather codes** to descriptive labels.
   - Converts **season and weather columns** from integers to strings.

3. **Final Output**  
   - Saves the cleaned dataset as an **Excel file**:
   ```python
   bikes.to_excel("london_bikes_final.xlsx", sheet_name="Data")
   ```
   - This file is **optimized for Tableau visualization**.

## Dataset Information  
- **Source**: [Kaggle: London Bike Sharing Dataset](https://www.kaggle.com/datasets/hmavrodiev/london-bike-sharing-dataset)
- **Columns Include**:
  - `timestamp` - Date and time of bike usage.
  - `cnt` - Number of bikes used.
  - `t1` - Temperature.
  - `t2` - Feels-like temperature.
  - `hum` - Humidity (before conversion to percentage).
  - `wind_speed` - Wind speed (km/h).
  - `season` - Numeric season code (later mapped to strings).
  - `weather_code` - Numeric weather condition code.

## License  
This project uses the **London Bike Sharing Dataset** from Kaggle. Refer to Kaggle’s dataset page for license details.

## Tableau Visualization 

[Here](https://public.tableau.com/shared/Q39D9WNRF?:display_count=n&:origin=viz_share_link) is how the visualization turned out



