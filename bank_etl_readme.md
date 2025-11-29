# 🏦 Largest Banks ETL Pipeline

A Python-based ETL (Extract, Transform, Load) pipeline that scrapes data about the world's largest banks from Wikipedia, transforms the market capitalization values into multiple currencies, and stores the results in both CSV and SQLite database formats.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Data Source](#data-source)
- [Output](#output)
- [SQL Queries](#sql-queries)
- [Logging](#logging)
- [Contributing](#contributing)
- [License](#license)

## 🎯 Overview

This project implements an automated ETL pipeline that:
1. **Extracts** bank data from a Wikipedia archive page
2. **Transforms** market capitalization from USD to GBP, EUR, and INR
3. **Loads** the processed data into CSV and SQLite database
4. **Logs** each step of the process with timestamps

## ✨ Features

- Web scraping using BeautifulSoup
- Multi-currency conversion (USD → GBP, EUR, INR)
- Data storage in multiple formats (CSV + SQLite)
- Automated logging with timestamps
- SQL query execution capabilities
- Error-resistant data processing

## 📁 Project Structure

```
largest-banks-etl/
│
├── banks_project.py          # Main ETL script
├── exchange_rate.csv          # Currency exchange rates input file
├── Largest_banks_data.csv     # Output CSV file (generated)
├── Banks.db                   # SQLite database (generated)
├── code_log.txt              # Execution log (generated)
├── requirements.txt           # Python dependencies
├── README.md                  # Project documentation
├── .gitignore                # Git ignore file
└── LICENSE                    # License file
```

## 🔧 Prerequisites

- Python 3.7 or higher
- pip (Python package installer)
- Internet connection (for web scraping)

## 📥 Installation

### Step 1: Clone the Repository

```bash
git clone https://github.com/yourusername/largest-banks-etl.git
cd largest-banks-etl
```

### Step 2: Create Virtual Environment (Recommended)

```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Prepare Exchange Rate File

Create an `exchange_rate.csv` file in the project root directory with the following structure:

```csv
Currency,Rate
GBP,0.8
EUR,0.93
INR,82.95
```

**Note:** Update the rates according to current exchange rates if needed.

## 🚀 Usage

### Running the ETL Pipeline

Simply execute the main script:

```bash
python banks_project.py
```

### What Happens:

1. Loads exchange rates from `exchange_rate.csv`
2. Scrapes bank data from Wikipedia archive
3. Transforms market cap values to multiple currencies
4. Saves data to `Largest_banks_data.csv`
5. Loads data into SQLite database `Banks.db`
6. Executes sample queries
7. Logs all steps to `code_log.txt`

## 🌐 Data Source

The pipeline extracts data from:
```
https://web.archive.org/web/20230908091635/https://en.wikipedia.org/wiki/List_of_largest_banks
```

This is an archived snapshot ensuring data consistency and reliability.

## 📊 Output

### CSV Output (`Largest_banks_data.csv`)

| Name | MC_USD_Billion | MC_GBP_Billion | MC_EUR_Billion | MC_INR_Billion |
|------|----------------|----------------|----------------|----------------|
| JPMorgan Chase | 432.92 | 346.34 | 402.62 | 35910.71 |
| ... | ... | ... | ... | ... |

### SQLite Database (`Banks.db`)

Table: `Largest_banks`
- Contains the same columns as CSV
- Supports SQL queries for data analysis

## 🔍 SQL Queries

The pipeline executes three sample queries:

1. **All Records:**
   ```sql
   SELECT * FROM Largest_banks
   ```

2. **Average Market Cap in GBP:**
   ```sql
   SELECT AVG(MC_GBP_Billion) FROM Largest_banks
   ```

3. **Top 5 Banks:**
   ```sql
   SELECT Name FROM Largest_banks LIMIT 5
   ```

### Running Custom Queries

You can modify the script or use any SQLite client to query the database:

```bash
sqlite3 Banks.db
sqlite> SELECT * FROM Largest_banks WHERE MC_USD_Billion > 300;
```

## 📝 Logging

All operations are logged to `code_log.txt` with timestamps:

```
2024-Nov-28-14:30:15 : Preliminaries complete. Initiating ETL process
2024-Nov-28-14:30:16 : Exchange rates loaded
2024-Nov-28-14:30:18 : Data extraction complete. Initiating Transformation process
...
```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

Your Name - [@yourhandle](https://github.com/yourusername)

## 🙏 Acknowledgments

- Data sourced from Wikipedia
- Built with Python, BeautifulSoup, and Pandas
- Exchange rates are example values and should be updated for production use

---

**⭐ If you find this project useful, please consider giving it a star!**