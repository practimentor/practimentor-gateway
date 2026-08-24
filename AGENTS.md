# AGENTS.md — utp-agent-gateway

API Gateway del proyecto **utp-agent**. C# .NET 10 con **YARP**
(*Yet Another Reverse Proxy*).

> **Estado: no iniciado.** Es un objetivo **opcional del Sprint 4**, a evaluar al
> cerrar el Sprint 3. Mientras tanto, el `Ingress` de Kubernetes hace el
> enrutamiento y los Route Handlers de Next.js hacen de BFF.
>
> **No empieces a trabajar aquí sin que André lo confirme.**

## Git lo ejecuta la persona, no tú

No ejecutes `git add`, `commit`, `push`, `pull`, `merge`, `rebase`, `reset` ni
`checkout` por tu cuenta. Puedes leer con `status`, `log`, `diff` y `show`.

Cuando haga falta una operación de escritura, escribe el comando exacto y
completo, listo para copiar, con el mensaje de commit ya redactado, y explica en
una línea qué hace. Solo ejecútalos tú si la persona te lo pide explícitamente.

## Qué haría este servicio

Puerta única de entrada al sistema:

- Enrutar cada petición al servicio que corresponde
- Validar el token de Keycloak **una sola vez**, en lugar de en cada servicio
- Aplicar límites de tasa
- Ocultar la topología interna: el navegador solo conoce una URL

## Qué NO le corresponde

- **No contiene lógica de negocio.** Solo enruta y valida.
- **No habla con bases de datos.**
- **No transforma respuestas.** Eso sería trabajo del BFF.

## Comandos

```bash
dotnet restore
dotnet build
dotnet run
```

## Convenciones

**Estrategia de ramificación: GitHub Flow con ramas personales.** `main` es la
única rama permanente compartida y siempre debe quedar ejecutable. No existe rama
`develop`. Cada integrante trabaja en su rama propia `dev/<nombre>`, que **no se
borra** al fusionar. Antes de cada tarea nueva se trae `main` a la rama propia.
Un Pull Request **por tarea**, con `Closes #NN`. Detalle completo en el ADR
2026-08-23-02 del repo `utp-agent-platform`.

- Tu rama: `dev/<tu-nombre>`. Nunca trabajes sobre `main`
- Commits convencionales con ámbito `gateway`: `feat(gateway): ...`

## Prohibido sin confirmación explícita

- No iniciar el desarrollo sin confirmación de André.
- No agregar ni actualizar paquetes NuGet.
- No modificar workflows de `.github/`.
- Si crees que necesitas hacer algo de esta lista, detente y comenta en el issue.
