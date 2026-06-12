---
title: "X stopped working"
date: 2007-01-12
forum: General Help
---

### Post by Dragonstar on 2007-01-12
I have this strange problem.  I was on holiday 3 weeks and when came home noticed that X won't start, it just gives black screen and no response to anything. Everything had worked fine before this. Some struggling, and I found out that if I leave the lines

Section "Extensions"
Option "Composite" "Disable"
EndSection

out of xorg.conf, X starts but then I don't have direct rendering. I was using fglrx-driver at the time. Well, okay no direct rendering for now I thought. 

Today when I needed to reboot my pc, X didn't start at all, no matter what. I tried ati-driver which didn't help. Then I reinstalled ubuntu (but not /home dir, if it makes any difference) hoping it would help, but no, nothing changed after reinstall. I still got the black screen when starting X. I downloaded desktop cd for ubuntu 6.10 and tried to start my pc with it, but it gets stuck at the same way when starting X.

So now my X won't start except if I use vesa-driver which sucks big time. At the same time my old and crappy windows me works fine. I doubted my graphic card had got somehow broken by itself, but 'cos everything works fine in windows it can't be it? Any thoughts what's the problem here?

Ubuntu 6.10 32 bit
AMD Athlon 64 3200+
1GB RAM
ATI Radeon 9800 Pro

---

### Post by olejorgen on 2007-01-12
[http://ubuntuforums.org/showthread.php?t=318206](http://ubuntuforums.org/showthread.php?t=318206) maybe? It's a real mess

---

### Post by Dragonstar on 2007-01-12
That seems to be connected to nvidia's drivers, but thanks anyway.

---

### Post by olejorgen on 2007-01-13
aha, sorry. I didn't read your specs. The vacation part trigged my suspicion :)

---

### Post by Dragonstar on 2007-01-13
I tried my old geforce 2 and, surprise surprise, X starts fine with nv driver. This is really strange. With radeon X starts only with vesa driver, but at the same time windows works fine. With geforce X starts ok with nv driver. Can it really be that my graphic card is somehow broken?

---

### Post by Dragonstar on 2007-01-14
Found the problem. I reinstalled ubuntu without network connection and now X starts fine. So I guess the problem was with ati's drivers. It just sucks now that I don't know what packages I can upgrade.

---

