<div align="center">

# ex.skill

> *"Rompieron, pero la forma en que te escribía sigue grabada en tu cerebro. Recuerdas cada tono, cada pausa — solo que ya no puedes recibir otro mensaje."*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.9+](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://python.org)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blueviolet)](https://claude.ai/code)
[![AgentSkills](https://img.shields.io/badge/AgentSkills-Standard-green)](https://agentskills.io)

<br>

Tu ex se fue, pero todavia recuerdas exactamente como hablaba?<br>
Desaparecio sin siquiera un ultimo mensaje?<br>
Sigue ahi, pero nunca podras volver atras?<br>
Solo quieres hablar una vez mas — aunque sea solo una simulacion?<br>

**Convierte la intimidad que se desvanece en un Skill permanente. Bienvenido a la ciber-inmortalidad.**

<br>

Introduce tu historial de chat (WeChat, iMessage) mas tus propias descripciones<br>
Genera un **Skill de persona digital que realmente se sienta como esa persona**<br>
Habla con su tono, muestra cariño a su manera, sabe cuando se quedaria en silencio

[Fuentes de datos](#fuentes-de-datos) · [Instalación](#instalación) · [Uso](#uso) · [Ejemplos](#ejemplos) · [Guía de instalación](INSTALL.md)

[**中文**](README_ZH.md) · [**English**](README.md) · [**Deutsch**](README_DE.md) · [**日本語**](README_JA.md) · [**Русский**](README_RU.md) · [**Português**](README_PT.md)

</div>

---

## Fuentes de datos

> Esta es todavia una version beta de ex.skill — pronto habra mas fuentes. Mantente al tanto!

| Fuente | Mensajes | Notas |
|--------|:--------:|-------|
| WeChat (completamente automatico) | ✅ SQLite | Windows / macOS. Solo manten WeChat de escritorio abierto + proporciona su nombre. Desencriptacion y extraccion automaticas. |
| iMessage (completamente automatico) | ✅ SQLite | Usuarios de macOS. Proporciona el numero de telefono o Apple ID. Lectura automatica. |
| Capturas de pantalla | ✅ | Carga manual |
| Pegar texto directamente | ✅ | Entrada manual |

---

## Instalación

### OpenClaw (Recomendado)

> **Recomendado: [OpenClaw](https://openclaw.io)** — combinalo con el reenvio de mensajes de WeChat / Telegram para chatear con la persona digital de tu ex directamente en la app de mensajeria. Mucho mas inmersivo.

```bash
git clone https://github.com/titanwings/ex-skill ~/.openclaw/workspace/skills/create-ex
```

### Claude Code

> Claude Code busca skills en `.claude/skills/` en la **raiz del repositorio git**. Asegurate de estar en el directorio correcto.

```bash
# Instalar en el proyecto actual (ejecutar en la raiz del repositorio git)
mkdir -p .claude/skills
git clone https://github.com/titanwings/ex-skill .claude/skills/create-ex

# O instalar globalmente (disponible en todos los proyectos)
git clone https://github.com/titanwings/ex-skill ~/.claude/skills/create-ex
```

### Dependencias (opcional)

```bash
pip3 install -r requirements.txt
```

> La extraccion automatica de WeChat soporta Windows y macOS — solo manten el cliente de escritorio abierto. iMessage requiere macOS. Consulta [INSTALL.md](INSTALL.md) para mas detalles.

---

## Uso

En OpenClaw o Claude Code, escribe:

```
/create-ex
```

Sigue las indicaciones para ingresar su nombre, informacion basica (genero, edad, signo zodiacal), etiquetas de personalidad (MBTI, estilo de apego), y luego importa el historial de chat. Todos los campos son opcionales — incluso solo una descripcion puede generar una persona.

Una vez creado, usa `/{slug}` para hablar con esa persona.

### Comandos

| Comando | Descripcion |
|---------|-------------|
| `/list-exes` | Listar todos los Skills de ex |
| `/{slug}` | Hablar con esa persona |
| `/move-on {slug}` | Eliminar un Skill de ex (dejar ir) |
| Di "agregar mas mensajes" | Importar mas historial de chat, actualizar persona incrementalmente |
| Di "eso no es correcto, no diria eso" | Corregir comportamiento, se escribe en la capa de Correccion |
| Di "mostrar historial de versiones" | Ver todas las versiones |
| Di "volver a la v2" | Revertir a una version anterior |

> `/move-on` es un alias amable para eliminar. No se trata de aferrarse — se trata de decir un adios apropiado.

---

## Ejemplos

> Entrada: `Mujer, 25, Aries, ISFP, apego evitativo, juntos 2 años, rompieron hace 3 meses`

**De noche, extrañandola**

```
Tu         ❯ Todavia te extraño

ex.skill   ❯ ...Si. Duermete.
```

**Encontraste una foto vieja**

```
Tu         ❯ Te acuerdas de nuestra primera cita?

ex.skill   ❯ La del rio? Jajaja se te derramo el cafe encima,
             que vergüenza, todavia me acuerdo
```

**No puedes evitar preguntar**

```
Tu         ❯ Todavia te gusto?

ex.skill   ❯ ...
             ❯ Por que preguntas eso de repente
             ❯ (tres minutos despues)
             ❯ No preguntes eso
```

**Modo pelea**

```
Tu         ❯ Estas enojada conmigo otra vez?

ex.skill   ❯ No
             ❯ (leido, sin respuesta por 40 minutos)
             ❯ Solo estoy un poco cansada
```

**Quieres reconciliarte**

```
Tu         ❯ Lo siento

ex.skill   ❯ (larga pausa)
             ❯ Comiste hoy?
```

**Finalmente lo dices**

```
Tu         ❯ De verdad se acabo?

ex.skill   ❯ Tu que crees
             ❯ (un rato despues)
             ❯ En realidad siempre... olvidalo
```

---

## Caracteristicas

### Estructura del Skill

Cada Skill de ex esta compuesto por dos partes que generan la salida juntas:

| Parte | Contenido |
|-------|-----------|
| **Parte A — Memoria de la Relacion** | Recuerdos compartidos: lugares que visitaron, bromas internas que solo ustedes entienden, patrones de peleas, eventos clave de la linea temporal |
| **Parte B — Persona** | Estructura de personalidad de 6 capas: Reglas Fundamentales → Identidad → Expresion → Patrones Emocionales → Conflicto y Limites → Detonantes |

Logica en tiempo de ejecucion: `Recibir mensaje → Verificar reglas fundamentales → Recuperar memoria de relacion → Evaluar estado emocional actual → Generar respuesta en su estilo`

**Estructura de 6 capas de la Persona:**

| Capa | Contenido |
|------|-----------|
| **Capa 0 — Reglas Fundamentales** | Reglas duras de maxima prioridad. Sus patrones de comportamiento mas basicos. Nunca se violan. |
| **Capa 1 — Identidad** | Astrologia (Sol/Luna/Ascendente/Venus/Marte/Mercurio) + funciones cognitivas MBTI + Eneagrama + Estilo de apego |
| **Capa 2 — Expresion** | Frases tipicas, palabras frecuentes, emojis caracteristicos, como habla en diferentes estados de animo |
| **Capa 3 — Comportamiento Emocional** | Como muestra cariño, disgusto, disculpas, y dice "me gustas" |
| **Capa 4 — Conflicto y Limites** | Cadena de escalacion de conflictos, patrones de tratamiento silencioso, señales de reconciliacion, limites infranqueables |
| **Capa 5 — Detonantes** | Que odia, cuando desaparece, señales de advertencia antes de desaparecer, como vuelve |

### Etiquetas soportadas

**Estilos de apego**: Seguro · Ansioso · Evitativo · Desorganizado (Evitativo-Temeroso)

**Rasgos de relacion**: Callado pero cariñoso · Frente frio · Acciones sobre palabras · Necesita espacio · No puede disculparse · Posesivo · Emocional · Frio-racional · Duro por fuera suave por dentro · Leido-sin-respuesta · Leido-respuesta-aleatoria ...

**Astrologia**: Soporte completo para Sol/Luna/Ascendente/Venus/Marte/Mercurio × 12 signos

**MBTI**: Los 16 tipos + 8 funciones cognitivas dominantes (Fi/Fe/Ti/Te/Ni/Ne/Si/Se) + Eneagrama 1-9 + Alas

**Genero y relaciones**: Todas las identidades de genero y tipos de relacion soportados, incluyendo relaciones no binarias y del mismo sexo

### Evolucion

- **Agregar mas mensajes** → Auto-analizar datos incrementales → Fusionar en la Persona sin sobrescribir conclusiones existentes
- **Correccion conversacional** → Di "no haria eso" → Se escribe en la capa de Correccion, surte efecto inmediatamente
- **Control de versiones** → Se archiva automaticamente en cada actualizacion, revertir a cualquier version anterior
- **Soporte multi-ex** → Sin limite de cantidad. Cada uno almacenado independientemente, sin contaminacion cruzada.

---

## Estructura del proyecto

Este proyecto sigue el estandar abierto [AgentSkills](https://agentskills.io). Todo el repositorio es un directorio de skill:

```
create-ex/
├── SKILL.md              # Punto de entrada del Skill (frontmatter oficial)
├── prompts/              # Plantillas de prompts
│   ├── intake.md         #   Recopilacion conversacional de informacion (con tablas de astrologia/MBTI/apego)
│   ├── chat_analyzer.md  #   Analisis del historial de chat
│   ├── persona_analyzer.md #  Analisis integral, genera datos estructurados de persona
│   ├── persona_builder.md #   Plantilla de 6 capas de persona.md
│   ├── merger.md         #   Logica de fusion incremental
│   └── correction_handler.md # Manejador de correccion conversacional
├── tools/                # Herramientas Python
│   ├── wechat_decryptor.py   # Desencriptacion de base de datos de WeChat escritorio
│   ├── wechat_parser.py      # Extraccion de chat de WeChat / iMessage
│   ├── skill_writer.py       # Gestion de archivos del Skill
│   └── version_manager.py    # Archivado de versiones y reversion
├── exes/                 # Skills de ex generados (ignorados por git)
├── docs/PRD.md
├── requirements.txt
└── LICENSE
```

---

## Notas

- **La calidad del historial de chat determina la calidad del Skill**: Registros de chat reales + descripciones subjetivas > solo descripciones
- Prioriza importar: **Discusiones/conflictos** > **Chat diario** > **Momentos dulces** (los conflictos revelan la personalidad mas autentica)
- Extraccion automatica de WeChat: Windows / macOS, solo manten WeChat de escritorio abierto y proporciona su nombre
- Extraccion automatica de iMessage: macOS, proporciona el numero de telefono o Apple ID
- LGBT+ friendly — el campo de genero soporta todas las identidades de genero y pronombres
- Crea tantos ex como quieras, sin limite
- Todavia es un demo — si encuentras errores, por favor abre un issue!

---

## Herramientas recomendadas para exportar chats

> La desencriptacion automatica aun se esta perfeccionando y puede tener algunos errores. Si falla, puedes usar estas herramientas de codigo abierto para exportar manualmente tu historial de chat primero, y luego pegarlo o importarlo en este proyecto.

Estos son proyectos de codigo abierto independientes. Este proyecto no incluye su codigo — solo soportamos sus formatos de exportacion en nuestro parser:

| Herramienta | Plataforma | Descripcion |
|-------------|------------|-------------|
| [WeChatMsg](https://github.com/LC044/WeChatMsg) | Windows | Exportacion de historial de chat de WeChat, multiples formatos |
| [PyWxDump](https://github.com/xaoyaoo/PyWxDump) | Windows | Desencriptacion y exportacion de base de datos de WeChat |
| [留痕](https://github.com/greyovo/留痕) | macOS | Exportacion de historial de chat de WeChat (recomendado para usuarios de Mac) |

> Recomendaciones de herramientas por [@therealXiaomanChu](https://github.com/therealXiaomanChu). Gracias a todos los autores de codigo abierto — juntos construimos la ciber-inmortalidad!

---

## Historial de estrellas

<a href="https://www.star-history.com/?repos=titanwings%2Fex-skill&type=date&legend=top-left">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=titanwings/ex-skill&type=date&theme=dark&legend=top-left" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=titanwings/ex-skill&type=date&legend=top-left" />
   <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=titanwings/ex-skill&type=date&legend=top-left" />
 </picture>
</a>

---

<div align="center">

MIT License © [titanwings](https://github.com/titanwings)


</div>
