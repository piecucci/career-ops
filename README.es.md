<!-- markdownlint-disable -->
# Career-Ops

[English](README.md) | [Español](README.es.md) | [Português (Brasil)](README.pt-BR.md) | [한국어](README.ko-KR.md) | [日本語](README.ja.md) | [Русский](README.ru.md) | [简体中文](README.cn.md) | [繁體中文](README.zh-TW.md)

<div align="center">
  <a href="https://x.com/santifer"><img src="docs/hero-banner.jpg" alt="Career-Ops — Sistema Multi-Agente de Busqueda de Empleo" width="800"></a>
</div>

<div align="center">

*Meses mandando CVs al vacio. Asi que me construi el sistema que echaba en falta.*  
Las empresas usan IA para descartarte. **Yo le di a los candidatos IA para *elegirlas*.**  
*Ahora es open source.*

</div>

<div align="center">
  <img src="https://img.shields.io/badge/Claude_Code-000?style=flat&logo=anthropic&logoColor=white" alt="Claude Code">
  <img src="https://img.shields.io/badge/OpenCode-111827?style=flat&logo=terminal&logoColor=white" alt="OpenCode">
  <img src="https://img.shields.io/badge/Codex_(pronto)-6B7280?style=flat&logo=openai&logoColor=white" alt="Codex">
  <img src="https://img.shields.io/badge/Node.js-339933?style=flat&logo=node.js&logoColor=white" alt="Node.js">
  <img src="https://img.shields.io/badge/Go-00ADD8?style=flat&logo=go&logoColor=white" alt="Go">
  <img src="https://img.shields.io/badge/Playwright-2EAD33?style=flat&logo=playwright&logoColor=white" alt="Playwright">
  <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="MIT">
  <a href="https://discord.gg/8pRpHETxa4"><img src="https://img.shields.io/badge/Discord-5865F2?style=flat&logo=discord&logoColor=white" alt="Discord"></a>
  <br>
  <img src="https://img.shields.io/badge/EN-blue?style=flat" alt="EN">
  <img src="https://img.shields.io/badge/ES-red?style=flat" alt="ES">
  <img src="https://img.shields.io/badge/DE-grey?style=flat" alt="DE">
  <img src="https://img.shields.io/badge/FR-blue?style=flat" alt="FR">
  <img src="https://img.shields.io/badge/PT--BR-green?style=flat" alt="PT-BR">
  <img src="https://img.shields.io/badge/JA-red?style=flat" alt="JA">
</div>

---

<div align="center">
  <img src="docs/demo.gif" alt="Career-Ops Demo" width="800">
</div>

<div align="center">**740+ ofertas evaluadas · 100+ CVs personalizados · 1 trabajo soñado conseguido**</div>

<div align="center"><a href="https://discord.gg/8pRpHETxa4"><img src="https://img.shields.io/badge/Unete_a_la_comunidad-Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white" alt="Discord"></a></div>

## Que es esto

Career-Ops convierte cualquier CLI de IA en un centro de mando de busqueda de empleo. En vez de trackear aplicaciones en un spreadsheet, tienes un pipeline AI que:

- **Evalua ofertas** con scoring estructurado A-F (10 dimensiones ponderadas)
- **Genera PDFs personalizados** -- CVs ATS-optimizados por oferta
- **Escanea portales** automaticamente (Greenhouse, Ashby, Lever, webs de empresas)
- **Procesa en batch** -- evalua 10+ ofertas en paralelo con sub-agentes
- **Trackea todo** en una fuente de verdad unica con checks de integridad

> **Importante: Esto NO es una herramienta de "mandar por mandar".** Career-ops es un filtro -- te ayuda a encontrar las pocas ofertas que merecen tu tiempo de entre cientos. El sistema recomienda encarecidamente no aplicar a nada con un scoring inferior a 4.0/5. Tu tiempo es valioso, y el del recruiter tambien. Revisa siempre antes de enviar.

Career-ops es agentico: Claude Code navega por las paginas de empleo con Playwright, evalua el encaje razonando sobre tu CV vs la descripcion del puesto (no por matching de keywords), y adapta tu resume por oferta.

