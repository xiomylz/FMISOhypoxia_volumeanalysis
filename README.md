# Máster en Física Médica Universitat de València

## TFM: Monitorización de la hipoxia en tumores de cabeza y cuello tratados con radioterapia

### Autora: Xiomy Lorena Zamudio Cifuentes

---

En este estudio, se llevó a cabo un seguimiento de la hipoxia detectada por FMISO durante la radioterapia en pacientes con cáncer de cabeza y cuello, con el objetivo de desarrollar modelos estadísticamente relevantes para predecir la respuesta al tratamiento, basados en los cambios en la hipoxia detectada por FMISO-PET/CT.

La investigación, que incluyó una cohorte prospectiva de 48 pacientes, utilizó imágenes de FMISO-PET/CT en tres momentos durante el tratamiento (semanas 0, 2 y 5). La hipoxia detectada por FMISO se evaluó midiendo las variaciones en el tamaño y la localización del subvolumen hipóxico dentro del tumor.

Para evaluar los resultados del tratamiento con radioterapia, se consideraron la recurrencia local, la metástasis a distancia, la supervivencia global y la supervivencia sin progresión. El análisis empleado en nuestro estudio es reproducible, mediante el código abierto que se puede descargar del repositorio GitHub.

---

### Requisitos Previos

- Python 3.x
- Bibliotecas necesarias: `numpy`, `pandas`, `scipy`, `matplotlib`, `seaborn`, `lifelines`
- Recomendamos crear un entorno virtual para gestionar las dependencias.

### Instrucciones de Instalación

1. Clona el repositorio:
    ```bash
    git clone https://github.com/usuario/repositorio.git
    ```
2. Navega al directorio del proyecto:
    ```bash
    cd repositorio
    ```
3. Crea un entorno virtual e instálalo:
    ```bash
    python -m venv venv
    source venv/bin/activate  # Para Linux/macOS
    venv\Scripts\activate  # Para Windows
    ```
4. Instala las dependencias necesarias:
    ```bash
    pip install -r requirements.txt
    ```

### Ejemplos de Uso

1. Para calcular los volúmenes de hipoxia:
    ```bash
    python hypoxia_volumen.py
    ```
2. Para realizar el análisis estadístico en términos de tiempo:
    ```bash
    python TestOutputTime.py
    ```
3. Para realizar el análisis estadístico en términos binarios (sí/no):
    ```bash
    python TestOutputEvent.py
    ```

### Contribuciones

Para la determinación automática de estos parámetros a partir de las segmentaciones GTV mediante los dos métodos (1.4 y 10mmHg) se desarrolló un código en Python, `hypoxia_volumen.py`, que sigue los pasos:

I. Cálculo del volumen (ml) para los contornos de hipoxia en las semanas S0, S2 y S5 de cada paciente.

II. Obtención de los parámetros ∆V, DSC, Sens, PPV y PC.

Para el análisis estadístico se desarrollaron dos códigos en Python: `TestOutputTime.py` y `TestOutputEvent.py`. El análisis se divide en dos partes principales:

**Parte I:** Evaluación de la correlación entre los parámetros extraídos de la imagen y la respuesta al tratamiento en términos de tiempo.

- Se aplica la prueba estadística de Pearson para evaluar la correlación entre los parámetros (DSC, Sens, PPV y PC) derivados de las imágenes FMISO-PET/TC y la respuesta al tratamiento.
- Para las variables con correlación significativa (|r|>0.7, p < 0.05), se estimaron las curvas de Kaplan-Meier, utilizadas para representar la tasa de eventos a lo largo del tiempo.
- La prueba de Log-Rank se empleó para determinar si las diferencias entre las curvas de Kaplan-Meier de los dos grupos, clasificados por la mediana del parámetro de imagen, eran significativas.

**Parte II:** Evaluación de la correlación entre los parámetros extraídos de la imagen y la respuesta al tratamiento en sentido binario (sí / no).

- Se utilizó la prueba U de Mann-Whitney para la comparación no pareada de grupos, útil cuando los datos no siguen una distribución normal.
- Para variables con diferencias significativas, se representaron mediante diagramas de cajas (box-plot), mostrando diferencias en la dispersión y posición central de los datos.

### Contacto

Para más información, puedes contactar a Xiomy Lorena Zamudio a través de:

- xiomyza@alumni.uv.es
- xiomylzamudio@gmail.com
