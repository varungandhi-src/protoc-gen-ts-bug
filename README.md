# Bug in protoc-gen-ts v0.8.2

Stack trace:

```
/Users/varun/Code/protoc-gen-ts-bug/node_modules/protoc-gen-ts/src/index.js:60
    const { major = 0, minor = 0, patch = 0 } = request.compiler_version;
            ^

TypeError: Cannot read property 'major' of undefined
    at Object.<anonymous> (/Users/varun/Code/protoc-gen-ts-bug/node_modules/protoc-gen-ts/src/index.js:60:13)
    at Module._compile (node:internal/modules/cjs/loader:1101:14)
```

Reproduction steps:

1. Download [Buf v1.4.0](https://github.com/bufbuild/buf/releases/tag/v1.4.0)
   from the releases.
2. ```
   yarn --frozen-lockfile && ./buf generate # assuming that buf was put in current dir
   ```

The bug doesn't reproduce with `0.8.1`.

```
yarn add --dev protoc-gen-ts@0.8.1 && yarn && ./buf generate # OK

yarn add --dev protoc-gen-ts@0.8.2 && yarn && ./buf generate # FAILS
```
