# SEA Noise Manager

Herramienta en un único archivo HTML para analizar los resultados de ruido calculados con **Designer Noise** (método SEA) a partir del Excel que exporta el programa (`REPORT_FINAL.xls`). Funciona sin instalación y **sin conexión a internet**.

## Qué hace

- **Importación del Excel de Designer Noise**
  - Hoja **SPL**: nivel recibido en cada compartimento por fuente y camino (AB aéreo, SB estructural, SSB estructural secundario) en bandas de octava de 31,5 Hz a 8 kHz, y las posiciones de interés (P1, P2…).
  - Hojas por elemento (panel): **Element Noise** (ruido radiado por cada panel, FSB y SSB), **Element La** (aceleración, dB re 1 µg), **Element Radiation** (σ, efecto de absorción y efecto de joiner panel), **TL**, **Damping Loss** y **Coupling Loss**.
  - Comprobación al importar: la suma de las fuentes se compara con los totales de Designer Noise, y la suma de los paneles con SB + SSB de cada compartimento.
- **Árbol editable**: carpetas con clic derecho, renombrar (F2), arrastrar y soltar, deshacer (Ctrl+Z). Cada compartimento se despliega en sus fuentes y sus paneles.
- **Condiciones de navegación**: cada condición define qué fuentes funcionan y un offset en dB por fuente (régimen, velocidad, número de equipos). Todos los niveles se recalculan al momento.
- **Vistas**
  - Compartimento: espectro A/C/Z con cursor, superposición de fuentes, caminos o paneles; contribuciones (share), tabla por bandas y nivel en cada condición.
  - Panel: ruido radiado, aceleración (dB, mm/s² o mm/s) y eficiencia de radiación; propiedades (σ, absorción, joiner, TL, η), compartimentos a los que radia y elementos conectados. Los paneles tratados se marcan con **T**.
  - Carpeta y condición: tabla de todos los compartimentos con criterio, margen y fuente dominante.
- **Comparación de dos modelos** (A: situación original, B: con tratamiento): Δ por espacio, por fuente, por banda y por panel; resultado de cumplimiento (*cumple*, *corregido con el tratamiento*, *sigue superando*, *empeora*).
- **Informe** en español o inglés (resumen de cumplimiento y una página por espacio con gráfico A/B, bandas, fuentes y paneles con cambio de tratamiento), para imprimir o guardar en PDF.
- **Exportación a Excel** y proyectos `.json` (guardar / abrir), con recuperación de la última sesión.

## Uso

**En línea:** https://oscarvib.github.io/sea-noise-manager/ (siempre la última versión). En Chrome o Edge se puede instalar como aplicación con su propio icono: botón de instalar en la barra de direcciones, o menú ⋮ → *Enviar, guardar y compartir* → *Instalar página como aplicación*. Una vez instalada, abre también sin conexión.

**Archivo local:** descarga `sea-noise-manager.html` y ábrelo en Chrome o Edge. Lleva dentro la librería de lectura de Excel y las fuentes, así que funciona sin internet.

1. **Import Excel** → el Excel de Designer Noise (modelo A).
2. Opcional: en *Models*, **+** → el Excel del modelo con tratamiento (modelo B) y marca *Compare A vs B*.
3. Define las condiciones de navegación y los criterios, y genera el **Report** o el **Export Excel**.

## Licencias de terceros

- SheetJS Community Edition 0.18.5 — Apache 2.0 (`lib/SheetJS-LICENSE.txt`).
- IBM Plex — SIL Open Font License 1.1 (`fonts/OFL.txt`).
