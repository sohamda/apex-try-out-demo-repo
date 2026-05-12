<!-- markdownlint-disable MD033 MD041 -->

<a id="readme-top"></a>

<div align="center">

![Status](https://img.shields.io/badge/Status-In%20Progress-yellow?style=for-the-badge)
![Step](https://img.shields.io/badge/Step-2%20of%207-blue?style=for-the-badge)
![Cost](https://img.shields.io/badge/Est.%20Cost-%241%2C971%2Fmo-purple?style=for-the-badge)

# 🏗️ copilot-agent-execution-platform

**Multi-tenant SaaS for spawning isolated, ephemeral execution environments where users launch fleets of GitHub Copilot-backed custom agents that perform code edits, web search, tool/MCP calls, and script execution until a goal is reached.**

[View Architecture](#-architecture) · [View Artifacts](#-generated-artifacts) · [View Progress](#-workflow-progress)

</div>

---

## 📋 Project Summary

| Property           | Value                  |
| ------------------ | ---------------------- |
| **Created**        | 2026-05-12             |
| **Last Updated**   | 2026-05-12             |
| **Region**         | swedencentral          |
| **Environment**    | Dev                    |
| **Estimated Cost** | ~$1,971 / month (within $1,000–$5,000 envelope; Round 1 revision applied) |
| **AVM Coverage**   | TBD (Step 4)           |

---

## ✅ Workflow Progress

```text
[████░░░░░░░░░░░░░░░░] 28% Complete
```

| Step | Phase          |                                  Status                                  | Artifact                                                           |
| :--: | -------------- | :----------------------------------------------------------------------: | ------------------------------------------------------------------ |
|  1   | Requirements   |  ![Done](https://img.shields.io/badge/-Done-success?style=flat-square)   | [01-requirements.md](./01-requirements.md)                         |
|  2   | Architecture   |  ![Done](https://img.shields.io/badge/-Done-success?style=flat-square)   | [02-architecture-assessment.md](./02-architecture-assessment.md)   |
|  3   | Design         | ![Pending](https://img.shields.io/badge/-Pending-lightgrey?style=flat-square) | [03-des-\*.md](.)                                                  |
| 3.5  | Governance     | ![Pending](https://img.shields.io/badge/-Pending-lightgrey?style=flat-square) | [04-governance-constraints.md](./04-governance-constraints.md)     |
|  4   | Planning       | ![Pending](https://img.shields.io/badge/-Pending-lightgrey?style=flat-square) | [04-implementation-plan.md](./04-implementation-plan.md)           |
|  5   | Implementation | ![Pending](https://img.shields.io/badge/-Pending-lightgrey?style=flat-square) | [05-implementation-reference.md](./05-implementation-reference.md) |
|  6   | Deployment     | ![Pending](https://img.shields.io/badge/-Pending-lightgrey?style=flat-square) | [06-deployment-summary.md](./06-deployment-summary.md)             |
|  7   | Documentation  | ![Pending](https://img.shields.io/badge/-Pending-lightgrey?style=flat-square) | [07-documentation-index.md](./07-documentation-index.md)           |

> **Legend**:
> ![Done](https://img.shields.io/badge/-Done-success?style=flat-square) Complete
> | ![WIP](https://img.shields.io/badge/-WIP-yellow?style=flat-square) In Progress
> | ![Pending](https://img.shields.io/badge/-Pending-lightgrey?style=flat-square) Pending
> | ![Skip](https://img.shields.io/badge/-Skipped-blue?style=flat-square) Skipped

---

## 🏛️ Architecture

_Architecture diagram will be generated in Step 3 (Design)._

### Key Resources (preliminary)

| Resource                       | Type                          | SKU            | Purpose                                 |
| ------------------------------ | ----------------------------- | -------------- | --------------------------------------- |
| AKS                            | Microsoft.ContainerService    | TBD (Step 2)   | Sandbox runtime (kernel-isolated pods)  |
| Azure Container Registry       | Microsoft.ContainerRegistry   | Premium (PE)   | Sandbox + control-plane images          |
| Azure Container Apps           | Microsoft.App/containerApps   | Consumption    | Stateless control-plane services        |
| Azure Service Bus              | Microsoft.ServiceBus          | Standard       | Agent job queue                         |
| Azure Cosmos DB                | Microsoft.DocumentDB          | Serverless     | Agent state / chat history              |
| Azure Storage (Blob)           | Microsoft.Storage             | Standard ZRS   | Artifacts, transcripts, audit logs      |
| Azure Key Vault                | Microsoft.KeyVault            | Standard       | Tenant secrets                          |
| Azure Front Door + WAF         | Microsoft.Network             | Premium        | Public ingress + WAF                    |
| Azure Monitor + Log Analytics  | Microsoft.OperationalInsights | Pay-as-you-go  | Observability + audit                   |
| Microsoft Defender for Cloud   | Microsoft.Security            | Plan-based     | Containers / KV / Storage protection    |

---

## 📄 Generated Artifacts

<details open>
<summary><strong>📁 Step 1-3: Requirements, Architecture & Design</strong></summary>

| File                                                           | Description                                              |                                  Status                                  | Created    |
| -------------------------------------------------------------- | -------------------------------------------------------- | :----------------------------------------------------------------------: | ---------- |
| [01-requirements.md](./01-requirements.md)                     | Project requirements with NFRs                           |   ![Done](https://img.shields.io/badge/-Done-success?style=flat-square)  | 2026-05-12 |
| [02-architecture-assessment.md](./02-architecture-assessment.md) | WAF assessment, SKU recommendations, architecture diagram |   ![Done](https://img.shields.io/badge/-Done-success?style=flat-square)  | 2026-05-12 |
| [02-waf-scores.png](./02-waf-scores.png)                       | WAF pillar scores chart                                  |   ![Done](https://img.shields.io/badge/-Done-success?style=flat-square)  | 2026-05-12 |
| [03-des-cost-estimate.md](./03-des-cost-estimate.md)           | Detailed monthly cost breakdown (Azure Pricing MCP)      |   ![Done](https://img.shields.io/badge/-Done-success?style=flat-square)  | 2026-05-12 |
| [03-des-cost-distribution.png](./03-des-cost-distribution.png) | Monthly cost distribution donut                          |   ![Done](https://img.shields.io/badge/-Done-success?style=flat-square)  | 2026-05-12 |
| [03-des-cost-projection.png](./03-des-cost-projection.png)     | 6-month cost projection                                  |   ![Done](https://img.shields.io/badge/-Done-success?style=flat-square)  | 2026-05-12 |
| [02-cost-estimate.json](./02-cost-estimate.json)               | Pricing breakdown JSON (cost-estimate-subagent output)   |   ![Done](https://img.shields.io/badge/-Done-success?style=flat-square)  | 2026-05-12 |

</details>

---

## 🔗 Related Resources

| Resource            | Path                                                                                                               |
| ------------------- | ------------------------------------------------------------------------------------------------------------------ |
| **Bicep Templates** | [`infra/bicep/copilot-agent-execution-platform/`](../../infra/bicep/copilot-agent-execution-platform/) (TBD)       |
| **Workflow Docs**   | [Published workflow guide](https://jonathan-vella.github.io/azure-agentic-infraops/concepts/workflow/)             |
| **Troubleshooting** | [Published troubleshooting guide](https://jonathan-vella.github.io/azure-agentic-infraops/guides/troubleshooting/) |

---

<div align="center">

**Generated by [APEX](../../README.md)** · [Report Issue](https://github.com/jonathan-vella/azure-agentic-infraops/issues/new)

<a href="#readme-top">⬆️ Back to Top</a>

</div>
