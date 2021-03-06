---
id: pnpm-recursive
title: pnpm recursive
---

## tl;dr

|Command|Meaning|
|--|--|
|`pnpm recursive link` | link all packages in the monorepo and install their dependencies |
|`pnpm recursive run build --filter foo-*` |builds all packages with names that start with `foo-` |

## Options

### filter

Added in: v2.13.0

Restricts the scope to package names matching the given glob.

Usage examples:

```sh
pnpm recursive link --filter @babel/*
```

Also allows to select all the dependencies (direct and non-direct ones).
To select all the dependencies of a package, prefix the name of the package with `...`.

Usage examples:

```sh
pnpm recursive link --filter @babel/preset-2018...
pnpm recursive link --filter @babel/preset-*...
```

### workspace-concurrency

Added in: v2.13.0

* Default: **4**
* Type: **Number**

Set the maximum number of concurrency. For unlimited concurrency use `Infinity`.

### bail

Added in: v2.13.0

* Default: **true**
* Type: **Boolean**

If true, stops when a task throws an error.

Usage example. Run tests in every package. Continue if tests fail in one of the packages:

```
pnpm recursive test --no-bail
```

## pnpm recursive install

Added in: v1.24.0

```sh
pnpm recursive install [arguments]
```

Concurrently runs install in all subdirectories with a `package.json` (excluding node_modules).

Usage examples:

```sh
pnpm recursive install
pnpm recursive install --ignore-scripts
```

## pnpm recursive update

Added in: v1.24.0

```sh
pnpm recursive update [arguments]
```

Concurrently runs update in all subdirectories with a `package.json` (excluding node_modules).

Usage examples:

```sh
pnpm recursive update
pnpm recursive update --depth 100
# update typescript to the latest version in every package
pnpm recursive update typescript@latest
```

## pnpm recursive uninstall

Added in: v2.10.0

```sh
pnpm recursive uninstall [<@scope>/]<pkg>...
```

Uninstall a dependency from each package

Usage examples:

```sh
pnpm recursive uninstall webpack
```

## pnpm recursive link

Added in: v1.32.0

```sh
pnpm recursive link [arguments]
```

Concurrently runs installation in all subdirectories with a `package.json` (excluding node_modules).
If a package is available locally, the local version is linked.

Usage examples:

```sh
pnpm recursive link
pnpm recursive link --ignore-scripts
```

## pnpm recursive dislink

Added in: v1.32.0

An alias of `recursive unlink` from v2.0.0

```sh
pnpm recursive dislink [arguments]
```

Removes links to local packages and reinstalls them from the registry.

Usage examples:

```sh
pnpm recursive dislink
```

## pnpm recursive outdated

Added in: v2.2.0

```sh
pnpm recursive outdated [[<@scope>/]<pkg> ...]
```

Check for outdated packages in every project of the multi-package repo.

Usage examples:

```sh
pnpm recursive outdated
```

## pnpm recursive list

Added in: v2.2.0

```sh
pnpm recursive list [[<@scope>/]<pkg> ...]
```

List packages in each project of the multi-package repo.
Accepts the same arguments and flags as the regular `pnpm list` command.

Usage examples:

```sh
pnpm recursive list
```

## pnpm recursive run

Added in: v2.3.0

```sh
pnpm recursive run <command> [-- <args>...]
```

This runs an arbitrary command from each package's "scripts" object.
If a package doesn't have the command, it is skipped.
If none of the packages have the command, the command fails.

Usage examples:

```sh
pnpm recursive run build
```

## pnpm recursive test

Added in: v2.3.0

```sh
pnpm recursive test [-- <args>...]
```

This runs each package's "test" script, if one was provided.

Usage examples:

```sh
pnpm recursive test
```

## pnpm recursive rebuild

Added in: v2.4.0

```sh
pnpm recursive rebuild [[<@scope>/<name>]...]
```

This command runs the **pnpm build** command in every package of the multi-package repo.

Usage examples:

```sh
pnpm recursive rebuild
```

## pnpm recursive exec

Added in: v2.9.0

```sh
pnpm recursive exec -- <command> [args...]
```

This command runs a command in each package of the multi-package repo.

Usage examples:

```sh
pnpm recursive exec -- rm -rf node_modules
```
