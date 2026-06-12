---
title: "N00b help: severe problem with bash"
date: 2007-05-08
forum: General Help
---

### Post by carlwillis on 2007-05-08
I'm a new user of Ubuntu ("feisty fawn"), which is running on a machine that also has Windows XP on another HD.  Everything has been fine...until today, when I installed a program called fs-driver in XP in order to see my three Linux ext3 partitions (which live on a separate HD from XP).  Then...serious trouble, as described below.

When I attempt to launch a terminal now, the following errors appear: 

[I]bash: lesspipe: command not found
bash: The: command not found
bash: sudo: command not found
bash: dircolors: command not found
bash: The: command not found
bash: sudo: command not found
bash: uname: command not found
bash: uname: command not found
bash: [: too many arguments
[about 20 of these...]
bash: sed: command not found
bash: complete: is: no completion specification
bash: complete: currently: no completion specification
bash: complete: not: no completion specification
bash: complete: installed.: no completion specification
bash: complete: You: no completion specification
bash: complete: can: no completion specification
bash: complete: install: no completion specification
bash: complete: it: no completion specification
bash: complete: by: no completion specification
bash: complete: typing:: no completion specification
bash: complete: apt-get: no completion specification
bash: complete: install: no completion specification
bash: complete: sed: no completion specification
bash: manpath: command not found[/I]

Obviously, this is problematic (I cannot even use "sudo".)  Perhaps it matters that I note that my /home is a separate partition from my Ubuntu installation.   By the way, attempting to reinstall the core utilities package, etc. does NOT help. 

Any assistance on where to how to fix this in a timely manner would be most appreciated.  If you want to see any other scripts or files on my system, let me know and I will toss them up here.

Thanks,
Carl

---

### Post by earobinson on 2007-05-08
can you copy and paste the output from cat ~/.bashrc, im betting you have changed it.

---

### Post by carlwillis on 2007-05-08
Cat does not work for me: 

[I]The program 'cat' is currently not installed.  You can install it by typing:
sudo apt-get install coreutils
bash: cat: command not found[/I]

Echo works, maybe this is something?

[I]carl@cwillis-linux:~$ echo $PATH
/opt/intel/idb/9.1.043/bin:/opt/intel/fc/9.1.043/bin:/usr/local/bin[/I]

You'll note some paths to stuff I installed recently, and added to my .profile in /home.  For some reason the profile, the bashrc, etc.  in /etc is not being adequately found??  These should hold the right paths to /usr/bin and so forth where ls, sudo, and so forth are properly found.

Thanks for the fast reply.

-Carl

---

### Post by earobinson on 2007-05-08
> **carlwillis said:**
> Cat does not work for me: 

[I]The program 'cat' is currently not installed.  You can install it by typing:
sudo apt-get install coreutils
bash: cat: command not found[/I]

Echo works, maybe this is something?

[I]carl@cwillis-linux:~$ echo $PATH
/opt/intel/idb/9.1.043/bin:/opt/intel/fc/9.1.043/bin:/usr/local/bin[/I]

You'll note some paths to stuff I installed recently, and added to my .profile in /home.  For some reason the profile, the bashrc, etc.  in /etc is not being adequately found??  These should hold the right paths to /usr/bin and so forth where ls, sudo, and so forth are properly found.

Thanks for the fast reply.

-Carl
Ok try ```
/bin/cat ~/.bashrc
```

---

### Post by carlwillis on 2007-05-08
Here is /home/carl/.bashrc as displayed via GNOME:

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
source /opt/intel/fc/9.1.043/bin/ifortvars.sh
source /opt/intel/idb/9.1.043/bin/idbvars.sh

---

### Post by carlwillis on 2007-05-08
> **earobinson said:**
> Ok try ```
/bin/cat ~/.bashrc
```

This works.  See the text I just posted.

---

### Post by 542 on 2007-05-08
To temporarily get your core applications back (cat, less, etc) try running the following commands:

PATH="$PATH:/bin:/usr/bin"
export PATH

---

### Post by 542 on 2007-05-10
Hi Carl, still having problems with this?

---

