# Task-1-Data-Cleaning-and-Preprocessing
This project demonstrates how to clean the [Netflix Movies and TV Shows dataset](https://www.kaggle.com/datasets/shivamb/netflix-shows) from Kaggle using Python and pandas. The final output is saved in an Excel file for easy use and further analysis.
## 📁 Dataset Used

- **Name**: Netflix Movies and TV Shows
- **File**: `netflix_titles.csv`
- **Source**: Kaggle

---

##  Cleaning Goals

- Remove duplicates
- Handle missing values
- Convert columns to appropriate data types
- Standardize column names
- Save the cleaned data into an Excel file

---

## 🧪 Step-by-Step Cleaning Process

### 🔹 1. Import Libraries

```python
import pandas as pd
Loads the pandas library for data manipulation.

🔹 2. Load the Dataset

df_netflix = pd.read_csv("netflix_titles.csv")
Loads the raw dataset into a pandas DataFrame.

🔹 3. Remove Duplicate Rows

df_netflix.drop_duplicates(inplace=True)
Removes any duplicated rows in the dataset.

🔹 4. Fill Missing Values in 'country'
python
Copy
Edit
df_netflix['country'] = df_netflix['country'].fillna('Unknown')
Replaces missing country values with "Unknown" to ensure consistency.

🔹 5. Convert date_added to Datetime Format

df_netflix['date_added'] = pd.to_datetime(df_netflix['date_added'], errors='coerce')
Converts the date_added column to a proper datetime format. Invalid values are turned into NaT.

🔹 6. Standardize Column Names

df_netflix.columns = df_netflix.columns.str.lower().str.replace(' ', '_')
Makes all column names lowercase and replaces spaces with underscores to improve readability and coding convenience.

🔹 7. Export the Cleaned Dataset to Excel

with pd.ExcelWriter("cleaned_netflix_dataset.xlsx") as writer:
    df_netflix.to_excel(writer, sheet_name="Netflix", index=False)
Saves the cleaned dataset to an Excel file with a sheet named "Netflix".

✅ Output
cleaned_netflix_dataset.xlsx – Excel file containing the cleaned data in a sheet named Netflix
