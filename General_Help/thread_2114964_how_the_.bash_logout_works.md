---
title: "how the .bash_logout works"
date: 2013-02-11
forum: General Help
---

### Post by rnerwein on 2013-02-11
hi
i recognized that the ~/.bash_logout only works when i log out from a console window. so what is the difference of log out from a GUI and log out from a console window. i tought log out is log out - isn't it  :confused:
cheers

---

### Post by schragge on 2013-02-11
I'd say, purely historical reasons. *bash* mimics behaviour of *csh* here that had *~/.logout*. In the seventies when csh was created, such thing as a GUI login/logout simply didn't exist.

On the other hand, you always can invoke bash with the -l option, or invoke *xterm* with the -ls option. The shell will then act as a login shell and execute *~/.bash_login* on entering the shell and *~/.bash_logout* on exiting it.

---

### Post by rnerwein on 2013-02-12
> **schragge said:**
> I'd say, purely historical reasons. *bash* mimics behaviour of *csh* here that had *~/.logout*. In the seventies when csh was created, such thing as a GUI login/logout simply didn't exist.

On the other hand, you always can invoke bash with the -l option, or invoke *xterm* with the -ls option. The shell will then act as a login shell and execute *~/.bash_login* on entering the shell and *~/.bash_logout* on exiting it.
hi
thanks for reply.
i know the history. but the GUI manager (here child of lightdm) can recognize the final logout.
i'll mark this thread closed.
cheers

---

