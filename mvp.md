# MVP: DockTweak

**Goal:**  
Build the first practical version of DockTweak that can analyze a Dockerfile, generate a lighter and more secure version, and produce a clear report explaining the changes.

---

## Scope of the MVP

**In this phase we focus on:**
- **Input:** A single Dockerfile.
- **Processing:**
  - Static analysis of the Dockerfile using [Hadolint](https://github.com/hadolint/hadolint).
  - Rule-based optimizations (e.g., removing unnecessary layers, combining RUN commands, using smaller base images).
  - Applying a limited set of security best practices (e.g., using non-root users, avoiding secrets in images).
- **Output:**
  - An optimized Dockerfile.
  - A simple, human-readable report listing:
    - What was changed.
    - Why it improves size, performance, or security.

---

## Components

- **Core Engine:**  
  A backend service that reads the original Dockerfile, applies rules, and generates the optimized version + report.

- **API:**  
  A simple RESTful API to receive the Dockerfile and return the optimized Dockerfile + report as JSON.

- **Frontend (Optional for MVP):**  
  A minimal web UI to upload a Dockerfile and see the results. (If not included in MVP, should be part of the next milestone.)

---

## Technical Stack (suggested)

- Language: Python (FastAPI for the API)
- Linting/Analysis: Hadolint (called as a subprocess or via wrapper)
- Rule Engine: Custom Python module
- Report: Markdown or HTML generation
- (Optional) Frontend: React or simple HTML + JS page

---

## Deliverables

- `optimizer/`: Python package for optimization rules.
- `api/`: FastAPI project exposing endpoints.
- `tests/`: Unit and integration tests.
- `examples/`: Sample Dockerfiles (before and after).
- `docs/`:  
  - `mvp.md` (this document)
  - `architecture.md` (brief technical overview)
  - `README.md` (project intro, how to run, contribution guide)

---

## Testing

- Unit tests for each optimization rule.
- Integration tests covering:
  - End-to-end optimization
  - Validation of output Dockerfile correctness
  - Consistency of report generation

---

## Timeline

| Week | Task                                      |
|-----|-------------------------------------------|
| 1   | Define optimization rules & architecture  |
| 2   | Build core optimizer & basic API          |
| 3   | Integrate Hadolint & write tests          |
| 4   | Create report generator & finalize MVP    |
| 5   | Internal testing & prepare for release    |

---

## Next Steps after MVP

- Support for docker-compose files.
- Use advanced tools like DockerSlim, Dive.
- AI-based optimization suggestions.
- More detailed web dashboard.
