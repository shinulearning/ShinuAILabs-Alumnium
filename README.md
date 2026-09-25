# ShinuAILabs-Alumnium

AI-native E2E testing **layered on top of the Playwright, Selenium, and Appium suites you already have** — describe steps in natural language, keep your framework.

<p align="center"><b>🚧 Shinu AI Labs Edition</b> — maintained study & enhancement fork of <a href="https://github.com/alumnium-hq/alumnium">alumnium-hq/alumnium</a> (MIT).</p>

---

## Why This Repo Exists

Most "AI testing" tools ask you to throw away your existing suite and start from agent-first chaos. **Alumnium takes the opposite path** — and we think that's the right one for enterprises:

1. **Keep** your existing Playwright / Selenium / Appium tests and CI
2. **Layer** natural-language actions and checks (`al.do(...)`, `al.check(...)`) on top
3. **Adopt AI incrementally** — one test step at a time, with framework-level control retained

This aligns with Shinu AI Labs' core philosophy:

> **The tools execute. Engineering judgment decides.**

Every AI-generated action/check remains reviewable, cacheable, and governed — AI proposes, engineers dispose.

## What's Inside (from upstream Alumnium)

| Component | Description |
|---|---|
| **Client libraries** | Java, Python, TypeScript — wrap your existing driver |
| **MCP Server** | Connect Claude Code, Codex, Cursor as agentic testing clients |
| **Markdown Test Runner** | Write scenarios in Markdown, execute locally or in CI |
| **Accessibility-tree engine** | Compact UI representation → LLM → deterministic browser actions |
| **Element & response cache** | Warm-cache replays need zero new LLM requests |
| **Vision support** | For checks that need "looking", not just accessibility trees |

## Quick Start (TypeScript + Playwright)

```typescript
import { test } from "@playwright/test";
import { Alumni } from "alumnium";

test.describe("YouTube Search", async () => {
  let al: Alumni;

  test.beforeEach(async ({ page }) => {
    al = new Alumni(page);
  });

  test.afterEach(async () => {
    await al.quit();
  });

  test("searches videos", async ({ page }) => {
    await page.goto("https://youtube.com");
    await al.do("search for 'lofi beats' and press Enter");
    await al.check("page title contains 'lofi beats'");
    await al.check("search results contain lofi videos");
  });
});
```

Works identically in **Python**, **Java** (JUnit 5), and via **MCP** for coding agents.

## Shinu AI Labs Track (Coming)

This fork will progressively add:

- **Governance patterns** — human-in-the-loop gates around AI test decisions
- **Indian enterprise examples** — compliance-heavy test scenarios
- **Cost analysis** — LLM token economics vs manual maintenance savings
- **Hybrid locator strategy** — Gherkin-style intent meets stable selectors
- **Case studies** — real runs documented in `docs/case-studies/`

## Attribution

Based on the original **Alumnium** by [alumnium-hq](https://github.com/alumnium-hq/alumnium), MIT license.
Shinu AI Labs edition — adaptations and additions follow the same MIT license.

## Connect

- 📄 Portfolio: [shinuailabs.com](https://shinuailabs.com)
- 💼 [LinkedIn — Shinoj K Narayan](https://linkedin.com/in/shinoj-narayan)
- ✉️ shinulearning@gmail.com

---

*Part of the Shinu AI Labs open-source initiative: practical AI-native engineering, India-first, built in public.*
