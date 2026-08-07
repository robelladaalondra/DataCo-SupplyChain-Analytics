# DataCo Supply Chain Analytics | Análisis de Cadena de Suministro

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.0%2B-orange)
![Pandas](https://img.shields.io/badge/Pandas-1.3%2B-green)
![Plotly](https://img.shields.io/badge/Plotly-Interactive-blueviolet)

> **End-to-End Analytics on DataCo Retail Supply Chain:** A comprehensive data project integrating ETL processes, KPI tracking (sales, margin, logistics), advanced visualizations (interactive maps, treemaps, density plots), and a Logistic Regression model (AUC 0.72) to predict late deliveries. Includes a rigorous Data Ethics & Algorithmic Bias auditing framework.
>
> **Análisis de extremo a extremo de la cadena de suministro de DataCo:** Un proyecto integral de datos que integra procesos ETL, seguimiento de KPIs (ventas, márgenes, logística), visualizaciones avanzadas (mapas interactivos, treemaps, gráficos de densidad) y un modelo de Regresión Logística (AUC 0.72) para predecir entregas tardías. Incluye un riguroso marco de Ética de Datos y auditoría de sesgos algorítmicos.

---

## 📊 Business Overview | Resumen del Negocio

This analysis uses the `DataCoSupplyChainDataset.csv` to provide actionable insights for a U.S.-based retail company. 
*Este análisis utiliza el `DataCoSupplyChainDataset.csv` para proporcionar información procesable a una empresa minorista con sede en EE. UU.*

| Metric | Value | Insight |
| :--- | :--- | :--- |
| **Total Sales** | **$12,770,673.41** | High transaction volume. |
| **Total Orders** | **65,752** | Significant sample size for statistics. |
| **Average Ticket** | **$194.22** | Healthy average purchase value. |
| **Net Margin** | **10.87%** | Positive but tight; optimization required. |
| **On-Time Delivery** | **17.83%** | **CRITICAL:** 82% of orders are delayed! |

---

## 🔧 Methodology & Tech Stack | Metodología y Tecnología

### 1. ETL Pipeline (Python + Pandas)
*   **Data Cleaning:** Column name standardization to `snake_case`, handling null values, and removing duplicates.
*   **Feature Engineering:** Created `delivery_days` (shipping_date - order_date) and extracted `month`/`year` for time-series analysis.

### 2. Exploratory Analysis & KPIs
*   Calculated business-critical metrics using custom Python functions.
*   Visualized data using **Matplotlib**, **Seaborn**, and **Plotly** for interactive maps (chloropleth) and treemaps.

### 3. Machine Learning Model (Scikit-Learn)
*   **Algorithm:** Logistic Regression (Chosen for its high interpretability / "White-box" model).
*   **Target:** `late_delivery_risk` (0 = On Time, 1 = Late).
*   **Preprocessing:** `StandardScaler` for numerical variables, `OneHotEncoder` for categorical features.
*   **Validation:** **Stratified 5-Fold Cross-Validation** to ensure robustness against class imbalance.

---

## 🧠 ML Model Performance & Insights | Rendimiento del Modelo

*   **AUC-ROC:** **0.7275** (Demonstrates solid discriminatory ability to separate late vs. on-time orders).
*   **Cross-Validation Accuracy:** **69.3%** (± 0.54%). The low standard deviation proves the model is robust and not overfitting.

**🔑 Most Critical Feature (Risk Driver):**
The variable **`shipping_mode_Standard Class`** is statistically the strongest predictor of a delivery delay. Negociations with this specific logistics provider are essential.
*La variable **`shipping_mode_Standard Class`** es estadísticamente el predictor más fuerte de un retraso en la entrega. Las negociaciones con este proveedor logístico específico son esenciales.*

---

## 📈 Visualizations | Visualizaciones Clave

*(Ensure you add your actual image files to your repository folder and update these paths accordingly / Asegúrate de añadir tus archivos de imagen a la carpeta de tu repositorio y actualizar estas rutas).*

- **Dashboard Comercial:** Ventas por estado (Mapa Interactivo) y segmento.
- **KPIs Globales:** Margen, ventas totales y desempeño logístico.
- **Violin Plot:** Distribución de márgenes por departamento (Identifica pérdidas puntuales).
- **Density Plot:** Patrones de gasto de los clientes por segmento.
- **Feature Importance:** Coeficientes del modelo de ML (Factores de retraso).
- **ROC Curve & Confusion Matrix:** Evaluación visual del rendimiento predictivo.

---

## 🛡️ Data Ethics & Governance | Ética y Gobernanza de Datos

*   **Privacy (Privacy):** All **PII** (Personal Identifiable Information) such as `Customer Email`, `Customer Fname`, `Customer Lname`, and `Customer Password` were strictly removed to comply with **GDPR and CCPA** regulations.
*   **Algorithmic Fairness (Equidad Algorítmica):** Given the disproportionate sales volume in **Puerto Rico (PR)**, a mandatory geo-bias audit is built into the pipeline. If the model unfairly penalizes this region, the geographic feature will be excluded to prevent discrimination.
*   **Explainability (Explicabilidad):** Logistic Regression was chosen so that if an order is flagged as "High Risk", the system can explain *exactly why* (e.g., "You chose Standard Class shipping"), upholding the customer's **Right to Explanation**.

---

## 🚀 Strategic Recommendations | Recomendaciones Estratégicas

### ⏱️ Short-Term (0 - 3 Months) | Corto Plazo
- **Logistics Renegotiation:** Immediately renegotiate SLAs or switch providers for **Standard Class shipping** to drastically reduce the 82% delay rate.
- **Commercial Campaign:** Launch targeted discounts for the **Corporate** segment, specifically on high-margin departments (**Fitness, Technology**) to increase profitability.

### 📈 Mid-Term (3 - 6 Months) | Mediano Plazo
- **Predictive Alert Integration:** Embed the Logistic Regression model into the ERP/CRM to auto-flag "High Risk" orders at checkout, allowing for proactive upgrades or adjusted delivery promises.

### ⚙️ Long-Term (6 - 12 Months) | Largo Plazo
- **Inventory Optimization:** Reduce warehouse space for low-margin categories (Book Shop, Pet Shop) and increase stock for high-margin ones (Fitness).
- **Quarterly Ethics Audits:** Schedule recurring reviews to monitor the model's feature weights, ensuring no demographic, racial, or geographic biases arise over time.

---

## 🚀 How to Run the Project | Cómo ejecutar el proyecto

1. **Clone the repository** | Clona el repositorio:
   ```bash
   git clone https://github.com/tu-usuario/DataCo-SupplyChain-Analytics.git
   cd DataCo-SupplyChain-Analytics
