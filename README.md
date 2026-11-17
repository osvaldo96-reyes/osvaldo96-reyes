<!-- Encabezado -->
<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,50:1F6FEB,100:2F81F7&height=190&section=header&text=Osvaldo%20Reyes&fontSize=44&fontColor=ffffff&fontAlignY=36&desc=Software%20Engineer%20%E2%86%92%20DevOps&descSize=18&descAlignY=58&animation=fadeIn" alt="Osvaldo Reyes" width="100%"/>
</p>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=20&pause=1200&color=2F81F7&center=true&vCenter=true&width=620&lines=Software+Engineer+en+transici%C3%B3n+a+DevOps;Contenedores+%C2%B7+Linux+%C2%B7+Automatizaci%C3%B3n;Llevo+sistemas+reales+a+producci%C3%B3n;Si+lo+hago+dos+veces%2C+lo+automatizo" alt="Typing SVG"/>
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/osvaldo-reyes-campos/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
  <img src="https://img.shields.io/badge/Ubicaci%C3%B3n-M%C3%A9xico-2F81F7?style=for-the-badge&logo=googlemaps&logoColor=white" alt="México"/>
  <img src="https://img.shields.io/badge/Abierto_a-oportunidades_DevOps-238636?style=for-the-badge" alt="Abierto a oportunidades"/>
</p>

---

### 👨‍💻 Sobre mí

- 🏛️ Desarrollo y opero **sistemas de grabación y gestión de audiencias** en el sector judicial: aplicaciones web, bases de datos y streaming de video en tiempo real.
- 🐳 Contenerizo y documento infraestructura completa con **Docker Compose**: apps Flask, Nginx, SQL Server, MySQL, FTP y servidores de streaming.
- 📡 Construyo pipelines de video **RTMP → WebRTC** (OBS, SRS, FFmpeg, OvenMediaEngine) para transmisiones en vivo de baja latencia.
- 🚀 Hoy me enfoco en **DevOps**: CI/CD, infraestructura como código, observabilidad y nube.

### 🛠️ Stack

**Lenguajes y backend**
<p>
  <img src="https://skillicons.dev/icons?i=python,fastapi,flask,js,html,css,kotlin&theme=dark" alt="Lenguajes"/>
</p>

**Infraestructura y DevOps**
<p>
  <img src="https://skillicons.dev/icons?i=docker,nginx,linux,ubuntu,bash,git,github,githubactions&theme=dark" alt="DevOps"/>
</p>

**Bases de datos y streaming**
<p>
  <img src="https://skillicons.dev/icons?i=mysql,postgres&theme=dark" alt="Bases de datos"/>
  &nbsp;
  <img src="https://img.shields.io/badge/SQL%20Server-CC2927?style=for-the-badge&logo=microsoftsqlserver&logoColor=white" alt="SQL Server" height="44"/>
  <img src="https://img.shields.io/badge/FFmpeg-007808?style=for-the-badge&logo=ffmpeg&logoColor=white" alt="FFmpeg" height="44"/>
  <img src="https://img.shields.io/badge/OBS-302E31?style=for-the-badge&logo=obsstudio&logoColor=white" alt="OBS" height="44"/>
  <img src="https://img.shields.io/badge/WebRTC-333333?style=for-the-badge&logo=webrtc&logoColor=white" alt="WebRTC" height="44"/>
</p>

### 💼 Proyectos profesionales

> El código de estos sistemas es privado porque está en producción en una institución. Aquí está **qué resuelven, cómo están construidos y qué hice yo**.

---

#### 🎥 Grabador distribuido de audiencias · *arquitecto y desarrollador*

Sistema que **reemplaza un software comercial de grabación**: una central coordina agentes instalados junto a las cámaras de cada sala, que graban, vigilan la señal y entregan el video final.

<p>
  <img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white"/>
  <img src="https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat-square&logo=sqlalchemy&logoColor=white"/>
  <img src="https://img.shields.io/badge/FFmpeg-007808?style=flat-square&logo=ffmpeg&logoColor=white"/>
  <img src="https://img.shields.io/badge/systemd-30D475?style=flat-square&logo=linux&logoColor=black"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white"/>
  <img src="https://img.shields.io/badge/SQL_Server_%7C_MySQL_%7C_SQLite-CC2927?style=flat-square&logo=microsoftsqlserver&logoColor=white"/>
</p>

```mermaid
flowchart LR
  subgraph DC["Centro de datos / nube"]
    C["Central<br/>FastAPI + panel web"] --- DB[("Base de datos<br/>SQL Server · MySQL")]
    C --> FTP[("Almacén de videos<br/>FTP · S3")]
  end
  subgraph S["Edificio"]
    A1["Agente 1<br/>FFmpeg"] ---|RTMP/RTSP| CAM1(("Cámaras sala A"))
    A2["Agente N<br/>FFmpeg"] ---|RTMP/RTSP| CAM2(("Cámaras sala N"))
  end
  C <-->|"API + token"| A1
  C <-->|"API + token"| A2
```

- Diseñé la arquitectura **central + agentes**: los agentes no guardan lógica de negocio y la central no guarda estado en memoria, así que **escala horizontalmente**.
- **Grabación tolerante a fallos**: pausa, reanudación y unión de tramos en MP4. Si el proceso se detiene, cierra los archivos íntegros y al volver recupera las grabaciones.
- **Instalador offline** para Ubuntu 16.04+ y Windows, con servicio **systemd**, actualización y desinstalación.
- Configuración 100 % por **variables de entorno**, base de datos intercambiable, monitoreo de salud y envío con reintentos.
- Documentación completa: arquitectura, despliegue, diccionario de datos y roadmap a **AWS** (ECS/Fargate, RDS, S3).

