---
title: "I want Terminal to be colored by default"
date: 2006-11-02
forum: General Help
---

### Post by anil_robo on 2006-11-02
I am running Ubuntu server, and the terminal used to show directories and files in color previously. But it's all plain black-n-white now, probably after some upgrade I did few months ago. Though it doesn't hurt as much, still I'd love to see the same settings back.

I am able to set the color of terminal by some command (I forgot), but the changes are temporary - the terminal becomes black and white again once I logout or restart the system.

Please help. Thanks

Anil

---

### Post by raul_ on 2006-11-02
Maybe right clicking it, edit profile and playing with the settings?

---

### Post by anil_robo on 2006-11-02
> **raul_ said:**
> Maybe right clicking it, edit profile and playing with the settings?
I am using "server install" - can't right click! ](*,)
In fact, I've detached the mouse and packed it in the closet.

---

### Post by CatKiller on 2006-11-02
Does it still use the .bashrc file in your Home folder?

---

### Post by TigerWolf on 2006-11-02
Cant you edit the profiles in the options menu of the terminal? Im not in ubuntu atm so cant tell you the exact location.

---

### Post by skymt on 2006-11-02
Add this line to "~/.bashrc":```
alias ls="ls --color=auto"
```

---

### Post by po0f on 2006-11-02
anil_robo,

Could you post your ~/.bashrc so I can compare it to mine?  The following is just a snippet (everything pertaining to color):
```
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
fi

alias ls='ls --color=auto -hF'
alias ll='ls --color=auto -lhF'
alias la='ls --color=auto -lahF'
alias grep='grep --color=auto'
```

You don't have to alias commands the way I have them aliased, it's just the way I like things done.

---

### Post by skymt on 2006-11-02
po0f: You don't need everything in every alias. Try this:```
alias ls='ls --color=auto -hF'
alias ll='ls -l'
alias la='ls -la'
```Here's how it works. "ll" expands to "ls -l". However, alias expansions are recursive, so that expands further to "ls --color=auto -hF -l". The only exception to recursive alias expansion is when the alias includes itself.

---

### Post by po0f on 2006-11-02
skymt,

I didn't know aliases were recursive, thanks!  You learn something new everyday.  :)  (I'll be keeping them that way anyway, I *do* like things being fairly verbose though!)

---

### Post by anil_robo on 2006-11-03
> **CatKiller said:**
> Does it still use the .bashrc file in your Home folder?

I don't know! In fact, I do not have a .bashrc file in my home folder! I have created a .bashrc file and inserted some text as shown by skymt, but still it does not work. Should I have tried double quotes instead of single quotes?

---

### Post by littlespy on 2006-11-03
I think this might be what your looking for

[http://www.pantz.org/scripting/shell/colorterm.shtml](http://www.pantz.org/scripting/shell/colorterm.shtml)

here is my .bashrc file which i've added nice colors to

> # ~/.bashrc: executed by bash(1) for non-login shells.
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
#case "$TERM" in
#xterm-color)
#    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
#    ;;
#*)
#    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
#    ;;
#esac

# Comment in the above and uncomment this below for a color prompt
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
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


---

