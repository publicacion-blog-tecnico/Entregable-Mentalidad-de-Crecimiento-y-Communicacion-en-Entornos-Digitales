 # Entregable-Mentalidad-de-Crecimiento-y-Communicacion-en-Entornos-Digitales
El objetivo de este trabajo es aplicar estrategias de comunicación adaptativa, mentalidad de desarrollo continuo y optimización de flujos de trabajo en plataformas digitales.

Presentación general y estructura del trabajo.

Alumno: Márquez Camila

Entrada de Blog Técnico: Resolución de Incidente y Aprendizajes

1. Contexto
Durante el desarrollo e integración de microservicios en un entorno de producción basado en contenedores, gestionamos la infraestructura de comunicación entre un servicio de procesamiento de pagos y la API principal. El objetivo principal del sprint era optimizar la latencia y garantizar alta disponibilidad durante picos de tráfico.
2. Problema
Tras un despliegue reciente, el servicio de pagos comenzó a registrar tiempos de respuesta superiores a los 5000 ms, generando errores 504 Gateway Timeout de manera intermitente. Esto afectó aproximadamente al 12% de las transacciones activas durante el periodo de mayor demanda.
3. Acciones
•	Identificación y Aislamiento: Se analizaron los logs centralizados y métricas de APM para rastrear el cuello de botella, identificando que el pool de conexiones a la base de datos se saturaba por consultas no optimizadas.

•	Mitigación Inmediata: Se escaló temporalmente el número de réplicas del servicio y se ajustó el timeout máximo de las conexiones para liberar recursos acumulados.

•	Post-mortem Constructivo: Se realizó una sesión de análisis sin culpa (blameless post-mortem) con el equipo para revisar la causa raíz, identificando la ausencia de un índice clave en la tabla de transacciones y la falta de pruebas de carga previas al despliegue.
5. Aprendizajes
•	Mejoras Técnicas: Se implementó el índice faltante en la base de datos y se configuró un patrón de Circuit Breaker para prevenir fallos en cascada.

•	Procesos: Se integraron pruebas de carga automatizadas en la canalización de CI/CD para detectar degradaciones de rendimiento antes de cada liberación a producción.

