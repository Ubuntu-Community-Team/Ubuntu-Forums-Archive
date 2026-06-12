---
title: "Quad Core Conundrum"
date: 2008-02-04
forum: General Help
---

### Post by cj100570 on 2008-02-04
I'm currently running Gutsy with an Intel Q6600. I'm not big on pc gaming but I do have America's Army and Unreal Tournament 2004 installed. Recently I attempted to record a gaming session using gtk-recordMyDesktop and my machine and the game stuttered which is something it's never done before. it occurred to me that UT2K4 and recordMydesktop were probably running on the same core. I know it's possible in Windows to set a programs affinity for a specific core but I'm wondering if anyone knows a way to do this in Linux?

---

### Post by happyhamster on 2008-02-04
It should be possible using the 'taskset' command. Something like:

taskset -c 1 program1
taskset -c 2 program2

(You'd better thoroughly read up on it first though.) Keep us informed.

---

