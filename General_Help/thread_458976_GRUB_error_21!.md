---
title: "GRUB error 21!"
date: 2007-05-30
forum: General Help
---

### Post by Strákzi on 2007-05-30
Hello,
I have Linux ubuntu on my old computer and it was OK..

Last month I got a new computer with Winows Vista but Vista is a terrable system. Now I want to set op linux ubuntu on my new computer but I always get this error:

GRUB loading.. please wait...
Error 21

What can I do? I want to get away from this terrable Vista!

I hope someone can help me :)

Ps. sorry if my English is bad, I'm from Iceland :D

---

### Post by Michelpt on 2007-05-30
> Hello,
I have Linux ubuntu on my old computer and it was OK..

Last month I got a new computer with Winows Vista but Vista is a terrable system. Now I want to set op linux ubuntu on my new computer but I always get this error:

GRUB loading.. please wait...
Error 21

What can I do? I want to get away from this terrable Vista!


Hi, 

First of all, tell please if you still have dual boot with Vista or you have installed Ubuntu removing entire hdd? 

Any case you can follow this steps:
Probably first of all you have to check your BIOS Settnigs. There in the Boot menu you should check submenu Boot device priority or/and submenu "Hard Disks" and put that device you have Ubuntu installed (hdd) in the first place in the list. More, depending on BIOS version and type(not all BIOSes) you can find some option like "Write protected HDD", just I dont remember in which menu, but it is there. Mark this option to disable write protection. 

Then,  if this does not help (but I hope it helps) try to reinstall Grub from Live cd. How to reinstall Grub from Live CD you can find easy way (just four steps) here:
[http://ubuntuforums.org/showthread.php?t=224351 ]("http://ubuntuforums.org/showthread.php?t=224351")

Good luck :)

---

### Post by Strákzi on 2007-05-30
No, I have no dual boot, I'we format all the disk.

---

