---
title: "Bash history not working"
date: 2008-06-27
forum: General Help
---

### Post by ddell on 2008-06-27
Greetings,

My bash 'history' used to work fine in Hardy, then after doing a complete reinstall, hitting the up arrow just gives a system beep error.  Well, it does if am in an already running session. 

Have tried fixes to append history from previous sessions, with my bashrc as this right now:

```

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

#Extract things. Thanks to urukrama, Ubuntuforums.org	
extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}

```


That I took from one of the other posts about customised bashrc files - hoping it would solve my problem - but still nothing!

Any help would be greatly appreciated - general searches for 'bash history not working' have yielded nothing so far!

Thanks.

---

### Post by p_quarles on 2008-06-27
Is it actually not recording the history, or is the shortcut for retrieving past commands (the up arrow) just not working correctly?

In other words, does typing
```
history
```
give you the list of recent commands.

---

### Post by ddell on 2008-06-27
It is recording history, but not from different terminal sessions.

The last fresh install it worked fine from session to session, this time it did not, right from the start.

In other words if I close the terminal and open a new one, it reads the history as blank.

---

### Post by kevinpercy on 2008-06-27
I landed here after searching.
My bash history disappears intermitantly, that is I have yet to track down the cause.

will try to figure out why and when, any advice appreciated.

Kubuntu Hardy heron

---

### Post by apmcd47 on 2008-06-27
> **ddell said:**
> It is recording history, but not from different terminal sessions.

The last fresh install it worked fine from session to session, this time it did not, right from the start.

In other words if I close the terminal and open a new one, it reads the history as blank.

What are your HIST* environment variables set to? The important ones are HISTFILE, HISTFILESIZE and HISTSIZE. I tend to set my HISTFILESIZE to zero, so that my history dies with my session - that is my HISTFILE is not written to. HISTFILE should be a file writable by you. Is it? What is currently in that file? If HISTFILE is not set then bash should be using ~/.bash_history - same questions.

Hope this helps.

Andrew

---

### Post by thedrunkduck on 2008-08-21
I had the same problem (or at least I think). The command history was not saved for normal users. The problem was the permission of the .bash_history file.

---

### Post by russelld on 2010-08-14
I had the same problem and fixed it with the hints in above posts

1) echoed the variable  HISTFILE to find where it is
```

:~$ echo $HISTFILE
/home/rd/.bash_history

```

2) had a look inside the file
```

:~$ cat /home/rd/.bash_history
cat: /home/rd/.bash_history: Permission denied

```

maybe this could be it  :confused: 

3) did a full file listing 
```

~$ ls -la  /home/rd/.bash_history
-rw------- 1 root root 34 2010-08-09 12:58 /home/rd/.bash_history

```

  found it!!!!  root has perms for the user history file :o

4) changed user and group for user history file
```

:~$ sudo chown rd:rd  /home/rd/.bash_history

```

5) closing the terminal and restarting and running history
```

:~$ history
    1  exit
    2  f
    3  du
    4  duh
    5  du --max-depth=1 -h
    6  history | tail
    7  cat .bashrc
    8  history
    9  echo $HISTFILE
   10  cat /home/rd/.bash_history
   11  ls -la  /home/rd/.bash_history
   12  sudo chown rd:rd  /home/rd/.bash_history
   13  ls -la  /home/rd/.bash_history
   14  echo $HISTFILESIZE
   15  echo $HISTSIZE
   16  history
   17  exit
   18  history

```

awesome!!! history is back!!! :D

---

### Post by deesto on 2010-09-17
Glad you were able to work this out.  But the cause of the problem is baffling to me: why would root need to own the user's bash history file?  This seems to be consistently the case as well: on a fresh install of lucid, root does indeed own ~/.bash_history ... strange.

---

### Post by ataris_kid on 2010-11-09
Thanks.. Was having this issue as well. Seems strange that root would own it by default.

---

### Post by sureshsaragadam on 2011-11-30
[B]You can try an alternative 
[/B]
Just delete the file .bash_history in your home folder,  and create an other file with the same name
[SIZE=2]
[/SIZE][SIZE=3][SIZE=2][SIZE=1]change to your home folder $cd /home/abcdefg then
[/SIZE]
$rm .bash_history
$touch .bash_histor[/SIZE]y
[/SIZE]
while i am unable to access history file through history command, 
i deleted the history file and created the same file, then it worked file, 
with the default permissions.

---

### Post by nothingspecial on 2011-11-30
And we bid you good night, good night, good night.......

---

