---
title: "Going from small to full screen | hangs | Firefox"
date: 2015-04-13
forum: General Help
---

### Post by warlord-of-death-87 on 2015-04-13
Hi

I have Ubuntu 14.04 installed and when I'm using firefox, going from a small window to full screen or vice versa, when watching a video, firefox lags a lot and will "grey out" being unable to close without force quitting it or killing the process. This happens with any quality of video, 1080p, 720, 480 etc etc. 

I realize it's probably a long shot that someone may know the issue as there isn't much more info I can specify besides what I've already said. But maybe someone else has ran into this problem as well?

Thank you

---

### Post by dino99 on 2015-04-13
you probably does not have 3D acceleration enabled, or the hardware cant support it. Which is the graphic card/chipset and how much ram installed ?

---

### Post by warlord-of-death-87 on 2015-04-14
4gb ram
   AMD A10-4600M 2.3GHz APU with Radeon(tm) HD Graphics 
   
Radeon HD 7660G
1Tb hard drive

It has one of the switchable graphic cards, where it switches to a (i think) 7470 when not gaming and to the 7660 when playing a game. Not sure if it is even working on ubuntu though. I previously had win 7.

---

### Post by dino99 on 2015-04-14
you probably need to purge the graphic installed driver, then install back fglrx
[http://askubuntu.com/questions/453902/problem-in-setting-up-amd-dual-graphics-trinity-radeon-hd-7660g-and-thames-ra](http://askubuntu.com/questions/453902/problem-in-setting-up-amd-dual-graphics-trinity-radeon-hd-7660g-and-thames-ra)

---

### Post by warlord-of-death-87 on 2015-04-17
Before I tried that, I downloaded chrome and it works perfectly. Must be a bug in firefox or something? Thanks for the help.

---

