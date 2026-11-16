# 07MIAR – Proyecto de programación: Deep Vision in classification tasks

## Clasificación de tumores cerebrales en resonancias magnéticas: CNN desde cero vs. redes preentrenadas

Proyecto de la asignatura **07MIAR – Redes Neuronales y Deep Learning** (Máster en Inteligencia Artificial).

**Autores:** Jorge Ramilo Plata, Ricardo Germes Serrano y Sebastián Alfredo Panesso Laverde.

## Descripción

Clasificamos imágenes de resonancia magnética (MRI) del cerebro en cuatro clases: **glioma**, **meningioma**, **tumor de hipófisis** y **sin tumor**. Comparamos dos estrategias:

1. **CNN diseñada y entrenada desde cero**, con seis experimentos (E1–E6) que van añadiendo profundidad, Batch Normalization, Dropout, regularización L2, data augmentation, EarlyStopping y ajuste del learning rate.
2. **Redes preentrenadas en ImageNet** (VGG16 y MobileNetV2), con transfer learning (base congelada, con y sin augmentation) y fine-tuning (parcial y progresivo).

**Dataset:** [Brain Tumor MRI Dataset](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset) (Kaggle). Unas 7.000 imágenes redimensionadas a 160×160. Antes de dividir los datos quitamos las imágenes duplicadas para que el test no tuviera copias del entrenamiento.

## Resultados en test

| Modelo | test_acc | F1 macro | Tumores no detectados | Parámetros |
|---|---|---|---|---|
| CNN desde cero (E6) | 0.9435 | 0.9423 | 10 de 781 | 3,9 M |
| VGG16 + fine-tuning (P4) | 0.9403 | 0.9381 | 9 de 781 | 14,8 M |
| MobileNetV2 + fine-tuning (P4) | 0.9012 | 0.9005 | 7 de 781 | 2,6 M |

La CNN desde cero y VGG16 con fine-tuning quedan prácticamente empatadas. MobileNetV2 es la más liviana y rápida, pero obtiene unos 4 puntos menos. En el notebook está el análisis completo: curvas de entrenamiento, matrices de confusión, errores de cada modelo y Grad-CAM.

## Contenido del repositorio

| Archivo | Descripción |
|---|---|
| `07MIAR_Proyecto_Programacion_Panesso_Plata_Germes.ipynb` | Notebook ejecutado en Google Colab (GPU), con todas las salidas y gráficas. |
| `07MIAR_Proyecto_Programacion_Panesso_Plata_Germes.pdf` | El mismo notebook exportado a PDF (88 páginas). |

## Cómo ejecutarlo

1. Abrir el notebook en [Google Colab](https://colab.research.google.com/) con un entorno de GPU.
2. Tener un token de la API de Kaggle (`KAGGLE_API_TOKEN`), ya sea como secreto de Colab o escrito cuando el notebook lo pida.
3. Ejecutar todas las celdas en orden. Los modelos se guardan en `MyDrive/07MIAR_Proyecto_Programacion/`.

Librerías principales: TensorFlow/Keras, NumPy, pandas, scikit-learn, OpenCV y Matplotlib.

## Uso de inteligencia artificial

Al final del notebook incluimos la declaración de uso de herramientas de IA, como exige la normativa del máster.
