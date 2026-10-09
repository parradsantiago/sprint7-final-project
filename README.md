# ConnectaTel — Análisis de uso de servicios móviles

Análisis exploratorio del uso real de llamadas y mensajes de los clientes de ConnectaTel en México y Colombia, para identificar patrones de uso, detectar comportamientos atípicos y definir segmentos de clientes que ayuden a optimizar la oferta comercial.

## Objetivo

Responder a las preguntas del negocio:
- ¿Qué segmentos de clientes muestran mayor o menor uso de llamadas y mensajes?
- ¿Qué usuarios presentan valores atípicos (comportamientos inusuales o errores de registro)?
- ¿Cómo varía el uso según la edad y el tipo de plan?
- ¿Qué patrones pueden ayudar a diseñar mejores planes?

## Datasets

| Archivo | Descripción |
|---|---|
| `plans.csv` | Catálogo de planes: precio, minutos, mensajes y GB incluidos, y costo por excedente. |
| `users_latam.csv` | 4,000 clientes: edad, ciudad, fecha de registro, plan y fecha de baja (churn). |
| `usage.csv` | 40,000 eventos de uso (enero–junio 2024): llamadas con duración y mensajes con longitud. |

## Etapas del análisis

1. **Exploración inicial:** estructura, tipos de datos y valores nulos de cada dataset.
2. **Calidad de datos:** detección de sentinels y valores inválidos (`age = -999`, `city = "?"`, fechas de registro en 2026, `duration = 120`, `length = 1490`, datos en la columna equivocada).
3. **Limpieza:** imputación de edad con la mediana, conversión de valores inválidos a nulo, conversión de fechas y verificación de nulos estructurales (MAR) en `duration` y `length`.
4. **Métricas por usuario:** agregación de mensajes, llamadas y minutos por cliente, y unión con la tabla de clientes.
5. **Visualización y outliers:** histogramas por plan, boxplots y límites con el método IQR.
6. **Segmentación:** grupos por nivel de uso (bajo, medio, alto) y por edad (joven, adulto, adulto mayor).
7. **Insight ejecutivo:** conclusiones y recomendaciones comerciales.

## Principales hallazgos

- El uso de llamadas y mensajes **no varía** según la edad ni el tipo de plan.
- Los clientes Premium usan lo mismo que los Básico, aunque pagan más del doble.
- El uso real está muy por debajo de lo incluido en los planes (unos 4 minutos y 1 mensaje al mes por cliente).
- El 73.6% de los clientes tiene uso medio, el 19.5% uso bajo y solo el 7% uso alto.

## Herramientas

Python · pandas · numpy · matplotlib · seaborn · Jupyter Notebook
