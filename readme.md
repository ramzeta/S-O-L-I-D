## 🧠 ¿Qué es SOLID?

SOLID es como el **código de conducta Jedi** de los desarrolladores. Son **5 principios poderosos** que, si los aprendes y los aplicas, te ayudarán a mantener el equilibrio en la galaxia del software.

---

## 🎓 Camino del Padawan a Maestro Jedi

Cada letra de **SOLID** es una lección Jedi. Dominar cada una te acercará al rango de **Maestro Jedi del código limpio**.

---

## ✨ S - **Single Responsibility Principle (SRP)**

> “Una clase debe tener una única responsabilidad… como un Jedi concentrado en una sola misión.”

### 🛡️ Lección Padawan:

Un **droide médico** no debe luchar con sables. Y un **droide de combate** no debe hacer curas. Cada uno tiene su misión.

### 💥 Código del Lado Oscuro:

```java
class Droide {
  void curarHeridos() {}
  void dispararLaser() {}
}
```

### ⚔️ Código del Lado Luminoso:

```java
class DroideMedico {
  void curarHeridos() {}
}

class DroideCombate {
  void dispararLaser() {}
}
```

### 🧠 ¿Cómo saber si estás cayendo al Lado Oscuro?

* Si una clase hace varias cosas que no están relacionadas.
* Si tus métodos parecen venir de planetas distintos.

---

## ✨ O - **Open/Closed Principle (OCP)**

> “El código debe estar abierto a ser mejorado, pero cerrado a ser modificado.”

### 🛡️ Lección Padawan:

Los **sables láser** pueden cambiar de color, pero no necesitas desmontarlos cada vez. Solo les cambias el cristal Kyber.

### 💥 Código del Lado Oscuro:

```java
class Nave {
  void atacar(String tipo) {
    if (tipo.equals("bláster")) { /* dispara */ }
    if (tipo.equals("torpedo")) { /* lanza torpedo */ }
  }
}
```

### ⚔️ Código del Lado Luminoso:

```java
interface Arma {
  void atacar();
}

class Blaster implements Arma {
  public void atacar() { /* disparo */ }
}

class Nave {
  void atacarCon(Arma arma) {
    arma.atacar();
  }
}
```

### 🧠 ¿Cómo detectarlo?

* Si cada vez que quieres añadir algo, tienes que editar muchas líneas antiguas.
* Si sientes que tocas piezas y el Halcón Milenario se rompe.

---

## ✨ L - **Liskov Substitution Principle (LSP)**

> “Si heredas una clase, el comportamiento debe seguir siendo válido.”

### 🛡️ Lección Padawan:

Un Jedi puede ser reemplazado por otro en una misión… pero un Sith no puede hacerse pasar por Jedi. ¡Sería una traición al código!

### 💥 Código del Lado Oscuro:

```java
class Caza {
  void despegar() {}
}

class ATAT extends Caza {
  void despegar() {
    throw new UnsupportedOperationException("No puedo volar");
  }
}
```

### ⚔️ Código del Lado Luminoso:

```java
interface Vehiculo {}

interface VehiculoVolador extends Vehiculo {
  void despegar();
}

class XWing implements VehiculoVolador {
  public void despegar() { /* al espacio */ }
}

class ATAT implements Vehiculo {
  // camina, no despega
}
```

### 🧠 ¿Cómo saber si violas la Fuerza?

* Si tu clase hija rompe el comportamiento esperado.
* Si un Maestro Jedi recibe un Padawan que desobedece el entrenamiento.

---

## ✨ I - **Interface Segregation Principle (ISP)**

> “No hagas que una clase implemente poderes que no necesita.”

### 🛡️ Lección Padawan:

No todos los Jedi tienen que ser pilotos, generales y curanderos a la vez. Que cada uno use solo los poderes que domina.

### 💥 Código del Lado Oscuro:

```java
interface Jedi {
  void usarFuerza();
  void pilotarNave();
  void curarHeridos();
}

class Yoda implements Jedi {
  public void usarFuerza() {}
  public void pilotarNave() {} // no le interesa
  public void curarHeridos() {} // tampoco
}
```

### ⚔️ Código del Lado Luminoso:

