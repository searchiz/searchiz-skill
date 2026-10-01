# searchiz-skill

The [searchiz-audit](https://github.com/searchiz/searchiz-audit) checks as an
agent skill and plugin: your coding agent audits whether AI search can read the
site this repository publishes, applies the fixes that need no facts from you,
and opens a pull request. It never invents business facts; anything only you
know is listed in the pull request instead.

## Install

**Claude Code**

```
/plugin marketplace add searchiz/searchiz-skill
/plugin install searchiz-audit@searchiz
```

**Codex and ChatGPT desktop** (repo marketplace)

```sh
codex plugin marketplace add searchiz/searchiz-skill
```

**Cursor**: copy `.cursor/rules/searchiz-audit.mdc` into your project's
`.cursor/rules/`, then ask "run the searchiz audit".

**OpenClaw and other Agent Skills hosts**: copy `skills/searchiz-audit/` into
your skills folder.

Then ask your agent: "Audit this site for AI search and open a PR with the
fixes."

## What happens

1. The agent finds the site URL (CNAME, package.json, site config) or asks.
2. It runs `npx -y github:searchiz/searchiz-audit <url> --format json`.
3. It applies the robots.txt and canonical fixes, fills structured data and
   meta description only with facts already in the repository, and lists what
   is missing.
4. It opens a pull request with the score, each change and the evidence from
   the pages AI answers cite most.

Requirements: Node 20+, and the GitHub CLI (`gh`) to open the pull request.
No account, no telemetry.

## Scope

Free and open, not a product: no support promise. Issues about wrong results
are welcome.

Open source tells you what could be wrong. Searchiz tells you whether AI
actually recommends you, and fixes it: [searchiz.com](https://searchiz.com).

## License

MIT
