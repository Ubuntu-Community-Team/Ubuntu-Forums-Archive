---
title: "Bashed BASH"
date: 2007-09-26
forum: General Help
---

### Post by fjstjohn on 2007-09-26
Hello,

Some basic BASH commands such as "ls" are not working. I had just finished saving a new PATH in my .bashrc file.  I reinstalled BASH and coreutils but this did not fix it.  Any ideas?

The program 'ls' is currently not installed.  You can install it by typing:
sudo apt-get install coreutils
bash: ls: command not found


Thanks

fjstjohn

---

### Post by Adramelech on 2007-09-26
saving  anew PATH in your .bashrc file?

WHat did you edited there? please paste your changes

---

### Post by fjstjohn on 2007-09-27
Hello,

Thanks for responding.  

This is what I get when trying to access .bashrc through command line.

fjstjohn@fsj-hp:~$ sudo gedit .bashrc
bash: sudo: command not found

If I view hidden files through nautilus then...

[COLOR="Navy"]# ~/.bashrc: executed by bash(1) for non-login shells.
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

## Coot
PATH=/home/fjstjohn/progams/coot/bin/:$PATH

## pymol
PATH=/home/fjstjohn/programs/pymol[/COLOR]

I just added the last PATH for pymol.

Thanks for the help.
fjstjohn

---

### Post by SeanTater on 2007-09-27
That would be why..

The one before last is correct, but the one with the label "pymol" needs a ":$PATH" at the end

Ah -- I see you did that..

Have you tested this in a new shell (started after you edited bashrc)?

---

### Post by fjstjohn on 2007-09-27
Thanks very much,

Adding the ending did the trick and BASH in now working fine.  Although I would like to know why  this little missing script could cause such significant problems.

Thanks 

fjstjohn

---

### Post by dormant on 2007-09-27
PATH is an environment variable. It tells the computer where to look for programs. To see the list of directories, type

$ printenv PATH

In your example

PATH=/home/fjstjohn/progams/coot/bin/:$PATH - adds a new directory to your path.

PATH=/home/fjstjohn/programs/pymol - creates a new path with just one directory.

---

### Post by tszanon on 2007-09-27
Good to know your problem is solved. Please, edit the thread and mark it as SOLVED, so everyone who's having a similar problem can benefit.

---

