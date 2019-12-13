# zpm-zsh/dircolors-material as a Zsh/NPM package

##### Homepage link: [zpm-zsh/dircolors-material](https://github.com/zpm-zsh/dircolors-material)

| **Package source:** | Tarball | Binary | Git | Node | Gem |
|:-------------------:|:-------:|:------:|:---:|:----:|:---:|
| **Status:**         |    -    |    -   | + <br> (default) | – |  –  |

## Introduction

[Zplugin](https://github.com/zdharma/zplugin) can use a `package.json`
(similar in construct to the one used in `npm` packages) to automatically:

- get the plugin's Git repository OR release-package URL,
- get the list of the recommended ices for the plugin,
    - there can be multiple lists of ices,
    - the ice lists are stored in *profiles*; there's at least one profile, *default*,
    - the ices can be selectively overriden.

## The `dircolors-material` Package

The package provides the
[zpm-zsh/dircolors-material](https://github.com/zpm-zsh/dircolors-material)
definitions for GNU `ls`, `ogham/exa` and also setups zsh-completion system to
use the definitions.

Example invocations that'll install `zpm-zsh/dircolors-material` from Git
repository in the most optimized way as described on the [Zplugin
Wiki](http://zdharma.org/zplugin/wiki/LS_COLORS-explanation/):

```zsh
# Download the default profile
zplugin pack for dircolors-material

# Download the no-zsh-completion profile
zplugin pack"no-zsh-completion" for dircolors-material
```

## Default Profile

Provides the dircolors-material definitions for GNU `ls`, `ogham/exa` and also setups
zsh-completion system to use the definitions.

The Zplugin command executed will be equivalent to:

```zsh
zplugin lucid \
 atclone"(( !${+commands[dircolors]} )) && local P=g
    \${P}dircolors -b dircolors-material > colors.zsh" \
 atpull'%atclone' pick"colors.zsh" nocompile'!' \
 atload'zstyle ":completion:*:default" list-colors "${(s.:.)LS_COLORS}";' for \
    zpm-zsh/dircolors-material
```

## `no-zsh-completion` Profile

Provides the dircolors-material definitions for GNU `ls`, `ogham/exa` but doesn't set up
the zsh-completion system to use them.

The Zplugin command executed will be equivalent to:

```zsh
zplugin lucid \
 atclone"(( !${+commands[dircolors]} )) && local P=g
    \${P}dircolors -b dircolors-material > colors.zsh" \
 atpull'%atclone' pick"colors.zsh" nocompile'!' for \
    zpm-zsh/dircolors-material
```

<!-- vim:set ft=markdown tw=80 fo+=an1 autoindent: -->
