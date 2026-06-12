---
title: "No Desktop Effects"
date: 2008-05-05
forum: General Help
---

### Post by sharkbite1414 on 2008-05-05
Hey Everyone I have 8.04 and everything is going fine except I can't enable desktop effects. My graphics card is more than powerful enough in both my Desktop and laptop but I can't enable the Effects.:confused: Does anyone else have this problem? It's nothing I can't live without, but still it would be nice to have them.:)

---

### Post by agentsmith23 on 2008-05-05
run this command in a terminal:

compiz --replace


post the results you get

---

### Post by Rocket2DMn on 2008-05-05
If your card is using the open source ati drivers, you need to follow this guide to allow for desktop effects in Hardy - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
That is to say, if your video card is an ati radeon 9500 or older you will need to follow that guide.  Newer ati cards use restricted drivers that are officialy supported in Compiz.

---

### Post by fignig on 2008-05-05
> **agentsmith23 said:**
> run this command in a terminal:

compiz --replace


post the results you get

wow do not do that command in the terminal, DO NOT LISTEN TO HIM

---

### Post by agentsmith23 on 2008-05-05
sorry if i told him to do something very wrong. but could you please tell me why this is bad?

---

### Post by CarnivorouZ on 2008-05-06
There is a lot of problems right now with Ubuntu and ATI cards.  At least when it comes to the desktop effects.  I run a Radeon x1650 and I can't enable desktop effects.  I have posted numerous posts in this forum without a resolution.  the best I can get is enabling my card with the current driver, yet when I run compiz in terminal, or I try to enable effects; it will switch to a white screen.  Hope someone resolves this issue soon.

---

### Post by sharkbite1414 on 2008-05-08
I have a Nvidia® Geforce 8600GT 256MB PCI-E Graphics Card in my Desktop and ATI Readon 6100 in the laptop.

---

