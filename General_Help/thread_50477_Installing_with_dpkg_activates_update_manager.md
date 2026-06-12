---
title: "Installing with dpkg activates update manager"
date: 2005-07-20
forum: General Help
---

### Post by emoui on 2005-07-20
Hi

Recently I have downloaded, compiled and installed mplayer on Ubuntu Hoary. To download and compile mplayer I used apt-src (apt-src install, apt-src build). Then I installed mplayer with dpkg -i and after installation the update manger activated and informed me that package mplayer needed to be updated. To my suprise the update manger wants to update mplayer to the same version , which was installed with dpkg. Does anybody have an idea why this happened and how to tell update manager that the version installed is the newest one? I observe the same behaviour of the update manager with other applications compiled with apt-src and installed with dpkg. Do I make any mistake?

emoui

---

### Post by Xian on 2005-07-20
The easiest way would probably be to just place a hold on that package:
```
$ sudo apt-get install wajig
$ sudo wajig hold mplayer
```

---

### Post by emoui on 2005-07-22
[QUOTE=Xian]The easiest way would probably be to just place a hold on that package:
```
$ sudo apt-get install wajig
$ sudo wajig hold mplayer
```[/QUOTE]


Thank you very much for your suggestion, but to me it seems to be partial solution. I would like to find out, whether I make mistake or there is a bug in update manager. Update manager should not insist on updating any package if the latest version is installed. 

emoui

---

