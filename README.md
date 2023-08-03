# Benchmarks for [wasm-coredump]

See [results].

## Running the benchmarks

Compile bench:
```
cargo b --target=wasm32-wasi
```

Make a coredump wasm version:
```
wasm-coredump-rewriter < target/wasm32-wasi/debug/bench.wasm > target/wasm32-wasi/debug/bench.coredump.wasm
```

Run:
```
hyperfine --warmup=10 --runs=100 --export-markdown=results.md --shell=none \
"wasmtime target/wasm32-wasi/debug/bench.wasm" "wasmtime target/wasm32-wasi/debug/bench.coredump.wasm"
```

[wasm-coredump]: https://github.com/xtuc/wasm-coredump
[results]: ./results.md
