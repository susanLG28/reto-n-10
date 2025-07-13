# reto 10
### 1. Desarrolle un programa que permita realizar la suma/resta de matrices. El programa debe validar las condiciones necesarias para ejecutar la operación

```python
def leer_matriz(filas, columnas, nombre="matriz"):
    print(f"Ingrese los valores de la {nombre}:")
    matriz = []
    for i in range(filas):
        fila = []
        for j in range(columnas):
            valor = int(input(f"Elemento [{i+1}][{j+1}]: "))
            fila.append(valor)
        matriz.append(fila)
    return matriz

def suma_matrices(matriz1, matriz2):
    filas = len(matriz1)
    columnas = len(matriz1[0])
    resultado = []
    for i in range(filas):
        fila = []
        for j in range(columnas):
            fila.append(matriz1[i][j] + matriz2[i][j])
        resultado.append(fila)
    return resultado

def resta_matrices(matriz1, matriz2):
    filas = len(matriz1)
    columnas = len(matriz1[0])
    resultado = []
    for i in range(filas):
        fila = []
        for j in range(columnas):
            fila.append(matriz1[i][j] - matriz2[i][j])
        resultado.append(fila)
    return resultado

# Lectura de dimensiones
filas = int(input("Ingrese el número de filas de las matrices: "))
columnas = int(input("Ingrese el número de columnas de las matrices: "))

# Lectura de matrices
matriz_a = leer_matriz(filas, columnas, "primera matriz")
matriz_b = leer_matriz(filas, columnas, "segunda matriz")

# Validación de dimensiones
if len(matriz_a) == len(matriz_b) and len(matriz_a[0]) == len(matriz_b[0]):
    print("Suma de matrices:")
    suma = suma_matrices(matriz_a, matriz_b)
    for fila in suma:
        print(fila)
    print("Resta de matrices:")
    resta = resta_matrices(matriz_a, matriz_b)
    for fila in resta:
        print(fila)
else:
    print("Error: Las matrices deben tener las mismas dimensiones para sumar o restar.")
```

### 2. Desarrolle un programa que permita realizar el producto de matrices . El programa debe validar las condiciones necesarias para ejecutar la operación

```python
def leer_matriz(filas, columnas, nombre="matriz"):
    print(f"Ingrese los valores de la {nombre}:")
    matriz = []
    for i in range(filas):
        fila = []
        for j in range(columnas):
            valor = int(input(f"Elemento [{i+1}][{j+1}]: "))
            fila.append(valor)
        matriz.append(fila)
    return matriz

def producto_matrices(matriz1, matriz2):
    filas_a = len(matriz1)
    columnas_a = len(matriz1[0])
    filas_b = len(matriz2)
    columnas_b = len(matriz2[0])
    if columnas_a != filas_b:
        print("Error: El número de columnas de la primera matriz debe ser igual al número de filas de la segunda matriz.")
        return None
    resultado = []
    for i in range(filas_a):
        fila_resultado = []
        for j in range(columnas_b):
            suma = 0
            for k in range(columnas_a):
                suma += matriz1[i][k] * matriz2[k][j]
            fila_resultado.append(suma)
        resultado.append(fila_resultado)
    return resultado

# Lectura de dimensiones para la primera matriz
filas_a = int(input("Ingrese el número de filas de la primera matriz: "))
columnas_a = int(input("Ingrese el número de columnas de la primera matriz: "))
matriz_a = leer_matriz(filas_a, columnas_a, "primera matriz")

# Lectura de dimensiones para la segunda matriz
filas_b = int(input("Ingrese el número de filas de la segunda matriz: "))
columnas_b = int(input("Ingrese el número de columnas de la segunda matriz: "))
matriz_b = leer_matriz(filas_b, columnas_b, "segunda matriz")

# Producto de matrices
resultado = producto_matrices(matriz_a, matriz_b)
if resultado:
    print("El producto de las matrices es:")
    for fila in resultado:
        print(fila)
```

