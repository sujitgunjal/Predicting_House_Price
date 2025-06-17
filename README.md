# 🏠 House Price Prediction using Linear Regression

This is a machine learning project I worked on to **predict housing prices in California** using **Linear Regression** and its regularized versions — **Ridge** and **Lasso** Regression.

The project helped me understand the importance of feature scaling, outlier handling, model evaluation, and the impact of regularization on performance.

---

## 📂 Dataset

I used the **California Housing dataset**, which includes various features about housing blocks in California. It contains **no null values** and includes the following numeric columns:

- `MedInc` – Median Income
- `HouseAge` – Age of the houses
- `AveRooms` – Average number of rooms
- `AveBedrms` – Average number of bedrooms
- `Population` – Population of the block
- `AveOccup` – Average occupancy
- `Latitude`, `Longitude` – Geographic coordinates
- `Price` – Target variable (house value)

---

## 📊 Exploratory Data Analysis (EDA)

### ✅ Boxplot Insights

- **Outliers** were detected in several features like `Population`, `AveRooms`, `MedInc`, and `AveOccup`.
- `Population` was the most **skewed**, with values exceeding **35,000** in some rows — suggesting the need for **log transformation or normalization**.
- Other features like `Latitude` and `Longitude` showed no outliers (as expected due to geographical bounds).

### ✅ Correlation Heatmap

I used a correlation heatmap to examine **linear relationships** between features and the target:

- `MedInc` had the **highest positive correlation** with `Price` (~0.69)
- `AveRooms` and `HouseAge` also had weak positive correlations
- `Latitude` and `Longitude` had weak or negative correlations
- Multicollinearity was observed between `AveRooms` and `AveBedrms` (~0.85)

---

## ⚙️ Preprocessing

### ✅ Normalization

To bring all features to the **same scale**, I applied **Standardization** using `StandardScaler()`.

Why?

- Features like `Population` have values in **thousands**, while others like `HouseAge` are in **tens**.
- Normalization improved **model stability and convergence**.
- It’s essential for models like **Linear Regression**, **KNN**, **SVM**, etc.

---

## 🧠 Models Used

### 🔹 Linear Regression

This is my baseline model. It tries to minimize the **Mean Squared Error (MSE)** between predicted and actual values.

---

### 🔹 Ridge Regression

Used **L2 regularization** to prevent overfitting. It slightly improved performance and handled multicollinearity better.

---

### 🔹 Lasso Regression

Used **L1 regularization**, which also helps with **feature selection** by shrinking less useful coefficients to zero. Performance dropped a bit here but gave insights into feature importance.

---

## 📈 Model Performance

| Metric     | Linear Reg | Ridge Reg | Lasso Reg |
|------------|------------|-----------|------------|
| **MAE**    | ~0.52      | ~0.52     | ~0.68       |
| **RMSE**   | ~0.73      | ~0.72     | ~1.14       |
| **MSE**    | 0.5306     | –         | –           |
| **R²**     | 0.5957     | –         | –           |

### 📌 Insights:

- MAE and RMSE are close → Not many large outliers.
- RMSE = ₹73k, so average error is in a **moderate range**.
- R² = 59.6% → My model explains ~60% of the variation in housing prices.
- Ridge outperformed Lasso slightly.
- Lasso had higher error but helped identify **less important features**.

---

## 📉 Residual Analysis

I calculated **residuals** (`y_test - y_pred`) to evaluate model error. Plotted them to check for:

- Non-random patterns (indicating bias)
- Uneven variance (indicating heteroscedasticity)

Residuals were mostly centered around zero with no clear trend — a good sign.

---

## 📚 What I Learned

- Importance of **scaling features** before training
- How **outliers and skewed data** affect model performance
- How **Ridge and Lasso** help deal with multicollinearity and overfitting
- How to evaluate a regression model using **MAE, MSE, RMSE, and R²**

---

## 🚀 Next Steps

- Try **log transformation** on skewed features (like `Population`)
- Explore **Polynomial Regression** or **Tree-based models** for better performance
- Tune hyperparameters using **GridSearchCV**

---

## 🛠️ Tools & Libraries Used

- Python 🐍
- Pandas
- NumPy
- Scikit-learn
- Seaborn & Matplotlib for visualization

---

## 💬 Feedback

If you’ve got ideas for improving this model or want to collaborate, feel free to reach out!

---