> **Aviso: las primeras evaluaciones no seran perfectas.** El sistema todavia no te conoce. Dale contexto -- tu CV, tu historia profesional, tus logros, tus preferencias, en que eres bueno, que quieres evitar. Cuanto mas lo alimentes, mejor funcionara. Piensa en ello como en el onboarding de un nuevo recruiter: la primera semana necesita aprender sobre ti, luego se vuelve indispensable.

Construido por alguien que lo uso para evaluar 740+ ofertas de empleo, generar 100+ CVs personalizados, y conseguir un puesto de Head of Applied AI. [Lee el caso de estudio completo](https://santifer.io/career-ops-system).

## Funcionalidades

| Funcionalidad | Descripcion |
|---------------|-------------|
| **Auto-Pipeline** | Pega una URL, obten una evaluacion completa + PDF + entrada en el tracker |
| **Evaluacion de 6 Bloques** | Resumen del rol, encaje de CV, estrategia de nivel, investigacion de comp, personalizacion, prep de entrevista (STAR+R) |
| **Banco de Historias de Entrevista** | Acumula historias STAR+Reflection a traves de las evaluaciones -- 5-10 historias maestras que responden a cualquier pregunta conductual |
| **Scripts de Negociacion** | Frameworks de negociacion salarial, respuesta a descuentos geograficos, palanca con ofertas competidoras |
| **Generacion de PDF ATS** | CVs con keywords inyectadas con diseño Space Grotesk + DM Sans |
| **Escaneo de Portales** | 45+ empresas pre-configuradas (Anthropic, OpenAI, ElevenLabs, Retool, n8n...) + queries personalizadas en Ashby, Greenhouse, Lever, Wellfound |
| **Procesamiento en Batch** | Evaluacion paralela con workers de `claude -p` |
| **Dashboard TUI** | Terminal UI para navegar, filtrar y ordenar tu pipeline |
| **Human-in-the-Loop** | La IA evalua y recomienda, tu decides y actuas. El sistema nunca envia una aplicacion -- tu siempre tienes la ultima palabra |
| **Integridad del Pipeline** | Merge automatizado, dedup, normalizacion de estados, health checks |

## Inicio Rapido

```bash
# 1. Clonar e instalar
git clone https://github.com/santifer/career-ops.git
cd career-ops && npm install
npx playwright install chromium   # Requerido para la generacion de PDF

# 2. Comprobar setup
npm run doctor                     # Valida todos los prerrequisitos

# 3. Configurar
cp config/profile.example.yml config/profile.yml  # Edita con tus datos
cp templates/portals.example.yml portals.yml       # Personaliza empresas

# 4. Añade tu CV
# Crea cv.md en la raiz del proyecto con tu CV en markdown

# 5. Personaliza con Claude
claude   # Abre Claude Code en este directorio

# Luego pidele a Claude que adapte el sistema a ti:
# "Cambia los arquetipos a roles de backend engineering"
# "Traduce los modos a ingles"
# "Añade estas 5 empresas a portals.yml"
# "Actualiza mi perfil con este CV que te pego"

# 6. Empieza a usarlo
# Pega la URL de un trabajo o ejecuta /career-ops
```

> **El sistema esta diseñado para ser personalizado por el propio Claude.** Modos, arquetipos, pesos de puntuacion, scripts de negociacion -- simplemente pidele a Claude que los cambie. Lee los mismos archivos que usa, asi que sabe exactamente que editar.

Consulta [docs/SETUP.md](docs/SETUP.md) para la guia de instalacion completa.

## Uso

Career-ops es un unico comando de slash con multiples modos:

```
/career-ops                → Muestra todos los comandos disponibles
/career-ops {pega un JD}   → Pipeline completo (evaluacion + PDF + tracker)
/career-ops scan           → Escanea portales en busca de nuevas ofertas
/career-ops pdf            → Genera CV optimizado para ATS
/career-ops batch          → Evaluacion por lotes de multiples ofertas
/career-ops tracker        → Mira el estado de tus aplicaciones
/career-ops apply          → Rellena formularios de aplicacion con IA
/career-ops pipeline       → Procesa URLs pendientes
/career-ops contacto       → Mensaje de outreach para LinkedIn
/career-ops deep           → Investigacion profunda de empresa
/career-ops training       → Evalua un curso/certificacion
/career-ops project        → Evalua un proyecto de portfolio
```

O simplemente pega la URL o descripcion de un trabajo directamente -- career-ops lo detecta automaticamente y ejecuta el pipeline completo.

## Como funciona

```
Pegas la URL o descripcion de un trabajo
        │
        ▼
┌──────────────────┐
│  Deteccion de    │  Clasifica: LLMOps / Agentic / PM / SA / FDE / Transformation
│  Arquetipo       │
└────────┬─────────┘
         │
┌────────▼─────────┐
│  Evaluacion A-F  │  Encaje, gaps, research de comp, historias STAR
│  (lee cv.md)     │
└────────┬─────────┘
         │
    ┌────┼────┐
    ▼    ▼    ▼
 Informe  PDF  Tracker
  .md   .pdf   .tsv
```

## Portales Pre-configurados

El scanner viene con **45+ empresas** listas para escanear y **19 queries de busqueda** en los principales job boards. Copia `templates/portals.example.yml` a `portals.yml` y añade las tuyas:

**AI Labs:** Anthropic, OpenAI, Mistral, Cohere, LangChain, Pinecone
**Voice AI:** ElevenLabs, PolyAI, Parloa, Hume AI, Deepgram, Vapi, Bland AI
**AI Platforms:** Retool, Airtable, Vercel, Temporal, Glean, Arize AI
**Contact Center:** Ada, LivePerson, Sierra, Decagon, Talkdesk, Genesys
**Enterprise:** Salesforce, Twilio, Gong, Dialpad
**LLMOps:** Langfuse, Weights & Biases, Lindy, Cognigy, Speechmatics
**Automation:** n8n, Zapier, Make.com
**European:** Factorial, Attio, Tinybird, Clarity AI, Travelperk

**Job boards buscados:** Ashby, Greenhouse, Lever, Wellfound, Workable, RemoteFront

## Dashboard TUI

El dashboard de terminal integrado te permite navegar por tu pipeline visualmente:

```bash
cd dashboard
go build -o career-dashboard .
./career-dashboard --path ..
```

Funcionalidades: 6 pestañas de filtro, 4 modos de ordenacion, vista agrupada/plana, previews cargadas en lazy, cambios de estado inline.

## Estructura del Proyecto

```
career-ops/
├── CLAUDE.md                    # Instrucciones para el agente
├── cv.md                        # Tu CV (crealo tu)
├── article-digest.md            # Tus "proof points" (opcional)
├── config/
│   └── profile.example.yml      # Plantilla para tu perfil
├── modes/                       # 14 modos de habilidad
│   ├── _shared.md               # Contexto compartido (personaliza esto)
│   ├── oferta.md                # Evaluacion individual
│   ├── pdf.md                   # Generacion de PDF
│   ├── scan.md                  # Escaner de portales
│   ├── batch.md                 # Procesamiento por lotes
│   └── ...
├── templates/
│   ├── cv-template.html         # Plantilla de CV optimizada para ATS
│   ├── portals.example.yml      # Plantilla de config del escaner
│   └── states.yml               # Estados canonicos
├── batch/
│   ├── batch-prompt.md          # Prompt auto-contenido para el worker
│   └── batch-runner.sh          # Script orquestador
├── dashboard/                   # Visor de pipeline en Go TUI
├── data/                        # Tus datos de tracking (gitignored)
├── reports/                     # Informes de evaluacion (gitignored)
├── output/                      # PDFs generados (gitignored)
├── fonts/                       # Space Grotesk + DM Sans
├── docs/                        # Setup, personalizacion, arquitectura
└── examples/                    # Ejemplo de CV, informe, proof points
```

## Tech Stack

![Claude Code](https://img.shields.io/badge/Claude_Code-000?style=flat&logo=anthropic&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=node.js&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat&logo=playwright&logoColor=white)
![Go](https://img.shields.io/badge/Go-00ADD8?style=flat&logo=go&logoColor=white)
![Bubble Tea](https://img.shields.io/badge/Bubble_Tea-FF75B5?style=flat&logo=go&logoColor=white)

- **Agente**: Claude Code con habilidades y modos personalizados
- **PDF**: Playwright/Puppeteer + plantilla HTML
- **Scanner**: Playwright + Greenhouse API + WebSearch
- **Dashboard**: Go + Bubble Tea + Lipgloss (tema Catppuccin Mocha)
- **Datos**: Tablas Markdown + config YAML + archivos TSV por lotes

## Sobre el autor

Soy Santiago -- Head of Applied AI, ex-fundador (monte y vendi un negocio que sigue funcionando con mi nombre). Construi career-ops para gestionar mi propia busqueda de empleo. Funciono: lo use para conseguir mi puesto actual.

Mi portfolio y otros proyectos open source → [santifer.io](https://santifer.io)

## Documentacion

- [SETUP.md](docs/SETUP.md) -- Guia de instalacion
- [CUSTOMIZATION.md](docs/CUSTOMIZATION.md) -- Como personalizar
- [ARCHITECTURE.md](docs/ARCHITECTURE.md) -- Como funciona el sistema

## Tambien Open Source

- **[cv-santiago](https://github.com/santifer/cv-santiago)** -- La web de portfolio (santifer.io) con chatbot de IA, dashboard de LLMOps y casos de estudio. Si necesitas un portfolio para mostrar junto con tu busqueda de empleo, hazle un fork y hazlo tuyo.

## Sobre el Autor

Soy Santiago -- Head of Applied AI, ex-fundador (monte y vendi un negocio que todavia funciona con mi nombre). Construi career-ops para gestionar mi propia busqueda de empleo. Funciono: lo use para conseguir mi puesto actual.

Mi portfolio y otros proyectos open source → [santifer.io](https://santifer.io)

☕ [Invitame a un cafe](https://buymeacoffee.com/santifer) si career-ops te ayudo en tu busqueda de empleo.

## Star History

<a href="https://www.star-history.com/?repos=santifer%2Fcareer-ops&type=timeline&legend=top-left">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=santifer/career-ops&type=timeline&theme=dark&legend=top-left" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=santifer/career-ops&type=timeline&legend=top-left" />
   <img alt="Star History Chart" src="https://api.star-history.com/chart?repos=santifer/career-ops&type=timeline&legend=top-left" />
 </picture>
</a>

## Disclaimer

**career-ops es una herramienta local y open-source — NO un servicio alojado.** Al usar este software, reconoces que:

1. **Tu controlas tus datos.** Tu CV, informacion de contacto y datos personales permanecen en tu maquina y se envian directamente al proveedor de IA que elijas (Anthropic, OpenAI, etc.). Nosotros no recopilamos, almacenamos ni tenemos acceso a ninguno de tus datos.
2. **Tu controlas la IA.** Los prompts por defecto instruyen a la IA para que no envie aplicaciones automaticamente, pero los modelos de IA pueden comportarse de forma impredecible. Si modificas los prompts o usas modelos diferentes, lo haces bajo tu propio riesgo. **Revisa siempre el contenido generado por IA para comprobar su exactitud antes de enviarlo.**
3. **Cumples con los ToS de terceros.** Debes usar esta herramienta de acuerdo con los Terminos de Servicio de los portales de empleo con los que interactues (Greenhouse, Lever, Workday, LinkedIn, etc.). No uses esta herramienta para hacer spam a empleadores o saturar sistemas ATS.
4. **Sin garantias.** Las evaluaciones son recomendaciones, no verdades absolutas. Los modelos de IA pueden alucinar habilidades o experiencia. Los autores no son responsables de los resultados del empleo, aplicaciones rechazadas, restricciones de cuenta o cualquier otra consecuencia.

Consulta [LEGAL_DISCLAIMER.md](LEGAL_DISCLAIMER.md) para los detalles completos. Este software se proporciona bajo la [Licencia MIT](LICENSE) "tal cual", sin garantia de ningun tipo.

## Licencia

MIT

## Conectemos

[![Website](https://img.shields.io/badge/santifer.io-000?style=for-the-badge&logo=safari&logoColor=white)](https://santifer.io)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/santifer)
[![X](https://img.shields.io/badge/X-000?style=for-the-badge&logo=x&logoColor=white)](https://x.com/santifer)
[![Discord](https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/8pRpHETxa4)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:hi@santifer.io)
[![Buy Me a Coffee](https://img.shields.io/badge/Buy_Me_a_Coffee-FFDD00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/santifer)
