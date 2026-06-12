---
title: "Bash Prompt Dollar Sign"
date: 2012-10-19
forum: General Help
---

### Post by Atbash on 2012-10-19
I'd like to change the dollar sign in my bash prompt that indicates user instead of root to some other symbol.  Is that difficult?  :confused:

---

### Post by Vaphell on 2012-10-19
no

```
$ grep PS1 ~/.bashrc
[ -z "$PS1" ] && return
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]**\$** '
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w**\$** '
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
```
this is how the prompt string is defined using PS1 variable. See that \$ at the end of the first 2 lines? That's your $ right there (1st line is with color, 2nd is without)
Modify .bashrc (it's hidden so press ctrl+h in your home dir)

---

### Post by nothingspecial on 2012-10-19
Duplicate thread here

[http://ubuntuforums.org/showthread.php?t=2072923](http://ubuntuforums.org/showthread.php?t=2072923)

[IMG]http://imageshack.us/a/img69/5481/suddenlyamuffin.jpg[/IMG]

---

