Claude Code Best V3 (CCB)
An unofficial, open-source project aimed at decompiling and reverse-engineering Anthropic's official Claude Code CLI tool. The goal is to replicate most of Claude Code's functionalities and engineering capabilities.
Documentation and PR Submissions Here
📌 Project Roadmap
 * [x] V1: Successfully run the project and pass basic type checking.
 * [x] V2: Complete engineering infrastructure.
   * Biome formatting is postponed to avoid code conflicts.
   * Build pipeline is complete; outputs run on both Node.js and Bun.
 * [x] V3: Extensive documentation and website improvements.
 * [ ] V4: Implement massive test coverages to improve stability.
⚠️ Important Notes from the Maintainer
 * Repo Lifespan: It is uncertain how long this project will stay up. Starring, forking, git clone, or downloading the .zip is highly recommended.
 * Contributions: The codebase updates rapidly (powered by Opus), so while issues are welcome, Pull Requests (PRs) are not accepted at the moment.
 * Donations: Over $800 has been spent on Claude API so far. If you wish to sponsor personally, please donate to any charity and post the receipt in the issues. For corporate sponsors (offering $10k+ API quotas), please email claude-code-best@proton.me to be featured on the sponsor list.
⏱️ Survival Log
 * 24 Hours: Surpassed 6k Stars. V3 documentation site completed. Moving to V4 (Testing). Still no takedown notice from Anthropic.
 * 15 Hours: Node.js support added to build output. Approaching 3k Stars.
 * 12 Hours: April Fools' Day. Broke 1k Stars.
 * Consulting: For private consulting, email claude-code-best@proton.me.
🚀 Quick Start
Prerequisites
You must use the latest version of Bun to avoid bugs. Run bun upgrade.
 * Bun >= 1.3.11
 * Standard Claude Code configuration methods apply (Providers have their own setups).
Installation & Execution
# Install dependencies
bun install

# Run in Development mode (If you see version 888, it's correct)
bun run dev

# Build the project
bun run build

Note: The build uses code splitting (build.ts) and outputs to the dist/ directory (dist/cli.js + approx. 450 chunks). The built artifacts can run natively on both Bun and Node.js.
🛠️ Capability Checklist
(✅ = Implemented | ⚠️ = Partially Implemented / Conditional | ❌ = Stub / Removed / Disabled)
Core System
 * ✅ REPL Interface: Full terminal interaction via Ink.
 * ✅ API Communication: Supports Anthropic Direct, AWS Bedrock, Google Vertex, and Azure Foundry.
 * ✅ Query Engine: Full chat engine, tool loops, auto-compaction, token tracking.
 * ✅ Context Building: git status, CLAUDE.md, memory integration.
 * ✅ Permission System: Plan/Auto/Manual modes with YOLO classifiers.
 * ✅ Hooks System: Pre/post tool use hooks via settings.json.
 * ✅ Session Management: Resume conversations (/resume), diagnostics (/doctor).
Tools
 * ✅ Always Available: BashTool, FileRead/Write/Edit, WebFetch/Search, AskUserQuestion, SendMessage, AgentTool (sub-agents), Cron jobs, Worktree tools.
 * ⚠️ Conditionally Enabled: Glob/Grep (default on), Task creation (if V2 enabled), Team management, LSPTool (via env var).
 * ❌ Disabled via Feature Flags: Sleep, RemoteTrigger, Monitor, WebBrowser, PushNotifications, etc.
 * ❌ Stub / Unavailable: TungstenTool, REPLTool, ReviewArtifactTool.
Slash Commands
 * ✅ Available: /add-dir, /agents, /branch, /clear, /compact, /config, /cost, /diff, /doctor, /effort, /export, /help, /login, /mcp, /memory, /model, /plan, /review, /tasks, /theme, etc.
 * ❌ Disabled (Feature Flagged): /voice, /proactive, /brief, /remote-control, /workflows, /subscribe-pr, etc.
 * ❌ Anthropic-Only (Unavailable): /files, /tag, /issue, /onboarding, /teleport, /env, etc.
CLI Subcommands
 * ✅ Available: claude (REPL), mcp, auth, plugin, setup-token, agents, doctor, update, install.
 * ❌ Disabled: server, ssh, open, auto-mode, remote-control, assistant, plus internal ANT commands (up, log, etc.).
Services & Internal Packages (packages/)
 * ✅ Services: API Clients, MCP, OAuth, Plugins, Session Memory, Skill Search, Policy Limits.
 * ✅ Native Implementations: color-diff-napi, audio-capture-napi (SoX/arecord), image-processor-napi (macOS), @ant/computer-use-input (AppleScript/JXA), @ant/computer-use-swift.
 * ❌ Stubs: url-handler-napi, @ant/claude-for-chrome-mcp.
⚙️ Technical Details & Feature Flags
Project Structure
Uses a Monorepo setup via Bun workspaces. Previously missing stubs have been moved to packages/ and resolved via workspace:*.
Runtime Polyfills
The entry point (src/entrypoints/cli.tsx) injects necessary polyfills. feature() always returns false to bypass unimplemented paths, and globalThis.MACRO simulates build-time macro injections.
🚩 Feature Flags Explained (All set to false)
Original Claude Code uses A/B testing flags. In this project, all 31 flags are disabled.
 * Autonomous Agents: KAIROS (Background Agent), PROACTIVE, COORDINATOR_MODE, BUDDY, FORK_SUBAGENT.
 * Remote/Distributed: BRIDGE_MODE (Remote control), DAEMON, BG_SESSIONS, SSH_REMOTE, DIRECT_CONNECT.
 * Enhanced Tools: CHICAGO_MCP (Computer Use), WEB_BROWSER_TOOL, VOICE_MODE, WORKFLOW_SCRIPTS.
 * Dialog & Infrastructure: HISTORY_SNIP, ULTRAPLAN, TRANSCRIPT_CLASSIFIER, UPLOAD_USER_SETTINGS.
📜 License
This project is strictly for educational and research purposes. All rights to Claude Code belong to Anthropic.
