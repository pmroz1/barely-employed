# barely-employed

Competent agent. Minimum ceremony. Mild HR exposure.

A portable skill for agents that should get the job done and sound like a coworker who has already sat through enough standups today.

- Terse replies, dry humor, occasional `xd`, `xD`, or `XDDDD`.
- Harmless typos in casual chat; exact code, commands, and technical details.
- Small working changes. No speculative architecture or comment essays.
- Skip new tests and optional test runs by default; preserve required checks.
- Reviews can start with `??????`, followed by an actual finding.
- Keep the capability. Lose the ceremony.

## The skill

[skills/barely-employed/SKILL.md](skills/barely-employed/SKILL.md) is the source of truth. It contains the whole behavior; there are no runtime dependencies, hooks, tools, or background processes. `agents/openai.yaml` supplies optional Codex UI metadata.

This follows the [Agent Skills format](https://agentskills.io/specification). Native discovery depends on the agent and its settings. Any agent that can read Markdown can use the instructions, but no file can force every host or model to follow them identically.

## Install

Clone this repo, then copy the **whole** `skills/barely-employed` folder to one of these destinations. Choose a project location for one repository or a personal location for your local projects.

| Agent | Project destination | Personal destination |
| --- | --- | --- |
| [Codex](https://learn.chatgpt.com/docs/build-skills) | `.agents/skills/barely-employed/` | `~/.agents/skills/barely-employed/` |
| [Claude Code](https://code.claude.com/docs/en/skills) | `.claude/skills/barely-employed/` | `~/.claude/skills/barely-employed/` |
| [GitHub Copilot](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/add-skills) | `.github/skills/barely-employed/` | `~/.copilot/skills/barely-employed/` |
| [Cursor](https://cursor.com/docs/skills) | `.cursor/skills/barely-employed/` | `~/.cursor/skills/barely-employed/` |

For example, install for Codex in the current project with PowerShell:

```powershell
git clone https://github.com/pmroz1/barely-employed.git
New-Item -ItemType Directory -Force .agents/skills | Out-Null
Copy-Item -LiteralPath ./barely-employed/skills/barely-employed -Destination ./.agents/skills/barely-employed -Recurse
```

Or with a POSIX shell:

```sh
git clone https://github.com/pmroz1/barely-employed.git
mkdir -p .agents/skills
cp -R barely-employed/skills/barely-employed .agents/skills/
```

These examples assume the destination does not already exist. To update, replace that skill folder with the new version instead of nesting another copy inside it. Personal directories on your machine do not automatically install skills into cloud agents; use the host's supported sync or project setup.

## Use

Invoke `$barely-employed` in Codex or `/barely-employed` in Claude Code. For any host, explicitly ask:

> Read the installed barely-employed/SKILL.md and apply it to this task. Fix the duplicate save request.

For an ongoing preference, ask the agent to keep applying the skill in the session. For a persistent default, add an instruction to your host's normal project or personal instructions that tells it to read the installed file. Use a path that exists in that environment. On hosts without skill support, paste the Markdown body after the YAML header into their custom instructions.

Installing a skill makes it available; it does not guarantee activation on every turn. This repo's [AGENTS.md](AGENTS.md) asks supporting agents working here to read the canonical file. Installing elsewhere does not modify global settings.

## What it looks like

**Ordinary fix, when verified:**

> fixed the double submit. one request now, shocking concept xd
>
> build passes. tests skipped.

**A real review finding:**

> ??? this catches the error and returns success. callers think the save worked even when it didn't. return the failure here.

**A legitimate blocker:**

> can't push: this environment can't reach GitHub. changes are committed locally.

Use the tone when it fits. Do not copy a claimed result without doing the work. No joke quota, deliberate bugs, personal abuse, fake verification, or pretend-human identity. The host's instruction hierarchy and the actual task still apply.

## License

[MIT](LICENSE). Steal the vibe, ship the fix.
