# api-workation

A **contract-first (API-first) OpenAPI specification** repository. It contains no application
code — only the API contract that serves as the single source of truth from which an Angular
frontend and a Spring Boot (Java 21) backend are intended to be generated.

## What's in here

The deliverable is the OpenAPI spec at [`src/main/resources/api-workation.yaml`](src/main/resources/api-workation.yaml).
It defines the "Coding Challenge API" (OpenAPI 3.1.0), including the `GET /workflex/workation`
endpoint and shared schemas/responses such as `ApiError`, `BadRequest`, `NotFound` and `Conflict`.

## What it uses

- **OpenAPI 3.1.0** — the API contract itself; the single source of truth for backend and
  frontend code generation.
- **Maven** (`pom.xml`) — packages and versions the spec as a resource artifact
  (`de.workflex.api.workation:api-workation`), with resource filtering enabled.
- **release-please** (`release-please-config.json`) — automated releases and changelog
  generation (`release-type: maven`)
- **Renovate** (`renovate.json`) — automated dependency updates via the shared
  `l-bank/fiola-renovate-config`.
- **GitHub Actions** (`.github/workflows/`) — CI build (`ci-build.yaml`) and bot automation
  (`bot.yaml`).

## What it does NOT use

- **No backend implementation** — no Java source and no Spring Boot application; `pom.xml` is a
- **No backend implementation** — no Java source and no Spring Boot application; `pom.xml` is a
  packaging shell with no dependencies or compile plugins.
- **No frontend implementation** — no Angular/TypeScript source; the npm package only ships the
  YAML spec.
- **No runtime dependencies** — neither `pom.xml` declares any libraries.
- **No tests, database, or Dockerfile.**

In short: this is a **spec/contract package**, not a runnable application — the API definition
plus the release and CI tooling needed to version and distribute it.