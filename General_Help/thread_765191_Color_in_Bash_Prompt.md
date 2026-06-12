---
title: "Color in Bash Prompt?"
date: 2008-04-24
forum: General Help
---

### Post by mrb88 on 2008-04-24
Hey - using Hardy Heron. I'm trying to figure out how to colorize my bash prompt like I did in 7.10 (this is a fresh install). My current .bashrc is: 

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth

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
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
force_colored_prompt=yes

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
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'

    #alias grep='grep --color=auto'
    #alias fgrep='fgrep --color=auto'
    #alias egrep='egrep --color=auto'
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



I uncommented the force_coloured_prompt yes, thinking that would do it. Which part allows the colored prompt? Thanks!

---

### Post by NTolerance on 2008-04-25
I'm having the same problem.  I changed the TERM environment variable from xterm to xterm-color and it still doesn't work.

Edit:  Looked at the script a bit more closely and found a bug.  Change this

```
force_colored_prompt=yes
```

to this

```
force_color_prompt=yes
```

---

### Post by maino on 2008-04-30
This worked for me.  Many thanks.

---

### Post by uku on 2008-04-30
[COLOR=#000000]You can customize the colors by changing the description in this part of the script:
```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}[COLOR=Red]\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$[/COLOR] '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
```Bash color codes:

Black       0;30         Dark Gray     1;30
Blue        0;34              Light Blue    1;34
Green       0;32           Light Green   1;32
Cyan        0;36             Light Cyan    1;36
Red         0;31              Light Red     1;31
Purple      0;35           Light Purple  1;35
Brown       0;33            Yellow        1;33
Light Gray  0;37      White         1;37

The first digit, as you can see, marks the brightness: 0 regular(dull color), 1 bright. This isn't the case in an xterm, where the same part marks bold/not bold. [/COLOR][COLOR=#000000]The same colors, beginning from 40, mark the background color. The first digit [/COLOR][COLOR=#000000](brightness)[/COLOR][COLOR=#000000] can't be used, or at least has no effect. There are some more options aswell, like [/COLOR]4: Underscore, 5: Blink, 7: Inverse, 8: Concealed.
[COLOR=#000000] 
For example, the following description will give a white, underlined user@host text on [/COLOR][COLOR=#000000]blue background and[/COLOR][COLOR=#000000] yellow directory text.
[/COLOR]```
\[\033[44m\]\[\033[1;37m\]\[\033[4m\]\u@\h\[\033[00m\]:\[\033[01;33m\]\w\[\033[00m\]\$ 
```A much more thorough bash prompt howto: [http://www.faqs.org/docs/Linux-HOWTO/Bash-Prompt-HOWTO.html#AEN343](http://www.faqs.org/docs/Linux-HOWTO/Bash-Prompt-HOWTO.html#AEN343)

---

