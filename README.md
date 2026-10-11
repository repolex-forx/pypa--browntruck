# Repolex Knowledge Graph of pypa/browntruck

RDF knowledge graph data for [pypa/browntruck](https://github.com/pypa/browntruck), parsed by [repolex](https://repolex.ai).

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
rlex download pypa/browntruck
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 8c6db1bb2daa565c28c857e00c55fffec2626efa
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 8c6db1bb2daa565c28c857e00c55fffec2626efa
│           └── chunk-001.nq.gz
├── blob
│   ├── 1b1307e69c12e936d1b91f18e4a440a5d3c3fa53.nq.gz
│   ├── 5faa545eae38396eaee32d408a1e4c41c930e370.nq.gz
│   ├── 8dada3edaf50dbc082c9a125058f25def75e625a.nq.gz
│   ├── 91f16ae3bf973f3198d047b79fd73501bb881fda.nq.gz
│   ├── b40c44bcf116220ecdec203ff7ee9efb3f4c5ff6.nq.gz
│   ├── c6f7782f61975eb26db83a0e0f32e62ec86d4b1e.nq.gz
│   ├── d14446d9388530344111e3f9ee77324b5a0d231e.nq.gz
│   ├── e76113b48d064cf85948d7753ab2ca3c39e40c2f.nq.gz
│   ├── f3ac32e3debe76316ace8af46014efbafc9835b8.nq.gz
│   ├── f8803e5d384907e71602f65c8097922eda72c52d.nq.gz
│   └── fd00253afbeb1186d87e7fd8632c097368bb632a.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 8c6db1bb2daa565c28c857e00c55fffec2626efa.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 19 files
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

[pypa/browntruck](https://github.com/pypa/browntruck)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
