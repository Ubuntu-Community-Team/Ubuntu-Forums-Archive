---
title: "Ubuntu/Windows Dual-Boot (Ubuntu First)"
date: 2007-10-11
forum: General Help
---

### Post by Roguespider13 on 2007-10-11
Every guide and post I've found for dual booting Ubuntu and windows I've found assumes that Windows was installed first. Not in my case. I built a machine and partitioned the drive so as to have a Windows partition but I installed Ubuntu first. How can I go about installing Windows XP and not disturb (or at least later fix) GRUB.

---

### Post by Scheater5 on 2007-10-11
Installing XP will cause grub no longer to show up on bootup, replaced by the windows boot manager.  However, Grub will not "disappear."  It's still installed, and to restore it boot into a live CD and issues these commands from a terminal (credit to Bulldog for this)


```

sudo grub


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


setup (hd0)

Finally exit the grub shell
```

---

