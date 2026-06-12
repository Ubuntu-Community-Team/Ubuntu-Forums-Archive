---
title: "how do you update from behind proxy?"
date: 2005-10-27
forum: General Help
---

### Post by susa on 2005-10-27
I am behind a corporate proxy and can browse web fine by plugging in the proxy server address but am unable to run updates, everything fails to connect to the listed items in sources.list

what's the trick? I have no other way to connect, other than behind corp proxy server

---

### Post by mlomker on 2005-10-27
[Try this.]("http://www.ubuntuforums.org/showpost.php?p=364026&postcount=2")

---

### Post by susa on 2005-10-28
ok, so the file now looks like this, and still I am unable to update from behind proxy

**

# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" -a -r /etc/debian_chroot ]; then
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
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

export http_proxy=http://myID:pass@myDomain.com:8080/
export ftp_proxy=http://myID:pass@myDomain.com:8080/

---

### Post by susa on 2005-10-28
ok, I now understand I was supposed to first open a command window and type

apt-get update

---

