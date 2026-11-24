# 🦀 rust_foundations

> 20 foundational systems programming challenges to master Rust, concurrency, low-level networking, and systems architecture at **stgo-tomLAB**.

---

## 🧭 Overview

This repository is structured as a **Cargo Workspace (Monorepo)**. All projects live inside the `crates/` directory and share dependencies, compiler caches, and a unified CI pipeline.

```text
rust_foundations/
├── Cargo.toml          # Workspace root manifest
├── crates/             # Individual project crates
│   ├── 01-huffman/
│   ├── 02-regex-nfa/
│   └── ...
└── .github/
    └── workflows/
        └── ci.yml      # Clippy, formatting & test suite
```

---

## 🗺️ Project Roadmap

| # | Tier | Project / Crate | Core Concepts & Challenges | Target Crate | Status |
|:---:|:---:|---|---|:---:|:---:|
| **01** | `A` | **Lossless Huffman File Compressor** | Byte frequency counting, priority queues, binary tree construction, bitwise packing/unpacking to shrink text files. | [`01-huffman`](crates/01-huffman) | ⚪ Planned |
| **02** | `A` | **Regex Engine (Thompson NFA)** | Machine math with zero regex crates, regex syntax parsing, Thompson's NFA construction, state machine simulation. | [`02-regex-nfa`](crates/02-regex-nfa) | ⚪ Planned |
| **03** | `A` | **Concurrent TCP Port Scanner** | Non-blocking socket manipulation, firing 1000 connection attempts in parallel, multiplexing readiness with `poll()` / `epoll`. | [`03-port-scanner`](crates/03-port-scanner) | ⚪ Planned |
| **04** | `A` | **Unix Shell** | Linux process lifecycle, line parsing/tokenizing, `fork()`, `execvp()`, parent `waitpid()`, signal handling, and I/O redirection. | [`04-unix-shell`](crates/04-unix-shell) | ⚪ Planned |
| **05** | `B` | **Raw Packet Sniffer & ICMP Ping Tool** | Raw sockets (`AF_INET`/`SOCK_RAW`), hand-packing 8-byte ICMP echo request headers, computing 1's-complement checksums, measuring RTT. | [`05-raw-ping`](crates/05-raw-ping) | ⚪ Planned |
| **06** | `B` | **Zero-Framework HTTP/1.1 Server** | Pure TCP listener, multiplexing thousands of sockets with non-blocking `epoll`, request header parsing, static file streaming, keep-alive, MIME types. | [`06-http-server`](crates/06-http-server) | ⚪ Planned |
| **07** | `B` | **L7 Reverse Proxy & Load Balancer** | Fronting backend servers, round-robin HTTP forwarding, background health checks, dynamic routing around failed nodes. | [`07-load-balancer`](crates/07-load-balancer) | ⚪ Planned |
| **08** | `B` | **BitTorrent Client** | Bencode dictionary parsing, tracker queries, binary peer-wire protocol over raw TCP (handshake, bitfield/unchoke, 16KB parallel block requests, SHA-1 verification). | [`08-bittorrent`](crates/08-bittorrent) | ⚪ Planned |
| **09** | `TBD` | *Project 09* | *To be added* | `crates/09-...` | ⚪ Planned |
| **10** | `TBD` | *Project 10* | *To be added* | `crates/10-...` | ⚪ Planned |
| **11** | `TBD` | *Project 11* | *To be added* | `crates/11-...` | ⚪ Planned |
| **12** | `TBD` | *Project 12* | *To be added* | `crates/12-...` | ⚪ Planned |
| **13** | `TBD` | *Project 13* | *To be added* | `crates/13-...` | ⚪ Planned |
| **14** | `TBD` | *Project 14* | *To be added* | `crates/14-...` | ⚪ Planned |
| **15** | `TBD` | *Project 15* | *To be added* | `crates/15-...` | ⚪ Planned |
| **16** | `TBD` | *Project 16* | *To be added* | `crates/16-...` | ⚪ Planned |
| **17** | `TBD` | *Project 17* | *To be added* | `crates/17-...` | ⚪ Planned |
| **18** | `TBD` | *Project 18* | *To be added* | `crates/18-...` | ⚪ Planned |
| **19** | `TBD` | *Project 19* | *To be added* | `crates/19-...` | ⚪ Planned |
| **20** | `TBD` | *Project 20* | *To be added* | `crates/20-...` | ⚪ Planned |

---

## 🛠️ Development & Quality Gates

Every project in this repository follows strict quality rules enforced by CI on every commit and PR:

### Running Commands from Workspace Root
```bash
# Check compilation for all crates
cargo check --workspace

# Run formatting check
cargo fmt --all --check

# Run linter (must pass with 0 warnings)
cargo clippy --all-targets --all-features -- -D warnings

# Run all test suites
cargo test --workspace

# Run a specific project
cargo run -p 01-huffman
```

### Adding a New Project
```bash
cargo new --bin crates/<number>-<name>
```
Cargo automatically registers it into the workspace thanks to `"crates/*"` in root `Cargo.toml`.
