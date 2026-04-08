# Order Instance Dataset README

## 1. Overview

This file contains a synthetic order instance for experimental evaluation in an AP-related delivery scenario:

`Expr1_order_instance_for_AP_(11_12)_orderNum_10_stationNum_3_lockerNum_1051_droneNum_20_seed_1.csv`

The dataset records a set of delivery orders. Each row represents one order request, including:

- the origin merchant (`store_id`)
- the destination customer/home (`home_id`)
- the geographic coordinates of both origin and destination

This dataset can be used for research on:

- drone delivery
- parcel locker assignment
- last-mile logistics optimization
- order dispatching
- route planning
- simulation-based evaluation

---

## 2. File Naming Convention

The file name encodes the main experimental settings:

```text
Expr1_order_instance_for_AP_(11_12)_orderNum_10_stationNum_3_lockerNum_1051_droneNum_20_seed_1.csv
```

### Naming Components

| Component | Meaning |
|----------|---------|
| `Expr1` | Experiment ID or experiment group |
| `order_instance_for_AP` | Order instance generated for the AP scenario |
| `(11_12)` | Scenario identifier, region index, or parameter setting label |
| `orderNum_10` | Number of orders = 10 |
| `stationNum_3` | Number of stations = 3 |
| `lockerNum_1051` | Number of lockers = 1051 |
| `droneNum_20` | Number of drones = 20 |
| `seed_1` | Random seed used for instance generation = 1 |

> **Note:** The exact meaning of `AP` and `(11_12)` should be specified according to the corresponding project or experiment setup.

---

## 3. File Format

The file is stored in **CSV** format with the following header:

```csv
order_ID,store_id,home_id,org_lng,org_lat,des_lng,des_lat
```

---

## 4. Column Definitions

| Column Name | Type | Description |
|-------------|------|-------------|
| `order_ID` | integer-like | Unique order identifier |
| `store_id` | integer-like | Identifier of the origin store (merchant) |
| `home_id` | integer-like | Identifier of the destination customer/home |
| `org_lng` | float | Longitude of the order origin |
| `org_lat` | float | Latitude of the order origin |
| `des_lng` | float | Longitude of the order destination |
| `des_lat` | float | Latitude of the order destination |

---

## 5. Example Records

```csv
order_ID,store_id,home_id,org_lng,org_lat,des_lng,des_lat
1,4402,25119,114.04328064244112,22.644065642441127,114.02754198425365,22.62832698425365
2,17629,13590,114.1100671210133,22.5495051210133,114.13188248195249,22.571320481952498
3,12685,10163,114.04703739051003,22.640104390510036,114.0301082481606,22.623175248160603
4,19116,11157,114.11052102654651,22.549959026546517,114.12303142474425,22.56246942474426
5,7613,20445,114.04426046763169,22.645045467631697,114.0659001420401,22.666685142040112
```

---

## 6. Record Semantics

Each row corresponds to one delivery order:

- the order is identified by a unique `order_ID`
- the order originates from a merchant represented by `store_id`
- the delivery destination is a customer/home represented by `home_id`
- `org_lng` and `org_lat` specify the origin coordinates
- `des_lng` and `des_lat` specify the destination coordinates

Therefore, each record can be interpreted as an **origin-destination (OD) demand pair** for delivery planning.

---

## 7. Instance Configuration

According to the file name, this dataset instance contains:

- **Number of orders:** 10
- **Number of stations:** 3
- **Number of lockers:** 1051
- **Number of drones:** 20
- **Random seed:** 1

---

## 8. Notes

### 8.1 Identifier Format

The fields `order_ID`, `store_id`, and `home_id` should be interpreted as identifiers rather than continuous numeric values.

In some CSV readers, these fields may still be loaded as floating-point numbers depending on the original file format or parsing behavior. If needed, users may convert them to integer type after loading the file.

### 8.2 Order ID Assignment

The `order_ID` field has been assigned as a unique ascending identifier for each order record. This makes the dataset easier to process, reference, and validate in downstream experiments and simulations.

### 8.3 Geographic Coordinates

The coordinate fields are represented in decimal degrees.

Before performing:

- distance calculation
- map matching
- shortest path computation
- geographic visualization

please verify that the coordinate reference system is consistent with the tools or map services being used.

### 8.4 Reproducibility

The suffix `seed_1` indicates that this instance was generated using **random seed 1**.  
To reproduce the same dataset, the same generation parameters and random seed should be used.

---

## 9. Recommended Loading Method

### Python Example

```python
import pandas as pd

file_path = "Expr1_order_instance_for_AP_(11_12)_orderNum_10_stationNum_3_lockerNum_1051_droneNum_20_seed_1.csv"
df = pd.read_csv(file_path)

# Convert identifier columns to integers if needed
df["order_ID"] = df["order_ID"].astype(int)
df["store_id"] = df["store_id"].astype(int)
df["home_id"] = df["home_id"].astype(int)

print(df.head())
print("Number of records:", len(df))
```

---

## 10. Potential Applications

This dataset is suitable for research and experiments in:

- drone delivery planning
- last-mile logistics optimization
- parcel locker assignment
- order allocation and dispatching
- multi-resource collaborative delivery
- route planning and simulation

---

## 11. Version Information

| Item | Value |
|------|-------|
| File format | CSV |
| Recommended encoding | UTF-8 |
| Instance seed | 1 |

---

## 12. Citation

If this dataset is used in a research project, thesis, or publication, please cite the corresponding paper, repository, or technical report that describes the data generation process and experimental setting.
