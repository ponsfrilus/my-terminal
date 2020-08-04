<!-- TOC titleSize:2 tabSpaces:2 depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 skip:0 title:0 charForUnorderedList:* -->
* [My Terminal](#my-terminal)
* [Oh My Zsh](#oh-my-zsh)
* [Zsh config](#zsh-config)
  * [History](#history)
  * [Aliases](#aliases)
  * [Plugins](#plugins)
  * [zsh-autosuggestions](#zsh-autosuggestions)
  * [zsh-syntax-highlighting](#zsh-syntax-highlighting)
* [Zsh theme](#zsh-theme)
  * [Zsh P10K Theme configuration](#zsh-p10k-theme-configuration)
* [fzf — command-line fuzzy finder](#fzf--command-line-fuzzy-finder)
* [Links](#links)
<!-- /TOC -->

# My Terminal

This is my reminder for configuring my terminal with [Zsh](https://www.zsh.org/),
and gain in efficiency in day to day terminal operations.

![My Terminal](./img/terminal.png)

# Oh My Zsh

> Oh My Zsh is an open source, community-driven framework for managing your zsh configuration.
[https://ohmyz.sh/](https://ohmyz.sh/)

```bash
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```

# Zsh config

## History

In your `~/.zshrc` file:
```bash
# User configuration
HISTFILE=~/.zsh_history
HISTSIZE=999999999
SAVEHIST=$HISTSIZE
setopt inc_append_history
setopt share_history
```

## Aliases

Zsh comes with a ton of alias, just type `alias` in your termial to study them.

If you want to use your own aliases, use your `~/.bash_aliases` in order to be
able to use them in any shells.

In your `~/.zshrc` file:
```bash
source ~/.bash_aliases
```

## Plugins

In your `~/.zshrc` file:
```bash
plugins=(
        git
        docker
        oc
        kubectl
        npm
        node
        wp-cli
        zsh-autosuggestions
        zsh-syntax-highlighting
        )
```

Have a look to [https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins) to find more!

![Zsh command completion](./img/suggestions.png)

## zsh-autosuggestions

> Fish-like autosuggestions for Zsh [https://github.com/zsh-users/zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions)

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions \
  ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

![Zsh autosuggestions](./img/autocomplete.png)

## zsh-syntax-highlighting

> Fish shell-like syntax highlighting for Zsh [https://github.com/zsh-users/zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
  ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

# Zsh theme

> Powerlevel10k is a theme for Zsh. It emphasizes speed, flexibility and out-of-the-box experience [https://github.com/romkatv/powerlevel10k](https://github.com/romkatv/powerlevel10k)

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \
  ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

## Zsh P10K Theme configuration

In your `~/.zshrc` file:
```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
POWERLEVEL9K_LEFT_PROMPT_ELEMENTS+=(dir vsc)
POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS+=(node_version php_version ram cpu_temp)
```

Once your `ZSH_TEME` is set, use `p10k configure` to configure p10k.

# fzf — command-line fuzzy finder

> fzf is a general-purpose command-line fuzzy finder [https://github.com/junegunn/fzf](https://github.com/junegunn/fzf)

```bash
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```

Once installed, use <kbd>ctrl + r</kbd> to search your `history`.

![fzf command-line fuzzy finder](./img/fzf.png)

# Links

  * [Your terminal can be much, MUCH more productive 💻](https://medium.com/@ivanaugustobd/your-terminal-can-be-much-much-more-productive-5256424658e8)
  * [Power up your Terminal using Oh-my-Zsh + iTerm2](https://medium.com/swlh/power-up-your-terminal-using-oh-my-zsh-iterm2-c5a03f73a9fb)
  * [How FZF and ripgrep improved my workflow](https://medium.com/@sidneyliebrand/how-fzf-and-ripgrep-improved-my-workflow-61c7ca212861)

<!--
[//]: pandoc \
  --variable mainfont="DejaVu Sans" \
  --variable monofont="DejaVu Sans Mono" \
  --variable fontsize=11pt \
  --variable geometry:"top=1.5cm, bottom=2.5cm, left=1.5cm, right=1.5cm" \
  --variable geometry:a4paper \
  --variable colorlinks \
  --variable linkcolor=blue \
  --variable urlcolor=blue \
  --number-sections \
  --highlight-style tango \
  -f markdown README.md \
  --pdf-engine=lualatex \
  -o MyTerminal.pdf && xdg-open MyTerminal.pdf
-->