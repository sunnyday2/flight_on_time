# FlightOnTime – MVP Predicción de Retrasos de Vuelos

# Descripción del proyecto
FlightOnTime es un **MVP de Machine Learning** que predice si un vuelo será **Puntual** o **Retrasado**, utilizando información del vuelo y variables meteorológicas.

El objetivo es demostrar un flujo completo de **Data Science aplicado**, desde datos históricos hasta un modelo listo para ser integrado en una API.

---

## Problema de negocio
Los retrasos en vuelos generan:
- insatisfacción en pasajeros
- costos operativos para aerolíneas
- problemas de planificación en aeropuertos

Este proyecto busca **anticipar retrasos** para permitir una mejor toma de decisiones.

---

## Dataset
El dataset utilizado contiene información histórica de vuelos, incluyendo:

### Variables principales
- **hour**: hora de salida del vuelo
- **distance**: distancia del vuelo (km)
- **marketing_airline_network**: aerolínea
- **temp_mean**: temperatura media
- **precipitation**: precipitación
- **wind_speed**: velocidad del viento

### Variable objetivo
- **target**
  - `0` → Puntual  
  - `1` → Retrasado  

El dataset se encuentra en:
```
data/dataset_vuelos_clima_final.csv
```

Incluye **features meteorológicas** integradas desde una API externa de clima.

---

## Proceso de Data Science

### Exploración y limpieza
- Revisión de valores nulos
- Selección de variables relevantes
- Separación de variables numéricas y categóricas

### Feature Engineering
- Extracción de hora desde la fecha
- Codificación de variables categóricas (One-Hot Encoding)
- Escalado de variables numéricas

### Modelos entrenados
Se entrenaron y compararon dos modelos:

### Logistic Regression (modelo final)
- Modelo simple y explicable
- Buen equilibrio entre métricas
- Fácil de integrar en un backend

### Random Forest (modelo comparativo)
- Usado como benchmark
- Se realizó una versión ajustada para reducir overfitting

---

## Resultados principales

### Logistic Regression
- Accuracy ≈ **0.68 – 0.81** (según umbral)
- Buen control del trade-off entre precision y recall
- Modelo elegido para el MVP

### Random Forest
- Accuracy ≈ **0.81**
- Mejor ROC AUC
- Menor interpretabilidad

> Aunque Random Forest tiene métricas competitivas, se priorizó **explicabilidad y simplicidad** para el MVP.

---

## Ajustes realizados
- Se analizó el impacto de **modificar el umbral de decisión** para aumentar la precision
- Se ajustaron hiperparámetros del Random Forest para análisis
- **Solo el modelo base se exporta**, los ajustes quedan como análisis

---

## Modelo exportado
El modelo final entrenado se guarda como:

```
model/MVP_entrenamiento.pkl
```

Incluye:
- preprocesamiento
- modelo entrenado
- listo para ser cargado por un backend

---

## Ejemplo de entrada (JSON)

```json
{
  "aerolinea": "AZ",
  "origen": "GIG",
  "destino": "GRU",
  "fecha_partida": "2025-11-10T14:30:00",
  "distancia_km": 350
}
```

### Ejemplo de salida esperada
```json
{
  "prevision": "Puntual",
  "probabilidad": 0.24
}
```

---

## Tecnologías utilizadas
- Python
- Pandas
- scikit-learn
- Jupyter Notebook
- joblib

---

## Estado del proyecto
✔ MVP funcional  
✔ Modelo entrenado y evaluado  
✔ Listo para integración vía API REST  

---

## Trabajo futuro
- Integración completa con API REST (Spring Boot)
- Ajuste dinámico del umbral según negocio
- Dashboard visual de predicciones
- Persistencia de predicciones

---

## Equipo
Proyecto desarrollado como parte de un **hackathon ONE** de Data Science y Back-End.
👥 Equipo

Ciencia de Datos
* Ezequiel Samuel Prilusky
* Javier Menéndez
* Ganna Kharkovska
* Rafael Osuna
* Alexander Tovar Morcillo

Colaboracion del equipo de Back-End

Como MVP para hackathon académico.