### 3. Desarrolle un programa que permita obtener la matriz transpuesta de una matriz ingresada. El programa debe validar las condiciones necesarias para ejecutar la operación
```python
def leer_matriz(filas, columnas):
    print("Ingrese los valores de la matriz:")
    matriz = []
    for i in range(filas):
        fila = []
        for j in range(columnas):
            valor = int(input(f"Elemento [{i+1}][{j+1}]: "))
            fila.append(valor)
        matriz.append(fila)
    return matriz

def transponer_matriz(matriz):
    # Validar que la matriz no esté vacía y tenga filas y columnas
    if not matriz or not matriz[0]:
        print("Error: La matriz debe tener al menos una fila y una columna.")
        return None
    filas = len(matriz)
    columnas = len(matriz[0])
    transpuesta = []
    for j in range(columnas):
        fila_transpuesta = []
        for i in range(filas):
            fila_transpuesta.append(matriz[i][j])
        transpuesta.append(fila_transpuesta)
    return transpuesta

# Lectura de dimensiones
filas = int(input("Ingrese el número de filas de la matriz: "))
columnas = int(input("Ingrese el número de columnas de la matriz: "))

# Validación de dimensiones
if filas < 1 or columnas < 1:
    print("Error: La matriz debe tener al menos una fila y una columna.")
else:
    matriz = leer_matriz(filas, columnas)
    resultado = transponer_matriz(matriz)
    if resultado:
        print("La matriz transpuesta es:")
        for fila in resultado:
            print(fila)

```

### 4. Desarrollar un programa que sume los elementos de una columna dada de una matriz

```python
def leer_matriz(filas, columnas):
    print("Ingrese los valores de la matriz:")
    matriz = []
    for i in range(filas):
        fila = []
        for j in range(columnas):
            valor = int(input(f"Elemento [{i+1}][{j+1}]: "))
            fila.append(valor)
        matriz.append(fila)
    return matriz

def sumar_columna(matriz, columna):
    if not matriz or columna < 0 or columna >= len(matriz[0]):
        print("Error: La columna indicada no existe en la matriz.")
        return None
    suma = 0
    for fila in matriz:
        suma += fila[columna]
    return suma

# Lectura de dimensiones
filas = int(input("Ingrese el número de filas de la matriz: "))
columnas = int(input("Ingrese el número de columnas de la matriz: "))

# Validación de dimensiones
if filas < 1 or columnas < 1:
    print("Error: La matriz debe tener al menos una fila y una columna.")
else:
    matriz = leer_matriz(filas, columnas)
    col = int(input(f"Ingrese el número de columna a sumar (1 a {columnas}): ")) - 1
    resultado = sumar_columna(matriz, col)
    if resultado is not None:
        print(f"La suma de los elementos de la columna {col+1} es: {resultado}")

```

### 5. Desarrollar un programa que sume los elementos de una fila dada de una matriz

```python
def leer_matriz(filas, columnas):
    print("Ingrese los valores de la matriz:")
    matriz = []
    for i in range(filas):
        fila = []
        for j in range(columnas):
            valor = int(input(f"Elemento [{i+1}][{j+1}]: "))
            fila.append(valor)
        matriz.append(fila)
    return matriz

def sumar_fila(matriz, fila):
    if not matriz or fila < 0 or fila >= len(matriz):
        print("Error: La fila indicada no existe en la matriz.")
        return None
    suma = 0
    for valor in matriz[fila]:
        suma += valor
    return suma

# Lectura de dimensiones
filas = int(input("Ingrese el número de filas de la matriz: "))
columnas = int(input("Ingrese el número de columnas de la matriz: "))

# Validación de dimensiones
if filas < 1 or columnas < 1:
    print("Error: La matriz debe tener al menos una fila y una columna.")
else:
    matriz = leer_matriz(filas, columnas)
    fila_elegida = int(input(f"Ingrese el número de fila a sumar (1 a {filas}): ")) - 1
    resultado = sumar_fila(matriz, fila_elegida)
    if resultado is not None:
        print(f"La suma de los elementos de la fila {fila_elegida+1} es: {resultado}")

```
