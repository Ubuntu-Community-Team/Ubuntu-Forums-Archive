---
title: "Ubuntu Sessions help"
date: 2007-08-28
forum: General Help
---

### Post by exclipse269 on 2007-08-28
I just Updated my Linux kernel to 2.6.22-10 and installed compiz-fusion onto my desktop. But when i tried to add compiz to sessions for it to run on startup. But when i logged out and logged back in to see if it worked compiz didn't startup. I did it again and saved the session and logged out again but it still didn't and my window borders were gone and sessions still didn't save my settings. Does anyone have any idea whats going on. I'm running ubuntu 7.04

---

### Post by bigbrovar on 2007-08-28
b4 u logged out the compiz fusion work?..and if it did was " compiz --replace -c emerald & " the command u used..if not try it that is the command to enable compiz to startup...by the way hope u have installed emerald..if not.go to synaptics search for emerald and emarald themes installed both...

---

### Post by exclipse269 on 2007-08-28
Yes both Compiz-Fusion and emerald worked the i used was compiz --replace and emerald --replace. but no matter what i add to sessions when i log out and back in the sessions manager doesn't save what put in. I've adding gaim to sessions to experiment and it also wasn't saved.

---

### Post by bigbrovar on 2007-08-28
well i really wish i could help u man but being a noob myself am very limited..anyway try make sure the in ur "session options"  ",automticlly save changes to session" is not checked...maybe that would help...by the way mke sure that the session are checked and enabled...

---

### Post by exclipse269 on 2007-08-28
I fixed it, all i had to do was edit the .profile file and added the startup script thanks for the trying to help.

---

