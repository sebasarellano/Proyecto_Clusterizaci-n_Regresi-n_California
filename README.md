# Segmentación de distritos de California y regresión del valor de vivienda

Proyecto académico de **Estadística 4** que combina análisis exploratorio, preparación de datos, segmentación con K-means y regresión lineal multivariante para estudiar perfiles de distritos de California a partir de datos históricos de vivienda.

> **Importante:** el conjunto de datos corresponde a información censal histórica de 1990. Este proyecto tiene fines académicos; no describe el mercado inmobiliario actual ni constituye asesoría de inversión.

## Objetivos

- Explorar la distribución de las variables y revisar posibles valores atípicos.
- Crear indicadores relativos al tamaño del distrito: habitaciones por hogar, personas por hogar y dormitorios por habitación.
- Limitar los extremos de esos indicadores mediante winsorización y estandarizar las variables usadas por K-means.
- Comparar distintas cantidades de clústeres con el método del codo y el coeficiente de silueta.
- Interpretar los perfiles encontrados y comparar modelos de regresión del valor mediano de vivienda, con y sin variables indicadoras de clúster.
- Revisar diagnósticos del modelo y reconocer las limitaciones de los resultados.

## Datos y metodología

El notebook utiliza `california_housing_train.csv`, disponible en el entorno de ejemplo de Google Colab, y selecciona una muestra reproducible de **5.000 distritos** con la semilla **5759**.

Para K-means se utilizan siete variables estandarizadas: longitud, latitud, edad mediana de las viviendas, ingreso mediano y tres indicadores por hogar winsorizados entre los percentiles 1 y 99. El valor mediano de vivienda se mantiene fuera de la clusterización y se utiliza después para describir los grupos y como variable objetivo en la regresión.

Se seleccionan **tres clústeres** por el equilibrio entre el método del codo y la interpretabilidad de los perfiles. La silueta promedio es aproximadamente **0,261**, lo que indica una separación débil y cierto solapamiento entre grupos. Por ello, los clústeres deben entenderse como perfiles descriptivos, no como categorías naturales perfectamente separadas.

## Resultados destacados

- **Grupo 0:** 1.947 distritos (38,9 %); perfil de ingreso medio-bajo y hogares más densos; valor medio de vivienda aproximado de **USD 179.506**.
- **Grupo 1:** 1.800 distritos (36,0 %); perfil de ingreso medio; valor medio de vivienda aproximado de **USD 186.068**.
- **Grupo 2:** 1.253 distritos (25,1 %); perfil de ingresos más altos y viviendas más amplias.

En la regresión, el ingreso mediano presenta una asociación positiva con el valor de vivienda. Añadir indicadores de clúster mejora el R² ajustado solo ligeramente (de aproximadamente **0,6018 a 0,6042**). Estos resultados describen asociaciones condicionadas por las variables incluidas; **no demuestran causalidad, infravaloración ni rentabilidad de inversión**.

## Herramientas

- Python
- pandas y NumPy
- Matplotlib
- scikit-learn
- statsmodels
- Google Colab / Jupyter Notebook

## Cómo ejecutar

1. Abre el notebook en Google Colab o en un entorno Jupyter.
2. Asegúrate de tener disponible el archivo `california_housing_train.csv` en `/content/sample_data/`, como se espera en Google Colab.
3. Ejecuta las celdas en orden.

Si ejecutas el proyecto fuera de Google Colab, modifica la ruta de lectura del CSV para que coincida con la ubicación local del archivo.

## Limitaciones

- Los datos son históricos y no representan precios ni condiciones actuales.
- La muestra de 5.000 distritos se selecciona aleatoriamente con una semilla fija.
- La silueta baja advierte que los clústeres se solapan.
- La regresión identifica asociaciones estadísticas y no relaciones causales.
- Los valores censurados o topados presentes en el archivo pueden limitar la interpretación de algunos extremos.
- La segmentación no debe utilizarse por sí sola para tomar decisiones de inversión.

## Uso de inteligencia artificial

Como se explica en el notebook, se utilizó IA como apoyo para generar código de análisis descriptivo, winsorización, estandarización, clusterización y regresión. Las interpretaciones y justificaciones se presentan como parte del trabajo académico.

## Autoría

Proyecto académico individual desarrollado como práctica de Estadística 4.
