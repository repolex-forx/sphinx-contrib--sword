# Repolex Knowledge Graph of sphinx-contrib/sword

RDF knowledge graph data for [sphinx-contrib/sword](https://github.com/sphinx-contrib/sword), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download sphinx-contrib/sword
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 4d304290ae46bcd01bba63888c36d3d503112acd
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 4d304290ae46bcd01bba63888c36d3d503112acd
│           └── chunk-001.nq.gz
├── blob
│   ├── 09206c4bb2901779e7f22a91e0f03c50a63ecda9.nq.gz
│   ├── 2c9b242cb57358dccf889caf8f9a6c8a64757227.nq.gz
│   ├── 2d74c58f248790e34e482eb07e20ec6c753c9d2d.nq.gz
│   ├── 45dd5f5b51e10661a6b6699e050c4ab23d721804.nq.gz
│   ├── 477c43f3ef6eb313518eab3331cc11de45469efc.nq.gz
│   ├── 62ddeb71ecf9d7327a0ddc375b52ba1834255986.nq.gz
│   ├── 9860de7838cf242cdeb0d3b27c05ec589f3a137c.nq.gz
│   └── b5a7dc29ef0f7f3593b1c61cfc5dfe8a17d3918c.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 4d304290ae46bcd01bba63888c36d3d503112acd.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 14 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[sphinx-contrib/sword](https://github.com/sphinx-contrib/sword)

---
*Parsed on 2026-11-07 by [repolex](https://repolex.ai)*
