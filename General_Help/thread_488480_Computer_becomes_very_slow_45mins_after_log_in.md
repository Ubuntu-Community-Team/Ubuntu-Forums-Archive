---
title: "Computer becomes very slow 45mins after log in"
date: 2007-06-30
forum: General Help
---

### Post by wersdaluv on 2007-06-30
Everytime I log in, after about 45 minutes, Feisty becomes very very slow. What I mean by that  is, switching desktop becomes very slow, mouse freezes, music continues but also skips sometimes, system responds very slowly to mouse clicks, etc.

What could be the reason why my system becomes slow after a period of time?

---

### Post by BobbyBionic on 2007-06-30
Hi

Do you have a 3D Desktop ? What's the result of the top command ?

---

### Post by wersdaluv on 2007-06-30
I have 3D desktop installed but I do not run it.

What command are you referring to? 3ddesk? If so, here is the output...
```
3ddesk
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)


```

---

### Post by tgalati4 on 2007-06-30
In a terminal:

>sudo apt-get install htop

>htop

Examine the processes that are hogging your machine then kill them.

Make a note of these offenders then search the forums to see if others have similiar problems.

Good luck.  Your CPU cycles are yours.  You paid for them.

---

