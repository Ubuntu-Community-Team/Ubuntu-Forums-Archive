---
title: "Ubuntu does not recognise my personal bin directory automaticly"
date: 2007-02-24
forum: General Help
---

### Post by Dylnuge on 2007-02-24
Hello,

My problem is that Ubuntu does not auto-add my personal ~/bin directory to the path.

This is my .bash_profile:
```
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
```

I know it runs, since my .bashrc works, and I know that the code is correct, because I ran the code in the terminal and then ran the results of an echo $PATH. However, if I do not run the code in every terminal I open, my bin directory is not in the path. However, my .bashrc file's code works perfectly (code such as autocoloring the ls and setting other aliases as well).

Thanks for the help,
-Dylan

---

### Post by taurus on 2007-02-24
Add these two lines to your ~/.bashrc.

```
PATH=$PATH:~/bin
export PATH
```

---

### Post by Dylnuge on 2007-02-24
That works! Thanks very much.

---

