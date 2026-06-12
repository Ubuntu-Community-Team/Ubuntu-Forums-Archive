---
title: "bash error"
date: 2007-05-05
forum: General Help
---

### Post by Régis B. on 2007-05-05
Hello everyone,
I recently tried to modify my ~/.bashrc file and since then I cannot open a shell and I am presented with the following error:

bash: PROMPT_COMMAND: line 0: unexpected EOF while looking for matching `"'
bash: PROMPT_COMMAND: line 1: syntax error: unexpected end of file

I guess this should originate from a syntax error in my ~/.bashrc but I simply can't find it; I compared the file with others .bashrc's, such as the one of root (/root/.bashrc) but couldn't find any significant difference.

Here is the incriminated file (~/.bashrc):

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~`;`;_:\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

# JAVA_HOME (for Tomcat) 
export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.11
export CLASSPATH=/usr/share/tomcat5.5/common/lib/jsp-api.jar:/usr/share/tomcat5.5/common/lib/servlet-api.jar



```

I'm using Kubuntu Feisty by the way.

Régis B.

---

### Post by jakev383 on 2007-05-05
This line:
```

PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~`;`;_:\007"'

```
Look funny. You have open ticks (`;`;) but no closing ticks afterwards.
Here's mine:
```

PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'

```
Hope that solves it for you.

---

### Post by Régis B. on 2007-05-05
That's another issued fixed in a matter of minutes!

In the name of me, I couldn't say when I did change this line but apparently that was the soruce of my problem.

Thanks a lot!

Régis B.

---

### Post by jakev383 on 2007-05-05
No problem. Enjoy!

---