---

#### 🏛️ Plataforma de gestión y grabación de audiencias · *full-stack + operación*

Aplicación web **en producción** que centraliza la operación de las salas: agenda de audiencias, estado de grabación en vivo, control remoto de OBS, reportes y auditoría.

<p>
  <img src="https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white"/>
  <img src="https://img.shields.io/badge/Gunicorn_+_WebSockets-499848?style=flat-square&logo=gunicorn&logoColor=white"/>
  <img src="https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white"/>
  <img src="https://img.shields.io/badge/SQL_Server-CC2927?style=flat-square&logo=microsoftsqlserver&logoColor=white"/>
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white"/>
  <img src="https://img.shields.io/badge/OBS_WebSocket-302E31?style=flat-square&logo=obsstudio&logoColor=white"/>
  <img src="https://img.shields.io/badge/SOAP-6D6D6D?style=flat-square"/>
</p>

```mermaid
flowchart LR
  U(("Operadores")) --> N["Nginx<br/>reverse proxy"] --> F["Flask + Gunicorn<br/>WebSockets"]
  F --> R[("SQL Server<br/>usuarios · roles · auditoría")]
  F --> J[("SQL Server<br/>audiencias")]
  F --> M[("MySQL<br/>4 salas")]
  F -->|WebSocket| O["OBS de cada sala"]
  F -->|SOAP| W["Servicio externo<br/>de expedientes"]
  F --> V[("Videos<br/>FTP")]
```

- Integré **7 bases de datos** (3 SQL Server y 4 MySQL) y servicios externos (SOAP, OBS WebSocket) en una sola plataforma.
- **Seguridad**: roles y permisos por módulo, bitácora de auditoría de más de 1 M de eventos y **URLs firmadas con HMAC** con expiración para descargar videos.
- Contenericé la app (**Docker + Gunicorn/eventlet + Nginx**) con healthchecks, separación dev/prod y script de despliegue.

---

#### 🐳 Infraestructura contenerizada y streaming en vivo · *DevOps*

Toda la infraestructura del servidor como código: **11 contenedores** documentados, reproducibles y con guías de instalación.

> 🔓 **Demo pública de esta arquitectura:** [streaming-rtmp-webrtc-stack](https://github.com/osvaldo96-reyes/streaming-rtmp-webrtc-stack). Se levanta con `docker compose up` y tiene CI con lint, escaneo de seguridad y prueba de punta a punta.
>
> [![CI](https://github.com/osvaldo96-reyes/streaming-rtmp-webrtc-stack/actions/workflows/ci.yml/badge.svg)](https://github.com/osvaldo96-reyes/streaming-rtmp-webrtc-stack/actions/workflows/ci.yml)

```mermaid
flowchart LR
  OBS["OBS<br/>4 salas"] -->|RTMP| SRS["SRS<br/>ingesta"]
  SRS --> R["Relays FFmpeg<br/>4 contenedores"]
  R -->|RTMP| OME["OvenMediaEngine"]
  OME -->|"WebRTC, menos de 1 s"| B(("Navegador"))
```

- Pipeline de video en vivo **RTMP → WebRTC** de baja latencia (SRS, FFmpeg, OvenMediaEngine).
- Pasé contenedores creados a mano con `docker run` a **Docker Compose versionado** en Git, con secretos fuera del repo (`.env.example`) y un mapa de puertos.
- **Diagnóstico y operación**: análisis de almacenamiento de SQL Server, respaldos verificados y plan de migración a **volúmenes persistentes** con rollback automático.
- Auditoría de seguridad de repositorios: detección y retiro de credenciales expuestas.

---

### 🧭 Ruta DevOps

| Área | Estado |
|---|---|
| Linux, Bash, redes | ✅ En producción |
| Docker y Docker Compose | ✅ En producción |
| Nginx (reverse proxy) | ✅ En producción |
| Git y GitHub | ✅ |
| CI/CD con GitHub Actions | ✅ Lint, escaneo de seguridad y pruebas E2E |
| Kubernetes | 🔜 |
| Terraform (IaC) | 🔜 |
| AWS / nube | 🔜 |
| Prometheus + Grafana | 🔜 |

### 📊 Actividad

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=osvaldo96-reyes&show_icons=true&count_private=true&include_all_commits=true&theme=github_dark&hide_border=true&bg_color=0D1117&title_color=2F81F7&icon_color=2F81F7&locale=es" height="165" alt="Estadísticas"/>
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=osvaldo96-reyes&layout=compact&theme=github_dark&hide_border=true&bg_color=0D1117&title_color=2F81F7&locale=es&langs_count=8" height="165" alt="Lenguajes"/>
</p>

<p align="center">
  <img src="https://streak-stats.demolab.com?user=osvaldo96-reyes&theme=github-dark-blue&hide_border=true&background=0D1117&ring=2F81F7&fire=2F81F7&currStreakLabel=2F81F7&locale=es" alt="Racha"/>
</p>

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/osvaldo96-reyes/osvaldo96-reyes/output/github-contribution-grid-snake-dark.svg"/>
    <img src="https://raw.githubusercontent.com/osvaldo96-reyes/osvaldo96-reyes/output/github-contribution-grid-snake.svg" alt="Contribuciones"/>
  </picture>
</p>

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:2F81F7,50:1F6FEB,100:0D1117&height=110&section=footer" width="100%" alt=""/>
</p>
