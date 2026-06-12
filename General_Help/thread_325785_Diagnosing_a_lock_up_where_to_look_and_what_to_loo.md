---
title: "Diagnosing a lock up: where to look and what to look for?"
date: 2006-12-26
forum: General Help
---

### Post by Schluppy on 2006-12-26
I've got a curious problem with certain applications locking up the system and I'm wondering how I would go about diagnosing the issue.

The apps that have repeatedly frozen the system are gnome-screensaver-preferences and openoffice.org.

I believe that it has something to do with X and 3D (or lack thereof) but don't have a clue how to go about diagnosing or fixing the issue.

I've poured through /var/log looking for a hint but have come up short.

For reference I'm running edgy with 3 displays on 2 video cards: an ATI 8500LE AGP pushing display 0 and a Radeon 7000 PCI pushing displays 1 and 2 - both cards using the OSS driver. Any sort of 3D app appears to lock the system also; glxgears, even glxinfo causes a total freeze.

The only errors X shows are:
```
(EE) AIGLX: Screen 1 is not DRI capable
(EE) AIGLX: Screen 2 is not DRI capable
```

Any tips? Perhaps a known issue?

Note that it's a complete lock-up requiring a hard reset.

UPDATE: Solved the problem by disabling AIGLX in Xorg.conf. 

Adding...
```
Option  	"AIGLX" 	"off"
```
... to the "ServerLayout" section did the trick. 

Turns out I was googling the wrong keywords. ](*,)

---

