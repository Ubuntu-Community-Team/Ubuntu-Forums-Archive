---
title: "Need Help..."
date: 2006-08-29
forum: General Help
---

### Post by Vyizis on 2006-08-29
I have just installed ubuntu on my desktop PC again which has the following specs.

AMD xp2500+
Abit NF7 Nforce2 mb
ATI Radeon 9500pro

The problem is once i log on to the system it absolutely crawls, it takes about 20mins to get to the desktop screen. I have installed ubuntu on this machine before and i didnt get this problem and nothing has changed with the computer.

Anybody have any ideas?

---

### Post by zxee on 2006-08-29
Off the top of my head it sounds like the installer messed up your xorg.conf.
What does that file look like, and does it reflect the correct gpu (ati)?
Have a look at /etc/X11/xorg.conf and or post it here.

---

### Post by Vyizis on 2006-09-01
No i think the xorg.conf was fine. I solved the problem in the end by using a termainal and changing to the k7 kernal. I dont know why that solved the problem but it did.

---

