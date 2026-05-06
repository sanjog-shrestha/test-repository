# 🔗 Zapier MCP + GitHub + VS Code

> Automate GitHub workflows using natural language — directly from your code editor via Zapier MCP.

<!-- BANNER IMAGE: Replace with a screenshot of your VS Code + Zapier MCP setup in action -->
![Project Banner](images/banner.png)

---

## 📋 Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Setup](#setup)
  - [1. Connect Zapier MCP to VS Code](#1-connect-zapier-mcp-to-vs-code)
  - [2. Add GitHub as a connected app](#2-add-github-as-a-connected-app)
  - [3. Configure Claude Code (alternative)](#3-configure-claude-code-alternative)
- [Usage](#usage)
- [Example Prompts](#example-prompts)
- [Troubleshooting](#troubleshooting)
- [Resources](#resources)

---

## Overview

This project demonstrates how to connect **Zapier MCP** (Model Context Protocol) to **VS Code** and **Claude Code**, enabling your AI assistant to interact with GitHub — creating issues, adding labels, listing PRs, and more — using plain English prompts.

No API keys. No custom scripts. Just natural language → real GitHub actions.

```
You  →  VS Code / Claude Code  →  Zapier MCP  →  GitHub API
```

<!-- ARCHITECTURE DIAGRAM: Replace with a diagram showing the flow: VS Code → Zapier MCP → GitHub -->
![Architecture Diagram](images/architecture.png)

---

## Prerequisites

| Requirement | Version | Notes |
|---|---|---|
| VS Code | 1.85+ | Any edition |
| Node.js | 18+ | Required for MCP runtime |
| Zapier account | Free tier OK | [zapier.com](https://zapier.com) |
| GitHub account | Any | Needs a test repository |
| Claude Code | Latest | Optional — alternative to Copilot Chat |

---

## Setup

### 1. Connect Zapier MCP to VS Code


**Option A — One-click (recommended):**

1. Go to [mcp.zapier.com](https://mcp.zapier.com)
2. Click **+ New MCP Server**
3. Select **Visual Studio Code** from the agents list
4. Click the purple **"Add to Visual Studio Code"** button
VS Code will open automatically and add the configuration for you.

**Option B — Manual configuration:**

Press `Cmd+Shift+P` (Mac) or `Ctrl+Shift+P` (Windows/Linux), then run:

```
MCP: Open User Configuration
```

Paste the following:

```json
{
  "servers": {
    "Zapier": {
      "url": "https://mcp.zapier.com/api/v1/connect"
    }
  }
}
```

> **Note:** No API key is required. Zapier authenticates via your browser session on first connect.

---

### 2. Add GitHub as a connected app

<!-- SCREENSHOT: The "Apps" tab on your Zapier MCP server page — click "Add app" and search GitHub -->
<img width="1578" height="682" alt="image" src="https://github.com/user-attachments/assets/ac2dfb3d-ae7b-4a73-bafe-ffea9f370f89" />


1. On [mcp.zapier.com](https://mcp.zapier.com), click the **Apps** tab
2. Click **"Add app"** → search for **GitHub**
3. Click **"Connect GitHub"** and authorize Zapier in the popup
4. GitHub actions are now available as MCP tools

<!-- SCREENSHOT: GitHub listed as a connected app with available tools shown -->
---

## Usage

Once connected, open your AI chat panel in VS Code and use natural language:

<!-- SCREENSHOT: VS Code AI chat panel showing a successful @zapier tool call response -->
<img width="1578" height="682" alt="image" src="https://github.com/user-attachments/assets/62d1216d-6606-46d5-a055-1b83f924209c" />


```
list all available zapier tools
```

```
@zapier create a GitHub issue in my-org/my-repo titled "Login bug" with label bug
```

```
@zapier list all open issues in my-org/my-repo
```

```
@zapier close issue #5 in my-org/my-repo and add comment "Fixed in v1.2"
```

<img width="1691" height="742" alt="image" src="https://github.com/user-attachments/assets/d7aed2ae-e4e2-4982-bbf9-cf2fef3982ef" />


---

## Example Prompts

| What you want | Prompt |
|---|---|
| Create an issue | `@zapier create issue in owner/repo titled "X" with label bug` |
| List open issues | `@zapier list open issues in owner/repo` |
| Add a label | `@zapier add label "urgent" to issue #3 in owner/repo` |
| Close an issue | `@zapier close issue #7 in owner/repo` |
| List available tools | `@zapier list all available GitHub tools` |
| Multi-app action | `@zapier create a GitHub issue and send a Slack message with the link` |

---

## Troubleshooting

<!-- SCREENSHOT: The History tab on mcp.zapier.com showing MCP call logs with inputs and outputs -->
![Zapier History Tab](images/troubleshoot-history.png)

**MCP server not showing up in VS Code**
- Run `Cmd+Shift+P` → `MCP: List Servers` to verify the connection
- Restart VS Code after adding the config

**Auth prompt on first use**
- A browser tab will open asking you to log in to Zapier — complete the login and return to VS Code

**`@zapier` not recognized in Claude Code**
- Make sure you edited `~/.claude/settings.json` (not `.vscode/mcp.json`)
- Claude Code and VS Code Copilot Chat use separate MCP configs

**Action failed or returned an error**
- Check the **History tab** on [mcp.zapier.com](https://mcp.zapier.com) for full input/output logs

---

## Resources

- [Zapier MCP documentation](https://zapier.com/mcp)
- [VS Code MCP support](https://code.visualstudio.com/docs/copilot/chat/mcp-servers)
- [Claude Code documentation](https://docs.anthropic.com/claude-code)
- [GitHub REST API reference](https://docs.github.com/en/rest)

---

## License
Sanjog Shrestha
MIT © 2026
