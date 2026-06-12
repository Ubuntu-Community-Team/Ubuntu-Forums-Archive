---
title: "updates always change grub!"
date: 2008-06-20
forum: General Help
---

### Post by belovedmonster on 2008-06-20
I log into my Xubuntu partition every few weeks, and when I do I run the update. Next time I start my computer I will find the boot menu defaults to some memory test thing and not my previous default. What is going on here?

---

### Post by Zorael on 2008-06-20
Some updates call update-grub to regenerate your menu.lst, commonly when adding/removing kernels.

I suggest using Startup Manager (package name **startupmanager**) - or by manually editing menu.lst - to change which kernel is set to default, how many kernels should be displayed, disabling memtest entries, etc. If you do it the manual way, the comments there are quite explanatory.

---

### Post by drs305 on 2008-06-20
Here is a link that explains the ways to change the display at boot via startupmanager or via editing the menu. I strongly recommend StartUp-Manager vs editing grub's menu.lst.

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

