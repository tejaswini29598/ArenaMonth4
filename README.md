```bash
# from repository root
mvn clean install -DskipTests

# run core app module for local dev
cd erp-core
mvn spring-boot:run
```

 Local execution with H2
- Default in-memory database config is included in `erp-core/src/main/resources/application.yml`
- Access API at `http://localhost:8080/api/v1` with Basic auth credentials (hradmin/password)

  Tests

- Unit tests: `mvn test`
- Integration tests: `mvn verify -Pintegration`
- Security scan: `mvn org.owasp:dependency-check-maven:check`

 CI/CD

- JenkinsFile in `ci-cd/Jenkinsfile`
- GitHub Actions sample: `.github/workflows/ci.yml`
- Steps include build, unit tests, integration tests, security scan, docker build/push, deploy & post actions.

 Deployment

- Infra: `infrastructure/` Terraform config for cloud resources
- Container orchestration: `kubernetes/` manifests (Deployment, Service, Ingress, HPA)
- Monitoring: `monitoring/` dashboards & alerts

 Security & Compliance

- OAuth2, RBAC, Spring Security config in `erp-core/src/main/java/com/example/erp/core/security`
- Audit and GDPR/SOX/ISO support referenced in documentation
- Dependency and code scanning step in CI

Observability

- Prometheus metrics at `/actuator/prometheus`
- Health checks at `/actuator/health`
- Distributed tracing with Jaeger setup in `monitoring`
- ELK logging config for centralized logs

 Database Optimization

- Index definitions in docs
- Partitioning and replication strategy
- HikariCP connection pooling settings

Contribution

See `CONTRIBUTING.md` for coding style, PR workflow, branch strategy, and issue template details.
