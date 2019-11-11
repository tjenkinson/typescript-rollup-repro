# Rollup/Typescript bug replication repo

Reproduction case for: https://github.com/rollup/rollup/issues/3224

This repo contains 2 npm modules, `packages/with-rollup` and `packages/without-rollup`.
These contain identical code and typescript configurations, but one includes rollup as an unused dev-dependency.
Both of these include a typescript file `index.ts` with an error, in the `with-rollup` package the error is not reported, in the `without-rollup` package the error is reported as expected.

## How to reproduce

```
cd packages/without-rollup
npm i
npm run build
```

This should throw a TS2339 error: "Property 'find' does not exist on type 'number[]'."

```
cd ../with-rollup
npm i
npm run build
```

This is expected to throw a TS2339 error, but does not.

