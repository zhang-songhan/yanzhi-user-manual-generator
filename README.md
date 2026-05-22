# yanzhi-user-manual-generator

A Claude Code plugin that generates friendly user manuals from source codes or spec documents.

## Installation

In Claude Code, run:

```
/plugin https://github.com/zhang-songhan/yanzhi-user-manual-generator
```

## Skills

### writing-user-manual

Generate or update a structured Markdown user manual from project source code or spec documents.

- Analyzes codebase to extract feature modules and workflows
- Produces a complete manual with product overview, feature descriptions, step-by-step instructions, and screenshot placeholders (`【图X：...】`)
- Supports **create** mode (new manual) and **update** mode (refresh existing manual)

**Trigger keywords:** `user manual`, `user guide`, `用户手册`, `使用手册`, `用户指南`, `update manual`, `更新手册`

### auto-capture

Automatically capture real screenshots for every placeholder in a user manual by interactively navigating the running application.

Uses a **snapshot-analyze-act** loop — reads the current screen, decides what to click, verifies the result — never a blind script.

Four capture modes:

| Mode | Platform | Method |
|------|----------|--------|
| Browser | Web apps | Playwright MCP |
| Windows native | WPF / WinForms | pywinauto |
| macOS native | Cocoa / AppKit | osascript (AppleScript) |
| Guided desktop | Linux / fallback | Step-by-step user guidance |

**Trigger keywords:** `auto capture`, `take screenshots`, `fill screenshots`, `截图`, `自动截图`

### generating-html-manual

Convert a Markdown user manual into a standalone, styled HTML page with sidebar navigation and company branding.

Features:

- Left sidebar TOC with active heading tracking
- Responsive layout (desktop, tablet, mobile)
- Company logo in header and footer
- Back-to-top button
- Print-optimized stylesheet
- Single `index.html` output — ready to distribute

**Trigger keywords:** `HTML manual`, `convert to HTML`, `生成HTML手册`, `转HTML`, `HTML版本`

## Typical Workflow

```
1. /writing-user-manual   →  Generate Markdown manual with screenshot placeholders
2. /auto-capture          →  Fill placeholders with real screenshots from the running app
3. /generating-html-manual →  Convert to a polished standalone HTML page
```

## License

MIT
