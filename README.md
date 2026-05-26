# Restaurante-men--Phyton
# Andrea Yuliany Bayona Perez
# Grupo:213022_783
# Ingenieria de Telecomunicaciones


def calcular_precio_final(categoria_producto, precio_base, categoria_objetivo, umbral_precio):
    # Validar si el producto es de la categoria seleccionada y pasa el precio limite
    if categoria_producto.lower() == categoria_objetivo.lower() and precio_base > umbral_precio:
        descuento = precio_base * 0.15
        return precio_base - descuento
    
    # Si no cumple, el precio se mantiene igual
    return precio_base


def main():
    print("--- PROGRAMA DE GESTION DE PRECIOS ---")
    print("Seleccione la promocion del dia:")
    print("1. Platos Fuertes (Descuento a mayores de $15000)")
    print("2. Bebidas (Descuento a mayores de $10000)")
    print("3. Entradas (Descuento a mayores de $10000)")
    
    opcion = input("\nIngrese el numero de la opcion (1, 2 o 3): ")
    
    # Matriz con los 6 productos de la guia
    menu_restaurante = [
        ["Hamburguesa Gourmet", "Platos Fuertes", 25000],
        ["Limonada Cerezada", "Bebidas", 8500],
        ["Filete de Pollo", "Platos Fuertes", 18000],
        ["Malteada de Chocolate", "Bebidas", 12000],
        ["Tres Leches", "Postres", 9000],
        ["Papas Supremas", "Entradas", 14000]
    ]
    
    # Asignar valores segun lo que elija el usuario
    if opcion == "1":
        categoria_promo = "Platos Fuertes"
        umbral_promo = 15000
    elif opcion == "2":
        categoria_promo = "Bebidas"
        umbral_promo = 10000
    elif opcion == "3":
        categoria_promo = "Entradas"
        umbral_promo = 10000
    else:
        print("Opcion no valida. No se aplican descuentos.")
        categoria_promo = ""
        umbral_promo = 0

    print("\nREPORTE FINAL DE PRECIOS:")
    print("PRODUCTO                 | CATEGORIA       | BASE        | FINAL")
    print("-" * 65)
    
    # Recorrer la matriz con un ciclo for
    for producto in menu_restaurante:
        nombre = producto[0]
        categoria = producto[1]
        precio_base = producto[2]
        
        # Llamar a la funcion para el calculo
        precio_final = calcular_precio_final(categoria, precio_base, categoria_promo, umbral_promo)
        
        # Imprimir los datos en la tabla
        print(f"{nombre:<24} | {categoria:<15} | ${precio_base:<10} | ${precio_final}")

if __name__ == "__main__":
    main()
