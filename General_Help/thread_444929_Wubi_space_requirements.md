---
title: "Wubi space requirements"
date: 2007-05-15
forum: General Help
---

### Post by LegoAddict on 2007-05-15
So I was looking at the Wubi folder that I have on my drive and it's a whopping 10GB, while Windows is only about 2.  I'm assuming that's the Wubi framework, and not Ubuntu itself...


So if I want to install two Ubuntu flavours with Wubi, do I need to use another 10 GB, or does it use the same framework just making it maybe 2 GB?

---

### Post by ago on 2007-05-15
Those are rough guidelines for space allocation of system.virtual.disk:

base system: 1 GB
each desktop environment (including bundled apps): 2GB
typical amount of extra software: 2-4GB (synaptic can become quite addictive...)
if you want to try lots of games/extras: 4-6GB

Choose your size depending what you want to do.

A standard installation requires 2-2.5GB, but that includes the OS with all the software (open office, gimp, chat etc...). As for home.virtual.disk that depends on what you plan to put in there. Swap <= memory if you want hybernation (which, by the way, does not work on some systems...) otherwise 0.5 will do in most cases.

---

### Post by LegoAddict on 2007-05-15
Ah, so the 10 GB is actually me.  Ok.  That's still rather small for the amount of use I give my system.  I've found that hybernation doesn't work...


On a side note, to upgrade the Wubi framework, do I just run the installer?  Mine is quite different then what you say I should have, so I was thinking of backing up everything and reinstalling (primarily so I could triple boot Ubuntu Studio).

---

### Post by ago on 2007-05-15
> **LegoAddict said:**
> On a side note, to upgrade the Wubi framework, do I just run the installer?  Mine is quite different then what you say I should have, so I was thinking of backing up everything and reinstalling (primarily so I could triple boot Ubuntu Studio).

I do not reccommend to triple boot. Better to have 1 installation (Ubuntu) and add desktop packages to it. 
I did not check that, but It should be possible to add ubuntu studio to stock ubuntu by simply adding their repositories (see software-sources) and installing a few packages (ubuntustudio-desktop, ubuntustudio-audio...). Then you can simply logoff and before you logon you select in the option what desktop environment you want

---

