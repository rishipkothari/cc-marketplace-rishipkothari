# cc-marketplace-rishipkothari

A Claude plugin marketplace that lists my custom Claude plugins. Each plugin lives in its own repo; this repo only holds the catalog (`.claude-plugin/marketplace.json`).

## Plugins

| Plugin | Repo | What it does |
| :- | :- | :- |
| `stack-playbook` | [rishipkothari/dev-stack-playbook](https://github.com/rishipkothari/dev-stack-playbook) | Interactive, learning-oriented walkthrough for choosing, setting up and tracking a project's tech stack |

## Install

**claude.ai / Claude Desktop** (saved to your account; also syncs to Cowork and to Claude Code when signed in with the same account):

1. **Customize** → **Plugins** → **Add** → **Add marketplace** → **Add from a repository**.
2. Enter `rishipkothari/cc-marketplace-rishipkothari`.
3. Install the plugins you want.

**Claude Code** (per device):

```
/plugin marketplace add rishipkothari/cc-marketplace-rishipkothari
/plugin install stack-playbook@rishipkothari-plugins
```

Turn on auto-update in `/plugin` → **Marketplaces** → `rishipkothari-plugins` → **Enable auto-update**, or update manually with `/plugin marketplace update rishipkothari-plugins`.

## Adding a plugin

1. Create the plugin's own repo with `.claude-plugin/plugin.json` (leave out `version` so every commit to `main` is picked up) and its `skills/`.
2. Add an entry to `plugins` in `.claude-plugin/marketplace.json`:
   ```json
   { "name": "<plugin-name>", "source": { "source": "github", "repo": "rishipkothari/<repo>" }, "description": "…" }
   ```
   The entry's `name` must match the `name` in the plugin's `plugin.json`.
3. Validate with `claude plugin validate .` and push to `main`.
