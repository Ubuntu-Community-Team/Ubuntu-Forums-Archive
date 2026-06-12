---
title: "Hard Drive not displaying"
date: 2013-09-05
forum: General Help
---

### Post by Elvis_Young on 2013-09-05
Hi, currently i'm using Windows 8 but i'm trying to dual boot. The problem is when I go through the setup, it tells me "the computer has no detected operating system" so I choose "something else" however my sda hard drive(the hard drive with Windows 8) does not show as one of my options. It shows my other two hard drives sdb and sdc. But the sda hard drive does show in the bootloader pull down menu. 

When I went to GParted partiton editor it also shows my sda hard drive. So if someone could help me so that I can install ubuntu 13.04 on my sda hard drive that would be amazing. 
Thanks

[ATTACH=CONFIG]246034[/ATTACH][ATTACH=CONFIG]246035[/ATTACH]

---

### Post by crazymonkey05 on 2013-09-05
well it could be windows causing the problem. how? windows 8 by default does not truly shutdown but instead goes into hibernation and when this happens it locks the HDD into an unreadable state and only windows can unlock it so the only way to stop that is disable hibernation in windows 8 which will cause it to have alot longer boot times here is a form to disable hibernation on windows [http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html](http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html)

---

### Post by Elvis_Young on 2013-09-05
Thanks for the quick reply and the suggestion, but when i tried it it still had the same result and didn't work.

---

### Post by Mark Phelps on 2013-09-06
You have to disable Fast Startup in Win8 to prevent it hibernating ... and when you do that, it will take a LOT longer to boot into Win8.

Also, be SURE to use the Win8 Disk Management utility to shrink any partitions.  Do NOT allow the Ubuntu installer to do this, as doing so risks corrupting the Win8 filesystem and rendering it unbootable.

---

### Post by Elvis_Young on 2013-09-07
Sorry for the late reply, but your suggestion also doesn't seem to work. I think i'll just use Windows 8 for now as it seems to be too much work to get Ubuntu to work. Thank you everyone for your help.

---

