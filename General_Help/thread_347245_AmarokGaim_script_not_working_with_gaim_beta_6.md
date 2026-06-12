---
title: "AmarokGaim script not working with gaim beta 6"
date: 2007-01-27
forum: General Help
---

### Post by shanepardue on 2007-01-27
The AmarokGaim script shows what music you are listening to in place of your status message on gaim and ever since the update to beta 6, the status hasn't been replaced by the music info. It only says media. Anyone getting this problem or find a solution?

---

### Post by donmiguel on 2007-02-14
have you found a solution?

i have the problem as well. and i am so clueless about what to do:

the dependencies are the following:

 * Gaim with D-Bus support (Tested on Gaim 2.0.0beta5)
 * Python with D-Bus support
 * DCOP client

but i don't know how to check if my gaim has d-bus support.. i must be looking in the wrong direction while searching, i don't know...

---

### Post by metalcoat on 2007-02-22
Do you have a DCOP client?
Does it also have Dbus support built into your builds?
If not the repository below does and works with the plugin (gaim v2.0.0 beta6)

Repos:
```

deb http://www.elisanet.fi/mlind/ubuntu edgy main
deb-src http://www.elisanet.fi/mlind/ubuntu edgy main

```

Good Luck

---

