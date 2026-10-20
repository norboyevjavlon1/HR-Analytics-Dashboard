# HR-Analytics-Dashboard


An HR analytics project built on a synthetic dataset of 10,000 employees. It contains two deliverables: a standalone interactive HTML dashboard generated with Python and Chart.js, and a four-page Power BI report built from the same data.

## Overview

The dashboard covers four areas of workforce analysis:

| Page | Focus | Key metrics |
|---|---|---|
| **Overview** | Headcount and employment status | Total employees, active employees, departments, job positions, average tenure |
| **Compensation** | Pay and payroll | Total gross payroll, average and median gross salary, average bonus, pay by department, education, gender, and country |
| **Performance** | Ratings and bonuses | Average rating, high performer share, average bonus, bonus as a share of basic salary |
| **Demographics & Retention** | Age, tenure, and retention | Average age, female share, inactive share, largest department |

Each page has four KPI cards and six charts.

## Repository Structure

```
hr-analytics-dashboard/
├── data/                  # Source CSV files (not tracked by Git)
├── python/
│   ├── build.py           # Builds the HTML dashboard from the CSV files
│   └── template.html      # HTML/CSS/JS template with Chart.js
├── powerbi/
│   ├── hr_dashboard.pbix  # Power BI report
│   └── dax_measures.md    # DAX measures and calculated columns
├── output/
│   └── hr_dashboard.html  # Generated dashboard (open in a browser)
├── .gitignore
└── README.md
```

## Data

The project uses four CSV files, placed in the `data/` folder:

| File | Contents |
|---|---|
| `emp_info.csv` | Employee personal and employment details (ID, date of birth, gender, country, city, qualification, marital status, hire date, active flag, years of experience) |
| `emp_salary.csv` | Salary components, performance rating, and bonus per employee |
| `department.csv` | Department ID and name |
| `job_roles.csv` | Role ID and position title |



## Power BI Report

1. Open `powerbi/hr_dashboard.pbix` in Power BI Desktop.
2. If you are starting from the raw CSV files, follow the steps in `powerbi/dax_measures.md`:
   - Load the four tables and set the data types. Dates use the `dd-mm-yyyy` format.
   - Create the relationships on `emp_id`, `dept_id`, and `role_id`.
   - Add the calculated columns and measures listed in the file.
   - Create the Calendar table and mark it as a date table.
3. Use the slicers (Department, Gender, Country) to filter across pages. Sync them under **View → Sync slicers**.

## Key Definitions

- **Average Tenure:** years between the hire date and 2026-10-20 for all employees, active and inactive.
- **Inactive Share:** the share of employees with `is_active = False`. It is used as a proxy for turnover because the data does not include termination dates.
- **High Performer:** an employee with a performance rating of 4.5 or above.
- **Bonus % of Basic Salary:** total performance bonus divided by total basic salary.
- **Gender Pay Gap:** the difference between male and female average gross salary, divided by the male average.

## Assumptions and Limitations

- The reference date for age and tenure calculations is fixed at **2026-10-20**.
- Salary values have no currency specified in the source data, so they are shown without a currency symbol.
- Tenure for inactive employees is measured up to the reference date, since no termination date is available.
- The dashboard is static. Filters exist only in the Power BI version

  <img width="1335" height="749" alt="image" src="https://github.com/user-attachments/assets/680f1ab4-fbb7-4892-af88-c3cede6c32d4" />
  <img width="1330" height="744" alt="image" src="https://github.com/user-attachments/assets/8bbe78b5-bbca-4190-a18c-7f6766355ad3" />
<img width="1338" height="747" alt="image" src="https://github.com/user-attachments/assets/adfc1e30-9865-43ed-a786-f4792bc02497" />
<img width="1336" height="747" alt="image" src="https://github.com/user-attachments/assets/d5fe1dc1-908a-4700-baf0-f3df69a6e040" />