```java
interface Fuerza {
  void usarFuerza();
}

interface Piloto {
  void pilotarNave();
}

interface Curandero {
  void curarHeridos();
}

class Yoda implements Fuerza {
  public void usarFuerza() {}
}
```

### 🧠 ¿Cómo detectarlo?

* Si te ves obligado a implementar métodos que no necesitas.
* Si sientes que estás forzando al Padawan a aprender cosas que no son su camino.

---

## ✨ D - **Dependency Inversion Principle (DIP)**

> “Los Jedi deben depender de la Fuerza, no de una fuente concreta.”

### 🛡️ Lección Padawan:

El sable láser puede usar un cristal azul, verde o púrpura… pero el Jedi solo necesita saber que **hay energía**. No debe preocuparse de **dónde** viene.

### 💥 Código del Lado Oscuro:

```java
class SableLaser {
  CristalAzul cristal = new CristalAzul();
  void encender() { cristal.encender(); }
}
```

### ⚔️ Código del Lado Luminoso:

```java
interface Cristal {
  void encender();
}

class CristalVerde implements Cristal {
  public void encender() {}
}

class SableLaser {
  Cristal cristal;
  SableLaser(Cristal cristal) {
    this.cristal = cristal;
  }
  void encender() { cristal.encender(); }
}
```

### 🧠 ¿Cómo detectar el error?

* Si tu clase depende de otra clase concreta en vez de una interfaz.
* Si cambiar una pieza requiere reconstruir todo el droide.

---

## 🧙‍♂️ ¿Cómo saber si ya eres Maestro Jedi del Código?

✅ ¿Tus clases hacen solo una misión? (**S**)

✅ ¿Puedes añadir funcionalidades sin tocar lo viejo? (**O**)

✅ ¿Tus clases hijas se comportan como las madres? (**L**)

✅ ¿Tus interfaces no obligan a usar lo que no necesitas? (**I**)

✅ ¿Usas la Fuerza de la abstracción en lugar de cosas concretas? (**D**)

---

## 🏁 Conclusión del entrenamiento Jedi

Dominar los principios **SOLID** te da el poder de mantener tu código limpio, fuerte y preparado para cualquier batalla en la galaxia.
Cada vez que usas un principio bien, das un paso hacia el Lado Luminoso del desarrollo profesional.

En el mundo real, escribir buen código no se trata solo de seguir **SOLID** como si fueran mandamientos, sino de **integrarlo con otros principios fundamentales** según el **contexto**. Aquí te dejo un pequeño recordatorio de cómo todos estos pilares **pueden convivir armoniosamente**:

---

### ⚔️ SOLID + Principios universales = Código Jedi

* **🧼 Clean Code:**
  Leer tu código debería ser como leer una historia clara, sin necesidad de decodificadores Sith. Aplica nombres legibles, evita la anidación innecesaria y dale a cada función un único propósito (**SRP** puro).

* **🎯 KISS (Keep It Simple, Stupid):**
  No sobreingenierices. Un buen Jedi no lleva 10 sables láser si con uno basta. Si aplicar un patrón SOLID complica más de lo que ayuda, **KISS te devuelve el equilibrio**.

* **🔁 DRY (Don’t Repeat Yourself):**
  La repetición lleva al Lado Oscuro. Usa abstracciones, funciones reutilizables y clases limpias. ¡Pero cuidado! Reutilizar código mal abstraído rompe el principio de SRP o LSP.

* **🧱 YAGNI (You Aren’t Gonna Need It):**
  No prepares el Halcón Milenario para una batalla espacial si solo vas a cruzar la calle. No implementes lo que no necesitas hoy. Aplica solo los principios que tengan sentido en tu dominio.

* **🧪 ACID (Atomicity, Consistency, Isolation, Durability):**
  En contextos donde trabajas con bases de datos o transacciones críticas (como microservicios con eventos o sistemas bancarios), el principio de **atomicidad** se vuelve crucial. Aquí los conceptos **atomic de Java** y **atomicidad de ACID** se cruzan para proteger la integridad del sistema.

---

### 🚀 El Jedi del código sabe elegir el equilibrio

No es necesario aplicar todo a la vez. El dominio viene de saber **cuándo aplicar cada uno**, cómo combinarlos y cómo **no romper más de lo que arreglas**.

---

