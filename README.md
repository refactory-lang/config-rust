# @refactory/config-rust

Shared Rust toolchain configuration for all [refactory-lang](https://github.com/refactory-lang) Rust repositories.

## Usage

Rust doesn't have an `extends` mechanism for Cargo.toml, so configs are referenced/copied:

### rustfmt

Copy `rustfmt.toml` to your repo root:

```bash
cp config-rust/rustfmt.toml .
```

### clippy

Copy `clippy.toml` to your repo root:

```bash
cp config-rust/clippy.toml .
```

### Cargo workspace

Copy relevant settings from `Cargo.workspace.toml` into your `Cargo.toml`:

```toml
[workspace.package]
edition = "2024"
rust-version = "1.85"
license = "Apache-2.0"

[workspace.lints.clippy]
all = { level = "warn", priority = -1 }
pedantic = { level = "warn", priority = -1 }
```

## What's included

| File | Purpose |
|------|---------|
| `rustfmt.toml` | Format config (2024 edition, 100-char width, shorthand) |
| `clippy.toml` | Clippy config (MSRV 1.85, complexity threshold) |
| `Cargo.workspace.toml` | Reference workspace settings (lints, release profile) |

## Toolchain

All refactory-lang Rust repos use:

| Tool | Purpose |
|------|---------|
| `cargo fmt` | Formatting (rustfmt) |
| `cargo clippy -D warnings` | Linting |
| `cargo test` | Testing |
| `cargo build --release` | Production builds (LTO, single codegen unit) |
| Rust 2024 edition | Minimum edition |
| MSRV 1.85 | Minimum supported Rust version |
