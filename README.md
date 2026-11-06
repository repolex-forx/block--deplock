# Repolex Knowledge Graph of block/deplock

RDF knowledge graph data for [block/deplock](https://github.com/block/deplock), parsed by [repolex](https://repolex.ai).

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
rlex download block/deplock
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 1772173ed53b84a97a4ce3fbacaf989bef61b576
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 1772173ed53b84a97a4ce3fbacaf989bef61b576
│           └── chunk-001.nq.gz
├── blob
│   ├── 0f60512f9adea841a0fe01ef4a6ea0d012dd4ada.nq.gz
│   ├── 18fb22c2a3bd2617c9b7838e16c36cf898d78814.nq.gz
│   ├── 19765e2ce510628601d21aef53c5a95c4fed7a2e.nq.gz
│   ├── 1bc469e68eb776aa52185c6cbfc5cdcaee837ce3.nq.gz
│   ├── 2eeff505164be6c62a378c8ba90ee31bd8b1c0f3.nq.gz
│   ├── 47d774c2e02cc1fbd894224ebb61a0bbea624052.nq.gz
│   ├── 50ea3fb14c4736ed9bf6816048af4aa8975fe749.nq.gz
│   ├── 5cb0abef618d3063fee0809fe531b803a28cab0b.nq.gz
│   ├── 61ecfa309de93d7902ea34af12b3b502f477decc.nq.gz
│   ├── 63bbe1234c62a388aabc8280ec389341f0e3e364.nq.gz
│   ├── 6a3d795443b738e7b5333a0e36c533ac00634073.nq.gz
│   ├── 6ae4d31c100abd099e42062685701e6b668d2b77.nq.gz
│   ├── 6bccf43368fd7c96d9c659562a5142b8b8cb98a1.nq.gz
│   ├── 6e6598680380ed48bcd0c273a48d03ab7f66eca3.nq.gz
│   ├── 7c016e3d1161221e91f7b174eef0702142277fb1.nq.gz
│   ├── 7fe4e7ddfa36bb35e66ef043b30a2fbf3f42ddfb.nq.gz
│   ├── 8fc8a93fae6d13fe7b7b936a9ffab71ba348d412.nq.gz
│   ├── 92cc8b4ab6a55ccab6ef12961c9dda806d656acd.nq.gz
│   ├── a453b7925fb066ebf0c0c65c771bd79a7c28146b.nq.gz
│   ├── ab34d6b0f5b2707ab48a6c09311a06dff505d3e2.nq.gz
│   ├── abd5fcdd91fe6cc1c8df8ef27a837fa283f32363.nq.gz
│   ├── ba9a7fb669bcdd686e09f23557833eb438ad3c55.nq.gz
│   ├── c19824dc92d757bec4dba6f99f39d21e6436f266.nq.gz
│   ├── c378136b128524109db4e00ddd6592055ea84697.nq.gz
│   ├── c596de4a5c43fa08f0c841cdc00a5544f8484981.nq.gz
│   ├── c63b9aaaee2757888b7c4d7f27ae15f3d826ec34.nq.gz
│   ├── c93bea64037462df19ab57799ad34b6e3904ee10.nq.gz
│   ├── c9c8e9276f75950b58cc24613db6b182244647d5.nq.gz
│   ├── d0d77fca452be534cee2ef2e1fbb01c3ac694e14.nq.gz
│   ├── e1f8144080960ce1b2311f9e9d04a882acc07793.nq.gz
│   ├── e251c30f129040a7e149cfc80fb06bfe96b68b7d.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── ed162d9d8ca7b0859b5ed22b17d87184b917d023.nq.gz
│   ├── eef4bd20cf972fc2f3c7405fdae3fdcff80e59d4.nq.gz
│   └── fb086fcbc4abb67e02cf37ec7f1996fcae392f8f.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 1772173ed53b84a97a4ce3fbacaf989bef61b576.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 43 files
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

[block/deplock](https://github.com/block/deplock)

---
*Parsed on 2026-11-06 by [repolex](https://repolex.ai)*
