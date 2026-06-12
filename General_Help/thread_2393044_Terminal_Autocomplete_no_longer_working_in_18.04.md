---
title: "Terminal Autocomplete no longer working in 18.04"
date: 2018-05-28
forum: General Help
---

### Post by michael363 on 2018-05-28
I have semi-upgraded from 17.10 to 18.04. Trying to simply upgrade did not work, so I had to make a USB stick for upgrading and installed 18.04 overwriting 17.10 but keeping all config in /home.

Since the upgrade the terminal autocomplete does no longer work correctly. It works for the first word entered, but not for any successive commands, which makes apt-get near impossible to use without looking up the exact package names beforehand.

What do I need to do to regain access to the autocomplete functionality?

Thanks in advance for your help 8-)

---

### Post by nlee2 on 2018-05-29
Did you try to reinstall

apt install --reinstall bash-completion

---

### Post by michael363 on 2018-05-29
Just tried removing it, then reinstalled and it did not help. :/

It works with the first command though, so I'm not sure what's going on there.

---

### Post by michael363 on 2018-06-04
Bump

---

### Post by #&amp;thj^% on 2018-06-04
Would be possibly helpful to see the contents of:
```
gedit ~/.bashrc
```
It should contain something like this:
```
# enable bash completion in interactive shells
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi
```
If the above is not listed>>then add it to the bottom and save.
Then either logout and back in>> or simply just run:
```
source ~/.bashrc
```
Good Luck

---

### Post by michael363 on 2018-06-05
Thanks for the reply.

There is no .bashrc file in my home-directory. Should I just create an empty textfile, name it .bashrc and copy your code to test if it works?

Thanks

---

### Post by #&amp;thj^% on 2018-06-05
> **michael363 said:**
> Thanks for the reply.

There is no .bashrc file in my home-directory. Should I just create an empty textfile, name it .bashrc and copy your code to test if it works?

Thanks

Are you sure?
let's have a peek at:
```
cd
ls -a
```
Run one line at  a time.
Paste back the return>>>and Please use Code Tags.
Or even better show the return for:
```
gedit .bashrc
```

---

### Post by michael363 on 2018-06-06
Yes, I am sure.

```
gedit .bashrc
``` gives me an empty file.

Doing ```
ls -a
``` in the home folder gives a whole bunch of stuff but no .bashrc file.

---

### Post by #&amp;thj^% on 2018-06-06
Well then that's a first for me, I've never seen where a **".bashrc" file was absent **from a proper install. :confused:
But any who here is mine, and you should be ok to use this on 18.04.
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
alias rmkern='echo "dpkg -l linux-* | awk '\''/^ii/{ print \$2}'\'' | grep -v -e \`uname -r | cut -f1,2 -d\"-\"\` | grep -e [0-3]| xargs sudo apt-get -y purge --dry-run"'


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
And just save it to your Home directory as** ".bashrc"**
And run:
```
source ~/.bashrc
```
If any errors paste them back here.

---

### Post by oldos2er on 2018-06-06
You can copy the system's bashrc to your home folder ```
cp /etc/bash.bashrc .bashrc
``` I agree with 1fallen that something's wrong with your system if ~/.bashrc doesn't exist.

---

### Post by michael363 on 2018-06-09
Thanks to both of you.

I copied the .bashrc from /etc/ and now the autocomplete works again 8-)

---

### Post by oldos2er on 2018-06-09
Would you please mark the thread solved? Thanks.

---

### Post by michael363 on 2018-06-09
Thanks to both of you, the completion functionality is completely restored now.

I copied the system bashrc, not the one that was posted here :)

---

