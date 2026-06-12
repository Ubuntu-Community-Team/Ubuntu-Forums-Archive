---
title: "SSH Xterm sessions do not show colors"
date: 2019-04-16
forum: General Help
---

### Post by kmorley on 2019-04-16
I have just loaded Ubuntu Server 18.04 LTS Minimal on an Odroid N2 SBC and it works as expected if I connect through the HDMI console.  But I frequently use VanDyke SecureShell for Xterm emulation and, while I can connect to the server, I only see black and white text - no colors.  When I check the environment variable during an SSH session, I see "TERM=xterm".  I've read numerous other reports of this issue, but those resolutions do not seem applicable.

This is a freshly-loaded system (today) and the startup files should be out-of-the-box original:

```

# cat .profile
#~/.profile: executed by Bourne-compatible login shells.


if [ "$BASH" ]; thenif [ -f ~/.bashrc ]; then
    . ~/.bashrc
  fi
fi

```


```

# cat .bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples


# If not running interactively, don't do anything
[ -z "$PS1" ] && return


# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace


# append to the history file, don't overwrite it
shopt -s histappend


# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000


# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize


# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"


# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi


# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac


# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes


if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
        # We have color support; assume it's compliant with Ecma-48
        # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
        # a case would tend to support setf rather than setaf.)
        color_prompt=yes
    else
        color_prompt=
    fi
fi


if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt


# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac


# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'


    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi


# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'


# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.


if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi


# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
#    . /etc/bash_completion
#fi

```




Any suggestions on where to start troubleshooting this?

Thanks!

Ken Morley

---

### Post by TheFu on 2019-04-17
I can't help with colors, but **ls -F** can be a big help to have visual feedback for directories, links, executable files and pipes. I can't read the color output.

The [Odroid-N2]("https://ameridroid.com/products/odroid-n2") looks pretty great as a 4k@60hz media player. Might be good as a backup server too. Don't think I'd use it as a desktop.  4xUSB3 ports and a real GigE NIC, though the Realtek RTL8211F wouldn't be my choice.

[https://ubuntuforums.org/showthread.php?t=2081842](https://ubuntuforums.org/showthread.php?t=2081842) says you need **ls --color=auto**

---

