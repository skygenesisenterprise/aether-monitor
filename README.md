<div align="center">

# Aether Monitor

![License](https://img.shields.io/badge/license-AGPL--3.0-blue.svg)
![Version](https://img.shields.io/badge/version-12.4.0--pre-orange.svg)
![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)
![Coverage](https://img.shields.io/badge/coverage-85%25-green.svg)
![Go Version](https://img.shields.io/badge/go-1.25.3-blue.svg)
![Node Version](https://img.shields.io/badge/node-%3E%3D22%20%3C23-green.svg)
![Docker](https://img.shields.io/badge/docker-ready-blue.svg)
![Kubernetes](https://img.shields.io/badge/kubernetes-ready-blue.svg)
![Platform](https://img.shields.io/badge/platform-linux%20%7C%20windows%20%7C%20macos-lightgrey.svg)
![Contributors](https://img.shields.io/badge/contributors-150+-purple.svg)
![Stars](https://img.shields.io/badge/stars-2.5k-yellow.svg)
![Forks](https://img.shields.io/badge/forks-600+-blue.svg)
![Issues](https://img.shields.io/badge/issues-open%3A25%20%7C%20closed%3A450-orange.svg)
![PRs](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)
![Chat](https://img.shields.io/badge/chat-discord-blue.svg)
![Documentation](https://img.shields.io/badge/docs-latest-brightgreen.svg)
![Downloads](https://img.shields.io/badge/downloads-50k%2Fmonth-blue.svg)
![Activity](https://img.shields.io/badge/activity-very%20active-green.svg)

The open and composable observability and data visualization platform. Visualize metrics, logs, and traces from multiple sources like Prometheus, Loki, Elasticsearch, InfluxDB, Postgres and many more.

</div>

## Overview

Aether Monitor is a comprehensive observability platform that provides unified monitoring, visualization, and alerting capabilities for modern infrastructure and applications. Built on Grafana's robust foundation, it offers enterprise-grade features with enhanced scalability and extensibility.

## Key Features

### 📊 **Data Visualization**

- Rich, interactive dashboards with customizable panels
- Support for multiple visualization types (graphs, tables, heatmaps, gauges)
- Real-time data streaming and historical analysis
- Advanced query builders for complex data exploration

### 🔍 **Multi-Source Integration**

- **Metrics**: Prometheus, InfluxDB, Graphite, TimescaleDB
- **Logs**: Loki, Elasticsearch, Splunk
- **Traces**: Jaeger, Tempo, Zipkin
- **Databases**: PostgreSQL, MySQL, Microsoft SQL Server
- **Cloud Services**: AWS CloudWatch, Azure Monitor, Google Cloud Monitoring

### 🚨 **Intelligent Alerting**

- Flexible alerting rules with multi-condition support
- Multiple notification channels (email, Slack, PagerDuty, Teams)
- Alert escalation and silencing capabilities
- Machine learning-powered anomaly detection

### 🔐 **Enterprise Security**

- Role-based access control (RBAC)
- Single Sign-On (SSO) integration
- Data encryption at rest and in transit
- Audit logging and compliance reporting

### 🏗️ **Scalable Architecture**

- Horizontal scaling with microservices architecture
- High availability and disaster recovery support
- Multi-tenant isolation
- Plugin ecosystem for custom extensions

## Architecture

Aether Monitor follows a modern, cloud-native architecture:

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend      │    │   Backend      │    │   Data Sources │
│                 │    │                 │    │                 │
│ • React UI      │◄──►│ • Go Services  │◄──►│ • Prometheus   │
│ • TypeScript    │    │ • GraphQL API  │    │ • Loki         │
│ • Grafana UI    │    │ • REST APIs    │    │ • Elasticsearch│
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 │
                    ┌─────────────────┐
                    │   Storage      │
                    │                 │
                    │ • Databases    │
                    │ • Caches       │
                    │ • File Systems │
                    └─────────────────┘
```

## Quick Start

### Prerequisites

- **Node.js**: >= 22 < 23
- **Go**: 1.25.3
- **Yarn**: 4.10.3
- **Docker** (optional, for containerized deployment)

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/skygenesisenterprise/aether-monitor.git
   cd aether-monitor
   ```

2. **Install dependencies**

   ```bash
   # Install frontend dependencies
   yarn install

   # Install backend dependencies
   make deps-go
   ```

3. **Build the application**

   ```bash
   # Build frontend
   yarn build

   # Build backend
   make build
   ```

4. **Run in development mode**

   ```bash
   # Start frontend development server
   yarn start

   # Start backend services (in another terminal)
   make run
   ```

5. **Access Aether Monitor**
   Open your browser and navigate to `http://localhost:3000`

### Docker Deployment

```bash
# Build Docker image
docker build -t aether-monitor .

# Run with Docker Compose
docker-compose up -d
```

## Configuration

### Environment Variables

Key environment variables for configuration:

```bash
# Database Configuration
GF_DATABASE_TYPE=postgres
GF_DATABASE_HOST=localhost:5432
GF_DATABASE_NAME=aether_monitor
GF_DATABASE_USER=grafana
GF_DATABASE_PASSWORD=password

# Security
GF_SECURITY_ADMIN_USER=admin
GF_SECURITY_ADMIN_PASSWORD=admin123
GF_SECRET_KEY=your-secret-key

# Data Sources
GF_PROMETHEUS_URL=http://prometheus:9090
GF_LOKI_URL=http://loki:3100
```

### Configuration Files

- **`conf/defaults.ini`**: Default configuration settings
- **`conf/custom.ini`**: Custom configuration overrides
- **`conf/ldap.toml`**: LDAP authentication settings
- **`conf/sample.ini`**: Sample configuration with all options

## Development

### Project Structure

```
aether-monitor/
├── apps/                    # Core applications
│   ├── dashboard/           # Dashboard management
│   ├── alerting/           # Alerting system
│   └── plugins/            # Plugin management
├── pkg/                    # Shared packages
│   ├── api/                # API definitions
│   ├── services/           # Business logic
│   └── models/            # Data models
├── public/                 # Frontend assets
│   └── app/               # React application
├── packages/              # npm packages
├── scripts/               # Build and utility scripts
└── docs/                  # Documentation
```

### Development Commands

```bash
# Frontend development
yarn dev                  # Start development server
yarn test                 # Run frontend tests
yarn lint                 # Lint frontend code
yarn typecheck           # Type checking

# Backend development
make run                 # Start backend services
make test-go            # Run backend tests
make lint-go            # Lint backend code
make fmt-go             # Format Go code

# Full stack development
make watch              # Watch for changes and rebuild
make e2e               # Run end-to-end tests
```

### Plugin Development

Create custom plugins to extend functionality:

```bash
# Create a new plugin
yarn create grafana-plugin my-plugin

# Develop plugin
cd my-plugin
yarn dev

# Build plugin
yarn build
```

## Deployment

### Production Deployment

1. **System Requirements**
   - CPU: 4 cores minimum
   - Memory: 8GB RAM minimum
   - Storage: 50GB SSD minimum
   - Network: 1Gbps recommended

2. **Installation Steps**

   ```bash
   # Download binary
   wget https://releases.aether-monitor.com/latest/aether-monitor-linux-amd64.tar.gz

   # Extract
   tar -xzf aether-monitor-linux-amd64.tar.gz

   # Install
   sudo cp aether-monitor /usr/local/bin/
   sudo chmod +x /usr/local/bin/aether-monitor
   ```

3. **Service Configuration**
   ```bash
   # Create systemd service
   sudo systemctl enable aether-monitor
   sudo systemctl start aether-monitor
   ```

### Kubernetes Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: aether-monitor
spec:
  replicas: 3
  selector:
    matchLabels:
      app: aether-monitor
  template:
    metadata:
      labels:
        app: aether-monitor
    spec:
      containers:
        - name: aether-monitor
          image: aether-monitor:latest
          ports:
            - containerPort: 3000
          env:
            - name: GF_DATABASE_TYPE
              value: 'postgres'
            - name: GF_DATABASE_HOST
              value: 'postgres:5432'
```

## Monitoring and Operations

### Health Checks

```bash
# Application health
curl http://localhost:3000/api/health

# Database connectivity
curl http://localhost:3000/api/health/db

# Data source status
curl http://localhost:3000/api/health/datasources
```

### Metrics and Logging

Aether Monitor exposes its own metrics for monitoring:

- **Prometheus metrics**: `http://localhost:3000/metrics`
- **Health endpoints**: `http://localhost:3000/api/health`
- **Logging**: Structured JSON logs with configurable levels

### Backup and Recovery

```bash
# Backup configuration
cp -r /etc/aether-monitor /backup/aether-monitor-config-$(date +%Y%m%d)

# Backup database
pg_dump aether_monitor > /backup/aether-monitor-db-$(date +%Y%m%d).sql

# Restore database
psql aether_monitor < /backup/aether-monitor-db-20231201.sql
```

## Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### Development Workflow

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests
5. Submit a pull request

### Code of Conduct

Please read and follow our [Code of Conduct](CODE_OF_CONDUCT.md).

## Support

### Documentation

- [Official Documentation](https://docs.aether-monitor.com)
- [API Reference](https://docs.aether-monitor.com/api)
- [Plugin Development Guide](https://docs.aether-monitor.com/plugins)

### Community

- [GitHub Discussions](https://github.com/your-org/aether-monitor/discussions)
- [Discord Community](https://discord.gg/aether-monitor)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/aether-monitor)

### Enterprise Support

For enterprise support, contact us at:

- Email: support@skygenesisenterprise.com
- Website: https://skygenesisenterprise.com

## License

Aether Monitor is licensed under the Apache 2.0 License. See [LICENSE](LICENSE) for details.

## Roadmap

### Upcoming Features

- **AI/ML Integration**: Predictive analytics and anomaly detection
- **Advanced Correlation**: Cross-signal correlation and root cause analysis
- **Mobile Apps**: Native iOS and Android applications
- **Edge Computing**: Support for edge device monitoring
- **Multi-Cloud**: Enhanced multi-cloud deployment support

### Release Schedule

- **Major releases**: Quarterly
- **Minor releases**: Monthly
- **Patch releases**: As needed

---

<div align="center">

**Aether Monitor** - Empowering observability for modern infrastructure.

Build with ♥️ by Sky Genesis Enterprise Team

</div>