# LLM Help

A self-discoverable, hierarchical help system that lets LLMs browse context-aware documentation to solve wiki-specific tasks autonomously.

## How it works

The plugin provides a single MCP tool `llm_help` that LLMs call to navigate a tree of help pages:

- `llm_help()` — returns top-level help categories
- `llm_help("data-model")` — navigates deeper into a category
- `llm_help("data-model/person/create")` — reaches a specific help page

Each level returns child topics with descriptions, so the LLM decides where to go based on its current task. Help pages can contain dynamic content — rendered at call time from the wiki's live state.

## Key features

- **Hierarchical navigation** — help pages organized in a tree of any depth
- **Dynamic content** — pages rendered as wikitext at call time, pulling live data from the wiki
- **Context-aware** — pages can be scoped to specific contexts (e.g., an appify app)
- **Multi-path mounting** — same page reachable from multiple paths in the tree
- **Plugin-extensible** — any plugin can contribute help pages via tagged tiddlers
- **User shortcuts** — users can add quick-reference help pages via the settings UI
- **Help browser** — settings tab lets users see and navigate what the LLM sees

## For plugin authors

To add help pages from your plugin, create shadow tiddlers with:

- Tag: `$:/tags/rimir/llm-help/page`
- Field `llm-help-path`: navigation path (space-separated for multiple paths)
- Field `llm-help-description`: one-line description shown in parent listings
- Optional `llm-help-sort`: numeric sort order within siblings
- Optional `llm-help-context`: space-separated context keys

## Requirements

- `$:/plugins/rimir/llm-connect` — provides the MCP tool infrastructure
- `$:/plugins/rimir/theme` — provides UI styling classes

## License

MIT
