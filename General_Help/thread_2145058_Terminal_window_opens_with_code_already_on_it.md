---
title: "Terminal window opens with code already on it"
date: 2013-05-14
forum: General Help
---

### Post by desesperado on 2013-05-14
Hi forum gurus, again I'm here asking for your help.

The problem I'm facing with appeared after I run this code:
```
sudo apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | head -n -1)
```which I get from [this post]("http://ubuntuforums.org/showthread.php?t=2098490&p=12426110#post12426110") by forum moderator CharlesA. Everything went well with it and I was able to free more than 600 MB on my hard drive.

What's strange, and this is the reason I'm asking for help, is that whenever I open a terminal window in my desktop, or TTL1 through TTL6, it opens with bits of that code before the prompt, as follow:
```
bash: /"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"/d: No such file or directory
bash: s/^[^: No such file or directory
bash: /[0-9]/!d | sort -t- -k3 | head -n -3): No such file or directory
korrigan@ubuntu:~$ 
```

Is this fixable? What are the implications of such a issue and why is this happening?

All help will be more than appreciated.

---

### Post by PowerBarry43 on 2013-05-14
Hi

Try checking in ~/.bashrc (hidden in your home dir press ctrl+h to view) and /etc/bash.bashrc for that command if you find it delete it and save the file. If it's in the second one you will need to use sudo to edit it like so...

```
sudo gedit /etc/bash.bashrc
```

hope this helps!!

Barry

---

### Post by desesperado on 2013-05-14
Hi, PowerBarry43, thanks for your answer and for helping.

I've done as you advise but the command isn't in either of those two files. Check it:
 ~/.bashrc content:
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
```

/etc/bash.bashrc content:
```
# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
#if ! shopt -oq posix; then
#  if [ -f /usr/share/bash-completion/bash_completion ]; then
#    . /usr/share/bash-completion/bash_completion
#  elif [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#  fi
#fi

# sudo hint
if [ ! -e "$HOME/.sudo_as_admin_successful" ] && [ ! -e "$HOME/.hushlogin" ] ; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
    cat <<-EOF
    To run a command as administrator (user "root"), use "sudo <command>".
    See "man sudo_root" for details.
    
    EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found -o -x /usr/share/command-not-found/command-not-found ]; then
    function command_not_found_handle {
         # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
     /usr/lib/command-not-found -- "$1"
                   return $?
                elif [ -x /usr/share/command-not-found/command-not-found ]; then
     /usr/share/command-not-found/command-not-found -- "$1"
                   return $?
  else
     printf "%s: command not found\n" "$1" >&2
     return 127
  fi
    }
fi

# Setting LaTex's PATH, MANPATH e INFOPATH
PATH=/usr/local/texlive/2012/bin/i386-linux:$PATH; export PATH
MANPATH=/usr/local/texlive/2012/texmf/doc/man:$MANPATH; export MANPATH
INFOPATH=/usr/local/texlive/2012/texmf/doc/info:$INFOPATH; export INFOPATH
```

Do you have any other suggestions?

---

### Post by PowerBarry43 on 2013-05-14
ok you can check in ~/.profile too otherwise try searching for "uname -r" (part of the error message) in all files like this:
```
sudo grep -r "uname -r" /
```
wil take a little while to run through...

Barry

---

### Post by desesperado on 2013-05-14
I found out what was causing it. The culprit was this bash aliases I made with that command and that I put in my **~/.bash_aliases** file:
```
alias cleankernel='sudo apt-get purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | sort -t- -k3 | head -n -3)'
```
I comment it out and now whenever I open a terminal window everything is back to normal.

Before I close this thread and mark it as solved, can anyone explain to me why was that happening? I have a few more aliases in that file defined the same way and neither of them has ever cause such an error.

---

### Post by PowerBarry43 on 2013-05-16
Hi

The problem is due to the way this specific command works. It's because you are setting a variable in the alias command which would be executed when bash starts, the bit after the $ inside the brackets. In order to resolve this code into the list of old kernel packages that will be used by apt-get purge. when setting this alias what you're effectively doing is:

```
KERNVAR=`dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed  "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^  ]*\).*/\1/;/[0-9]/!d' | sort -t- -k3 | head -n -3`

sudo apt-get purge $KERNVAR

```

but if you just run

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | sort -t- -k3 | head -n -3
```

you'll probably find that it genarates the same errors

Barry

---

