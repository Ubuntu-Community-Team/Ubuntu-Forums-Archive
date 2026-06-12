---
title: "'W' not showing LTSP users"
date: 2008-06-09
forum: General Help
---

### Post by plengnom on 2008-06-09
On my new hardy installation 'w' is not showing users logged in on the thin clients. Its a fairly standard install, except I'm using GDM instead of LDM. 

W shows this:
> USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
root     pts/0    localhost        08:39    0.00s  0.00s  0.00s w
kurs412           192.168.0.235:6  08:39    8:44   1:43m  0.02s /bin/sh /home/kurs412/.Xsession

Root is me. kurs412 is running a little script i .xsession and is showing up, but without anything on TTY.  

Several others users are logged in aswell (they don't have an .xsession), but not showing here. They do show up in last though.

I guess it has something to do with gdm and umtp, but what exactly?

---

### Post by p_quarles on 2008-06-09
What's the output of
```
users
```
?

---

### Post by plengnom on 2008-06-09
The same as W. 

Weird, 2 seconds ago both w and users showed one other user logged in. Then nothing. Then one user again. Hmpf!

edit: seems to show the last user that logged in - and the nothing when someone logs out.

---

### Post by plengnom on 2008-06-09
Solved.. kinda. 

Seems to be an GDM issue, as everything is as it should with LDM and KDM. Switched to KDM now; I hope the bug that made me switch go GDM in the first place is fixed.. :)

---

