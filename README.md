# Grafana Cursor Plugin

Cursor Marketplace plugin that exposes the official [Grafana MCP server](https://github.com/grafana/mcp-grafana) for AI-assisted observability workflows.

## Getting started

1. [Docker](https://docs.docker.com/get-docker/) must be installed and running.

2. Create a [service account](https://grafana.com/docs/grafana/latest/administration/service-accounts/) in Grafana with at least **Viewer** role (or **Editor** for write operations). Generate a token.

3. Set environment variables:

   ```bash
   export GRAFANA_URL="http://localhost:3000"
   export GRAFANA_SERVICE_ACCOUNT_TOKEN="<your token>"
   ```

   For Grafana Cloud, use your instance URL instead (e.g. `https://myinstance.grafana.net`).

4. Install the plugin from the Cursor Marketplace.

## What's included

- **MCP server** (`mcp.json`) — runs the official `grafana/mcp-grafana` Docker image in stdio mode, providing 40+ tools for dashboards, datasources, Prometheus, Loki, alerting, incidents, OnCall, annotations, and more.
- **Rule** (`rules/grafana-assistant.mdc`) — best practices for using Grafana MCP tools effectively (context window management, write safety, deeplinks).

See [plugins/grafana/README.md](plugins/grafana/README.md) for the full tool reference.

## Development

To validate the plugin structure:

```bash
node scripts/validate-template.mjs
```

To add more plugins, create a new directory under `plugins/` and register it in `.cursor-plugin/marketplace.json`. See `docs/add-a-plugin.md` for details.
