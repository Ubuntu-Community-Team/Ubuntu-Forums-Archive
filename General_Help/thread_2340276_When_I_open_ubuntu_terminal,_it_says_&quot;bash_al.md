---
title: "When I open ubuntu terminal, it says &quot;bash: alias: /home/login.py: not found&quot;"
date: 2016-10-17
forum: General Help
---

### Post by ozturkemry on 2016-10-17
When I open ubuntu terminal, it says "bash: alias: /home/login.py: not found". I tried to edit bashrc and everthing looks perfect. Here my bashrc file :

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
    xterm-color|*-256color) color_prompt=yes;;
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


# colored GCC warnings and errors
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'


# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'


#now default version of python is python3.5
alias python=python3.5


# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'


# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.


#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi


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

``` 

Any suggestion?

---

### Post by howefield on 2016-10-17
You could copy the existing .bashrc file to your Documents folder for safe keeping and create a new default ~/.bashrc with the following terminal command..

```
/bin/cp /etc/skel/.bashrc ~/
```

---

### Post by vasa1 on 2016-10-17
Could be the last alias here?

```

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'


#now default version of python is python3.5
alias python=python3.5

```
I don't use that alias, but try```
alias python='python3.5'
```I added single quotes around 'python3.5'. Or just comment out that line and let the system figure out which python to use?

---

### Post by kevdog on 2016-10-17
What's in these files they reference:
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi

---

### Post by ozturkemry on 2016-10-17
Changed .bashrc file and still says same thing after restart. Adding single quotes around 'python3.5' didn't work.

---

### Post by ozturkemry on 2016-10-17
> **kevdog said:**
> What's in these files they reference:
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi



I don't know. Add # to each line. And stuck after login screen. Switched Ctrl+Alt+F1 and redited with vim. I guess they are important.

---

### Post by Habitual on 2016-10-17
```

alias python=python3.5

```
If you don't use it, REM "#" is out so that it resembles
```
#alias python=python3.5
```


```
python3
``` starts well, python3

Restart bash in same terminal using source ~/.bashrc and look for the "error".

---

### Post by ozturkemry on 2016-10-17
> **Habitual said:**
> ```

alias python=python3.5

```
If you don't use it, REM "#" is out so that it resembles
```
#alias python=python3.5
```


```
python3
``` starts well, python3

Restart bash in same terminal using source ~/.bashrc and look for the "error".


No "error" in active terminal after restart bash. But when I open new terminal,  error appear again.

---

