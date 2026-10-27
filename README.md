# Last Mile Delivery Analysis

> Analysis of last-mile delivery performance for Brazilian e-commerce orders: order timelines, delivery delays, and customer/seller locations. *(Edit this to match what your notebook actually does.)*

This project analyses the **Olist Brazilian E-Commerce dataset** and is built in **Google Colab** using Python.

---

## Dataset

- **Source:** [Brazilian E-Commerce Public Dataset by Olist (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

The dataset page contains **more than 5 CSV files**, but this project uses **only the following 5**:

| # | File | Description |
|---|------|-------------|
| 1 | `olist_customers_dataset.csv` | Customer IDs and location details |
| 2 | `olist_geolocation_dataset.csv` | Zip code prefixes with latitude/longitude |
| 3 | `olist_order_items_dataset.csv` | Items in each order, price, freight, seller |
| 4 | `olist_orders_dataset.csv` | Order status and purchase/delivery timestamps |
| 5 | `olist_sellers_dataset.csv` | Seller IDs and location details |

> ⚠️ **Do not use the other files** from the dataset (payments, reviews, products, category translation). Using them will not match the project's code or results.

---

## Repository Structure

```
├── last_mile_delivery_analysis.ipynb   # Main Colab notebook
├── README.md                    # This file
└── data/                        # (optional) not committed, see note below
```

> The CSV files are **not stored in this repo**. Please download them from Kaggle using the link above.

---

## Setup Guide: Running the Project in Google Colab

### Step 1: Download the dataset
1. Open the [Kaggle dataset page](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) (free Kaggle account required).
2. Click **Download** to get the ZIP file.
3. Unzip it on your computer.
4. Keep only the 5 files listed in the table above.

### Step 2: Open the notebook in Colab
1. Open the `.ipynb` file from this repo.
2. Click **Open in Colab** (or go to [colab.research.google.com](https://colab.research.google.com) → **File → Upload notebook**).

### Step 3: Upload the 5 CSV files to Colab

**Option A: Direct upload (quickest, but files vanish when the session ends)**
1. Click the **folder icon** 📁 in Colab's left sidebar.
2. Click the **Upload** icon and select the 5 CSV files.

Or upload with code:
```python
from google.colab import files
uploaded = files.upload()   # select the 5 CSV files
```

**Option B: Google Drive (files persist across sessions)**
1. Create a folder in Drive, e.g. `MyDrive/olist_data/`, and upload the 5 CSVs there.
2. Mount Drive in the notebook:
```python
from google.colab import drive
drive.mount('/content/drive')
```
3. Use the Drive path when reading files:
```python
DATA_PATH = '/content/drive/MyDrive/olist_data/'
```

### Step 4: Load the files in the notebook
```python
import pandas as pd

# Use '' for Option A, or DATA_PATH for Option B
DATA_PATH = ''

customers   = pd.read_csv(DATA_PATH + 'olist_customers_dataset.csv')
geolocation = pd.read_csv(DATA_PATH + 'olist_geolocation_dataset.csv')
order_items = pd.read_csv(DATA_PATH + 'olist_order_items_dataset.csv')
orders      = pd.read_csv(DATA_PATH + 'olist_orders_dataset.csv')
sellers     = pd.read_csv(DATA_PATH + 'olist_sellers_dataset.csv')

print(customers.shape, geolocation.shape, order_items.shape, orders.shape, sellers.shape)
```

### Step 5: Run the notebook
Go to **Runtime → Run all**.

If you see `FileNotFoundError`, check that the file names match exactly and that the path is correct.

---

## Acknowledgements

Dataset provided by [Olist](https://olist.com/) and published on Kaggle.
