# Repolex Knowledge Graph of explosion/spacy-loggers

RDF knowledge graph data for [explosion/spacy-loggers](https://github.com/explosion/spacy-loggers), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/spacy-loggers
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 607fc89366cf25b18441a92fe54ddcd07b8e6c3f
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 607fc89366cf25b18441a92fe54ddcd07b8e6c3f
│           └── chunk-001.nq.gz
├── blob
│   ├── 061f94222dbaadbd6d2b837c97e407a6944d5127.nq.gz
│   ├── 1f1a1479b7321ba91fba64fb69f6bf479c634a4e.nq.gz
│   ├── 28bd112a73d4fc82e621318b3eb29361619c073a.nq.gz
│   ├── 2f61526cf02236745cc79d8c1535e58b2cb495b5.nq.gz
│   ├── 3af8060dba870aac31bba2badb5c2ad1f3847bbc.nq.gz
│   ├── 3ec78f2bace7f0aa648c660c8e98d6f892ed93ce.nq.gz
│   ├── 4350174cf9f66ebf628b484903b6fe34d73ff69b.nq.gz
│   ├── 453ef23fbd50c6fea885577ab5461c7b0b82de19.nq.gz
│   ├── 4ad1f09cfa4ee0a90334d9afdab06cfcac769b97.nq.gz
│   ├── 4d3bb6749c0df63f084e0f266068b01ee7fc2500.nq.gz
│   ├── 549442debdaaad7d1ef4005b454cf532d23b191d.nq.gz
│   ├── 54fc2ffccbeed5b7f850a6423bb2d9802008499d.nq.gz
│   ├── 6bc52b04024d8bf765cf54add612713af5290bb5.nq.gz
│   ├── 7b1da4d2c1deceffea9e79bc632746a9d08bf38e.nq.gz
│   ├── 7bafbdf70b05713887b55e3be660c54e41c628b7.nq.gz
│   ├── 969d31ed6db767cc2e78bc2b1c9825a287fa6830.nq.gz
│   ├── 983a7c93292304d4092bffa5869eb21fd835b869.nq.gz
│   ├── a49b486bf03abdb573112097dbe3696d4c576327.nq.gz
│   ├── acdd4f6248c92e77caac9505f3d321724179024a.nq.gz
│   ├── d85521251ca663f50eecef686746823943b91a57.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e9850e60820e26bbc5b622ef8a2c74c8f98eafea.nq.gz
│   └── f5ce4d9e09b55735c57e7a419d6ed6501ab8e1c6.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 607fc89366cf25b18441a92fe54ddcd07b8e6c3f.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 30 files
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

[explosion/spacy-loggers](https://github.com/explosion/spacy-loggers)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
