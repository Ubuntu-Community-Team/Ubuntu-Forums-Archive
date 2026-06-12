---
title: "Can't log in on CTRL+ALT+F1"
date: 2015-11-27
forum: General Help
---

### Post by mickee384 on 2015-11-27
For some reason, Can't log in on CTRL+ALT+F1 (or  any other F key). When I enter my user/pass it just goes back to login. Not sure when this happened so don't really know what caused this. I can say that I can log in using root. Just not from my login. I have no issues with logging in to the GUI. I am concerned as I like the console should I make my system fubar, in order to fix it. Everything else seems ok. I have done some searching on the forum as well as the internet. Any ideas will be greatly appreciated.:p

---

### Post by furtom on 2015-11-27
Just to check the obvious, is is possible your user name has a capitalization you are forgetting?

---

### Post by mickee384 on 2015-11-27
no caps all lower case. Also it doesn't give any error at all, just goes back to login

---

### Post by steeldriver on 2015-11-27
Is there perhaps something in one of your startup scripts (.profile, .bash_profile) that might be killing the login shell?

---

### Post by mickee384 on 2015-11-27
Ok, so I created a new user. I can log into the console CTRL+AL+F1 with that as well as root. If I was to hazard a guess I would say the my main profile is corrupted somehow, So I could copy over /home to the new profile and test that. I would have to chown the /home to my new user name, right? I am reluctant to do all this as i have no issues logging into the lightdm with my user and all works from there. Is there something specific in the .profile I should maybe look for?

sorry btw I am running Ubuntu 14.04 with Unity as my desktop

---

### Post by mickee384 on 2015-11-27
I was thinking that, but would that not also affect the login to Ubuntu desktop?

---

### Post by mickee384 on 2015-11-27
Ok so it's byobu that is mucking up the works. I removed it but the login still references it:

-bash:/usr/bin/byobu-launch
no such file or directory

I want to remove the reference to byobu as the program stopped working

So its in .bashrc as last entry:

```
[ -r /home/mickee/.byobu/prompt ] && . /home/mickee/.byobu/prompt   #byobu-prompt#
```


This is the full .bashrc:

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
force_color_prompt=yes

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
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;37m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
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

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

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
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi
[ -r /home/mickee/.byobu/prompt ] && . /home/mickee/.byobu/prompt   #byobu-prompt#
```

---

### Post by mickee384 on 2015-11-27
I remarked the byobu line in .bashrc and also in the .profile. Fixed.

---

