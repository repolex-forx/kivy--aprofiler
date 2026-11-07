# Repolex Knowledge Graph of kivy/aprofiler

RDF knowledge graph data for [kivy/aprofiler](https://github.com/kivy/aprofiler), parsed by [repolex](https://repolex.ai).

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
rlex download kivy/aprofiler
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 4edbd155031ecf9113ce1d91c9cdde8ea65a0c3e
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 4edbd155031ecf9113ce1d91c9cdde8ea65a0c3e
│           └── chunk-001.nq.gz
├── blob
│   ├── 193e396ea93ec49f59f70ae9d92197bd203b29a2.nq.gz
│   ├── 3978855d6ae6d26465c5b06f6cd717e6e449f5d1.nq.gz
│   ├── b742dbe69e8f5b32d8ee9b09d731d4304535f302.nq.gz
│   ├── b9017f51981353180c35d87752e84895785c4843.nq.gz
│   └── d2d6f360b5d1ea91375f06547df0048ec47a4862.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 4edbd155031ecf9113ce1d91c9cdde8ea65a0c3e.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 11 files
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

[kivy/aprofiler](https://github.com/kivy/aprofiler)

---
*Parsed on 2026-11-07 by [repolex](https://repolex.ai)*
