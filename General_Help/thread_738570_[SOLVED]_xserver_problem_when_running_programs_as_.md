---
title: "[SOLVED] xserver problem when running programs as different user"
date: 2008-03-28
forum: General Help
---

### Post by sstusick on 2008-03-28
I tried running programs as a different user and I get this error:

> frank@stu-laptop:/home/stu$ kopete
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-11467' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kopete: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-11456' to 'kopete'
kopete: ERROR: Communication problem with kopete, it probably crashed.


Anyone know how to fix this? It happens with any program I try, I used to be able to do it on Feisty.

---

### Post by sstusick on 2008-03-30
Bump

---

### Post by monraaf on 2008-03-30
Try this:

```
xhost +local:
```

---

### Post by sstusick on 2008-04-11
Hey thanks! That worked!

---

