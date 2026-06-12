---
title: "bash_profile .. HUH ?1"
date: 2007-01-19
forum: General Help
---

### Post by israphelr on 2007-01-19
Hi everyone.

I'm just a little confused with something.

I've been playing around with permissions on the .bash_profile file.


All of a sudden I can't seem to find the P$1 variable thingie anywhere,here's what my current .bash_profile looks like.


# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

Also, Is **PATH=~/bin:"${PATH}"** meant to be like that? I thought it was meant to be...
[B]
PATH=$PATH:$HOME/bin[/B]

Thanks in advance for any help.

---

### Post by taurus on 2007-01-19
It should be in either /etc/bash.bashrc or /etc/profile.

```
PATH=$PATH:~/bin
```

---

### Post by israphelr on 2007-01-19
Thanks, problem solved,

---

