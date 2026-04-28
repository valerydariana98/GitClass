# Apuntes de Git

**Nombre:** Valery Dariana Ortuño Panozo

Repositorio creado para registrar el avance diario de la materia.

---

## Clase 1 – Introducción a Git

### ¿Qué es Git?

Git es un Sistema de Control de Versiones Distribuido (VCS).

Permite:

* Guardar archivos
* Mantener un historial de cambios
* Trabajar de manera local sin depender de internet

---

### ¿Cómo nació Git?

Git fue creado por **Linus Torvalds**.

---

### Instalación de Git

Para instalar Git:

1. Ir a la página oficial:
   https://git-scm.com/install/

2. Descargar según tu sistema operativo

3. Verificar instalación en terminal:

```bash
git --version
```

---

### Configuraciones básicas

Configurar nombre de usuario:

```bash
git config --global user.name "Tu Nombre"
```

Configurar correo:

```bash
git config --global user.email "tu@correo.com"
```

Configuración recomendada:

```bash
git config --global core.autocrlf true
```

---

### Archivos importantes en un repositorio

Todo repositorio debería tener:

* `README.md` → Documentación del proyecto
* `.gitignore` → Archivos que Git debe ignorar

---

## Clase 2 – Estados y Commits

### Los 3 estados de Git

Los archivos en Git pasan por tres estados:

| Estado | Zona | Descripción |
|---|---|---|
| Modificado | Directorio de Trabajo | Cambios locales que Git aún no tiene registrados |
| Preparado | Stage Area | Cambios seleccionados listos para el próximo commit |
| Confirmado | Repositorio Local | Cambios guardados en el historial con un hash único |

---

### Directorio de Trabajo

Git observa los archivos y los clasifica en:

* **Untracked:** Archivo nuevo que Git nunca ha visto
* **Modified:** Archivo que Git ya conoce y fue modificado, eliminado o renombrado

Comandos útiles:

```bash
# Revertir un archivo a su estado original (cuidado: borra los cambios)
git restore <archivo>
```

> Para que Git ignore un archivo nuevo, agrega su nombre al `.gitignore`.

---

### Stage Area

Es el área de preparación donde seleccionas qué cambios irán en el próximo commit.

```bash
# Agregar un archivo específico
git add <archivo>

# Agregar todos los archivos observados por Git
git add .

# Sacar un archivo del stage (vuelve a "Modified")
git restore --staged <archivo>
```

---

### Repositorio Local

Una vez en stage, se confirman los cambios con un commit, que crea un punto en el historial.

```bash
# Crear un commit
git commit -m "mensaje"

# Deshacer el último commit (los cambios vuelven a stage)
git reset --soft HEAD~1
```

---

### Buenas prácticas con commits

#### ¿Cada cuánto hacer un commit?

Usa **commits atómicos**: cada commit representa un único cambio lógico, pequeño y completo. Es mejor varios commits pequeños con sentido que uno grande con todo.

#### Cómo escribir un buen mensaje de commit

1. **Usa verbos imperativos en inglés:**

   * `Add` → se añade un nuevo archivo
   * `Change` → se modifica un archivo existente
   * `Fix` → se corrige un bug
   * `Remove` → se elimina un archivo

2. **Sin punto final ni puntos suspensivos**

3. **Máximo 50 caracteres** — si tienes mucho que explicar, probablemente debas separar el commit

4. **Usa prefijos semánticos:**

```bash
git commit -m "<tipo>: <descripción>"
```

| Prefijo | Cuándo usarlo |
|---|---|
| `feat` | Nueva funcionalidad para el usuario |
| `fix` | Bug que afecta al usuario |
| `perf` | Mejora de rendimiento |
| `build` | Cambios en el sistema de build o despliegue |
| `ci` | Cambios en integración continua |
| `docs` | Cambios en documentación |
| `refactor` | Renombrar variables, funciones, reestructurar código |
| `style` | Formato, espacios, tabulaciones (sin impacto funcional) |
| `test` | Tests nuevos o refactorización de tests |

5. **Agrega cuerpo si necesitas más contexto:**

```bash
git commit
# Primera línea: título (prefijo + descripción)
# Desde la segunda línea: cuerpo con la explicación detallada
```