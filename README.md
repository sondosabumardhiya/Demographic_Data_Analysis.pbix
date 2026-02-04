# 📊  Data Analysis
### *A Data Science & Visualization Project*

## 📝 Project Overview
This project is part of a data analysis track designed to extract socio-economic insights from demographic data. Using **Power BI** and **DAX**, I transformed raw data into an interactive dashboard to answer critical questions about global income, education, and labor patterns.

## 🔍 Educational Assignment Questions & Solutions
Below are the specific questions addressed in this analysis, along with the results derived from the dashboard:

1. **Race Representation**: How many people of each race are represented?
   * **White**: 27,816
   * **Black**: 3,124
   * **Asian-Pac-Islander**: 1,039
   * **Amer-Indian-Eskimo**: 311
   * **Other**: 271

2. **Men's Demographics**: What is the average age of men?
   * **Result**: **39.4 years**.

3. **Education Levels**: What is the percentage of people who have a Bachelor's degree?
   * **Result**: **16.4%**.

4. **Advanced Education & Income**: What percentage of people with Bachelors, Masters, or Doctorate make >50K?
   * **Result**: **46.54%**.

5. **Lower Education & Income**: What percentage of people without advanced education make >50K?
   * **Result**: **17.37%**.

6. **Work Hours Insight**: What is the minimum number of hours a person works per week?
   * **Result**: **1 hour**.

7. **Minimum Hours & Salary**: What percentage of people working the minimum hours earn >50K?
   * **Result**: **10.0%**.

8. **Top Earning Country**: Which country has the highest percentage of people earning >50K?
   * **Result**: **Iran** with **41.86%**.

9. **India's Job Market**: Identify the most popular occupation for high earners (>50K) in India.
   * **Result**: **Prof-specialty**.

## 🧮 Key DAX Measures
To achieve these results, I developed several custom measures:

* **Higher Education Rich %**:
    ```dax
    Higher Education Rich % = 
    DIVIDE(
        CALCULATE(COUNT('adult data'[salary]), 'adult data'[salary] = ">50K", 'adult data'[Education Level] = "Bachelors, Masters, or Doctorate"),
        CALCULATE(COUNT('adult data'[salary]), 'adult data'[Education Level] = "Bachelors, Masters, or Doctorate")
    )
    ```
* **Country Rich %**:
    ```dax
    Country Rich % = 
    DIVIDE(
        CALCULATE(COUNT('adult data'[salary]), 'adult data'[salary] = ">50K"),
        CALCULATE(COUNT('adult data'[salary]), ALL('adult data'[salary]))
    )
    ```
* **Min Hours Rich %**:
    ```dax
    Min Hours Rich % = 
    VAR MinHours = MIN('adult data'[hours-per-week])
    RETURN
    DIVIDE(
        CALCULATE(COUNT('adult data'[salary]), 'adult data'[salary] = ">50K", 'adult data'[hours-per-week] = MinHours),
        CALCULATE(COUNT('adult data'[salary]), 'adult data'[hours-per-week] = MinHours)
    )
    ```

## 🛠️ Skills & Tools
* **Power BI**: Full dashboard design and data modeling.
* **DAX**: Created custom measures for precise percentage calculations.
* **Data Cleaning**: Handled demographic variables and salary filtering.

## 🔒 Data Privacy & Credits
This project is for **educational purposes**. To respect data ownership, the raw dataset is not hosted here. All analytical logic and visualizations are my original work. Original data source: UCI Machine Learning Repository.
