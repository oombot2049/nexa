# NexaPilot Documentation

This documentation describes how to install and operate NexaPilot, how its agent runtime behaves, where its implementation boundaries lie, and which configuration and persistence contracts are stable.

## Recommended reading order

1. [Installation](getting-started/installation.md) — install dependencies and prepare local configuration.
2. [Configuration](getting-started/configuration.md) — configure providers, storage, permissions, and optional integrations.
3. [First agent run](getting-started/first-agent-run.md) — create a project and thread, run a task, and inspect the result.
4. [System overview](architecture/overview.md) — understand runtime boundaries, execution flow, and persistence.
5. [Configuration reference](reference/configuration.md) and [database schema](reference/database-schema.md) — look up exact contracts.

## Documentation map

| Directory | Content | Purpose |
| --- | --- | --- |
| `getting-started/` | Installation and first-run paths | Bring up a working local runtime |
| `concepts/` | Product and execution concepts | Explain objects, guarantees, and user-facing behavior |
| `guides/` | Feature operation and troubleshooting | Configure, use, and verify implemented capabilities |
| `architecture/` | Runtime internals and failure behavior | Describe control flow, boundaries, and source modules |
| `reference/` | Exact configuration and storage contracts | Provide authoritative values, fields, and compatibility notes |
| `examples/` | Executable datasets and configurations | Supply reproducible evaluation and gateway examples |

## System summary

NexaPilot is a local-first personal-agent runtime. A task runs inside an explicit project workspace, streams through a durable agent loop, applies permission policy before tool execution, and persists messages, events, attempts, and results in SQLite. The same runtime is available through the Web console, CLI, and REST API.

## Implementation boundaries

- Implemented: durable runs, provider routing, permission-aware tools, memory, subagents, scheduled tasks, MCP and Skills, evaluation, and local Web/CLI/API surfaces.
- Optional adapters: Daytona, Feishu, Langfuse, Tavily, external knowledge bases, and MCP servers.
- Deployment model: a trusted local operator; the repository does not provide a hosted multi-tenant control plane.
- Sources of truth: source code, configuration parsing, API schemas, migrations, and tests take precedence over prose when behavior changes.

## Getting started

- [Installation](getting-started/installation.md) — install dependencies and prepare local configuration.
- [Configuration](getting-started/configuration.md) — configure a provider, storage, permissions, and optional features.
- [First agent run](getting-started/first-agent-run.md) — create a project and thread, run a task, and inspect the result.

## Concepts

- [Projects, threads, and runs](concepts/projects-threads-runs.md)
- [Tools, policy, and permission](concepts/tools-policy-permission.md)
- [Memory and context](concepts/memory-and-context.md)

Concept pages explain what an object means and why it exists. They intentionally avoid database and implementation detail.

## Guides

- [CLI](guides/cli.md)
- [Memory](guides/memory.md)
- [Subagents](guides/subagents.md)
- [MCP and Skills](guides/mcp-and-skills.md)
- [Agent evaluation](guides/evaluation.md)

Guides explain how to configure, operate, verify, and troubleshoot an implemented capability.

## Architecture

- [System overview](architecture/overview.md)
- [Agent loop](architecture/agent-loop.md)
- [Context and Memory](architecture/context-and-memory.md)
- [Tool execution](architecture/tool-execution.md)
- [Persistence and events](architecture/persistence-and-events.md)
- [Model routing and fallback](architecture/model-routing-and-fallback.md)

Architecture pages describe runtime boundaries, control flow, failure behavior, and relevant source modules.

## Reference

- [Configuration reference](reference/configuration.md)
- [Database schema](reference/database-schema.md)
- [Provider compatibility](reference/provider-compatibility.md)

Reference pages list precise values and contracts. Source code and tests remain authoritative when a document becomes stale.

## Executable examples

- [Evaluation datasets and fixtures](examples/README.md)

## Documentation rules

- Describe implemented behavior, not roadmap ideas.
- Link to one authoritative explanation instead of copying it between pages.
- Put commands and expected outcomes in guides; put exhaustive fields and values in reference pages.
- Never include API keys, personal paths, private repository names, or runtime data.
