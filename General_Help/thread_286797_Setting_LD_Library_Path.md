---
title: "Setting LD_Library_Path"
date: 2006-10-28
forum: General Help
---

### Post by Apple 101 on 2006-10-28
Hi everyone,

I would like to set the LD_Library_Path environment variable for Ubuntu 6.06.  I have read other posts on similar topics, but am still confused with how to do this.

In my .bash_profile, there is the following:
```

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

How should the LD_Library_Path environment variable be added to this file?

Thankyou for your help.

---

### Post by Apple 101 on 2006-10-28
Hi everyone,

I managed to solve this issue by doing the following:

1. gksudo gedit /etc/ld.so.conf
2. Adding the path to the shared libraries (/path/to/libraries).


I hope that this can help someone at some stage.

---

