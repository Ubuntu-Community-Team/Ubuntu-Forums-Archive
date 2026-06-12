---
title: "Attempted to make Wacom Tablet work, broke things"
date: 2007-01-04
forum: General Help
---

### Post by Ragzouken on 2007-01-04
As part of the beginning steps of getting my Wacom Volito 2 tablet to work I did:
```
sudo apt-get install wacom-tools
```
Now I have rebooted it's broken things. A constant highpitched note/sound is played (I encountered this sound before when attempted to get my wireless card to work), and the 'taskbar' and 'start bar' (I'm not sure what they are called in ubuntu) take a longer time to load up. The Terminal is also slow to become ready to use. Also the computer sometime freezes on the ubuntu 'loading screen'. Could someone please help me reverse the damage?

---

### Post by Ragzouken on 2007-01-05
It appears I gave up trying a reboot to early.

My attempts were just uninstalling the tools then dpkg-reconfigure xserver-xorg, although I didn't uninstall from the start which was probably my problem.

---

