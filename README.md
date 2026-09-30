# enterprise-neural-analyst
Analista de IA empresarial que permite leer cualquier documento que se le cargue y resumirlo o dar informacion del mismo. 
# Enterprise Neural Analyst 🧠⚡
> **Plataforma Empresarial de Análisis Documental Basada en RAG Híbrido y Agentes Autónomos**

---

## 🏢 Planteamiento del Problema Empresarial

En el entorno corporativo moderno, las organizaciones acumulan diariamente volúmenes masivos de información no estructurada: reportes financieros, manuales operativos, normativas legales, auditorías y políticas internas en formato PDF y Office.

Esta sobrecarga de datos genera tres grandes cuellos de botella operativos:

1. **Incapacidad de Búsqueda Semántica:** Los sistemas de gestión documental tradicionales se limitan a búsquedas por palabras clave exactas (*keyword search*), perdiendo contexto y omitiendo respuestas críticas.
2. **Ineficiencia y Costos Operativos:** Un analista promedio invierte hasta el **20% de su jornada laboral** localizando y contrastando información dispersa en múltiples archivos de más de 100 páginas.
3. **Riesgo de Alucinación en IA Convencional:** Intentar usar LLMs comerciales sin una capa de recuperación adecuada introduce el riesgo de "alucinaciones" e invención de datos, algo inaceptable en auditorías, contratos o decisiones corporativas.

---

## 🚀 La Solución: Enterprise Neural Analyst

**Enterprise Neural Analyst** es una solución de arquitectura **RAG Híbrido (Retrieval-Augmented Generation)** diseñada para transformar repositorios documentales pasivos en un motor de inteligencia activa. 

El sistema garantiza:
* **Gobernanza y Precisión:** Respuestas fundamentadas estrictamente en la documentación cargada por la empresa, acompañadas de **citas directas y número de página/fuente**.
* **Agentes Autónomos:** Enrutamiento inteligente que evalúa si la consulta requiere análisis documental profundo, búsqueda externa o procesamiento de lógica.
* **Privacidad de Datos:** Infraestructura modular capaz de conectarse a bases de datos vectoriales privadas sin exponer información confidencial de la organización.

---

## 📐 Arquitectura del Sistema

```mermaid
graph TD
    User[Cliente / Usuario Empresarial]
    API[Gateway FastAPI / Backend REST]
    Router[Agente Orquestador / Router]
    
    VectorDB[(Vector Store / ChromaDB)]
    WebSearch[Microservicio Búsqueda Externa]
    LLM[Modelo LLM Core]
    Docs[Documentos PDFs / Corporativos]

    Docs -->|1. Ingesta + Chunking + Embeddings| VectorDB
    User -->|2. Consulta de Negocio| API
    API -->|3. Procesa Petición| Router

    Router -->|Opción A: Documentación Interna| VectorDB
    Router -->|Opción B: Búsqueda Web| WebSearch
    Router -->|Opción C: Lógica Directa| LLM



## 📐 Arquitectura del Sistema

```mermaid
graph TD
    User[Cliente / Usuario Empresarial]
    API[Gateway FastAPI / Backend REST]
    Router[Agente Orquestador / Router]
    
    VectorDB[(Vector Store / ChromaDB)]
    WebSearch[Microservicio Búsqueda Externa]
    LLM[Modelo LLM Core]
    Docs[Documentos PDFs / Corporativos]

    Docs -->|1. Ingesta + Chunking + Embeddings| VectorDB
    User -->|2. Consulta de Negocio| API
    API -->|3. Procesa Petición| Router

    Router -->|Opción A: Documentación Interna| VectorDB
    Router -->|Opción B: Búsqueda Web| WebSearch
    Router -->|Opción C: Lógica Directa| LLM

    VectorDB -->|4. Contexto Relevante + Citas| Router
    WebSearch -->|4. Resultados Externos| Router

    Router -->|5. Prompt Final = Pregunta + Contexto| LLM
    LLM -->|6. Respuesta Fundamentada| API
    API -->|7. Streaming SSE / Interfaz Web| User

    VectorDB -->|4. Contexto Relevante + Citas| Router
    WebSearch -->|4. Resultados Externos| Router

    Router -->|5. Prompt Final = Pregunta + Contexto| LLM
    LLM -->|6. Respuesta Fundamentada| API
    API -->|7. Streaming SSE / Interfaz Web| User
