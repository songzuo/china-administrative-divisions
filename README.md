# China Administrative Divisions (中国行政区划)

> Complete dataset of China's administrative divisions with **665,163 regions** across **5 administrative levels**.

[![Live Explorer](https://7zi.com/china/)](https://7zi.com/china/)

## 📊 Dataset Overview

| Level | Name | Count | Description |
|-------|------|-------|-------------|
| 1 | Province (省) | 35 | Provincial-level divisions (provinces, municipalities, autonomous regions, SARs) |
| 2 | City (市) | 475 | Prefecture-level and district-level cities |
| 3 | County (县) | 2,728 | Counties, districts, county-level cities |
| 4 | Town (镇) | 41,352 | Towns, townships, sub-districts |
| 5 | Village (村) | 620,573 | Villages, neighborhoods, communities |
| | **Total** | **665,163** | |

## 📂 Data Files

| File | Format | Size | Description |
|------|--------|------|-------------|
| `china_administrative_divisions.csv` | CSV (UTF-8 with BOM) | ~63 MB | Complete dataset, Excel-compatible |
| `province.json` | JSON | ~5 KB | Provincial-level data |
| `city.json` | JSON | ~100 KB | City-level data |
| `county.json` | JSON | ~700 KB | County-level data |
| `town.json` | JSON | ~11 MB | Town-level data |

## 🗂️ Data Fields

| Field | Type | Description |
|-------|------|-------------|
| `adcode` | string | Administrative division code (e.g., `110000` for Beijing) |
| `name` | string | Chinese name (e.g., `北京市`) |
| `name_en` | string | English name (e.g., `Beijing`) |
| `level` | string | Level: `province` / `city` / `county` / `town` / `village` |
| `parent_adcode` | string | Parent division's adcode |
| `children_num` | integer | Number of direct child divisions |
| `slug` | string | URL-friendly slug |
| `is_urban` | integer | 1 = urban area (city districts), 0 = rural |
| `province` | string | Province name (for non-province levels) |
| `city` | string | City name (for county and below) |
| `county` | string | County name (for town and below) |

## 📖 Usage Examples

### Python
```python
import csv

with open('china_administrative_divisions.csv', encoding='utf-8-sig') as f:
    reader = csv.DictReader(f)
    for row in reader:
        print(f"{row['adcode']} - {row['name']} ({row['name_en']}) [{row['level']}]")
```

### JavaScript
```javascript
const data = require('./province.json');
data.forEach(p => console.log(`${p.adcode}: ${p.name} (${p.name_en})`));
```

### Quick Stats with SQLite
```bash
# Import CSV into SQLite for fast queries
sqlite3 china.db
.mode csv
.import china_administrative_divisions.csv admin_divisions

# Example queries
SELECT level, COUNT(*) FROM admin_divisions GROUP BY level;
SELECT * FROM admin_divisions WHERE parent_adcode = '110000';
```

## 🔗 Live Data Explorer

Browse all 665,163 administrative divisions with interactive maps and search:

👉 **[7zi.com/china/](https://7zi.com/china/)**

## 📋 Data Source

Based on the National Bureau of Statistics of China administrative division codes. Last updated: 2026.

## 📄 License

This dataset is provided for educational and research purposes. The administrative division data itself is public information.

## ⭐ Star This Repo

If you find this dataset useful, please consider giving it a star!