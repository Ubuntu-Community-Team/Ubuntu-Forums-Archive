---
title: "Can only boot 7.04 Feisty Fawn in Recovery Mode"
date: 2007-06-05
forum: General Help
---

### Post by fergalpoconnor on 2007-06-05
Hello,

I'm newly registered and not very familiar with this forum or with forums in general so my etiquette might not be perfect :)

I resized my disk using the Ubuntu Setup Tool to accommodate Ubuntu, Windows XP (which was on the disk to begin with) and a share partition.

Everything went fine and Ubuntu is set as the default OS under GRUB. Ubuntu will not boot though in Normal Mode. The Screen just goes black. When I reboot and choose Ubuntu (recovery mode) it goes through various checks but the GUI loads normally after a few minutes.

Windows XP works fine.

Any ideas?

---

### Post by adampyre on 2007-06-05
One thing that I do if I have issues booting, when you get the "black screen of death" hit alt + F1 to take you into a console, login with your username and password and then type startx, the command for starting the xwindows environment (probably Gnome) it probably won't load X but will give you an error message as to why it won't load. Try that and you can post back here what the issue might be. Also, I am doing this from memory, if ALT + F1 doesn't get you into a terminal, try CTRL+ALT+F1.... 

good luck.

---

