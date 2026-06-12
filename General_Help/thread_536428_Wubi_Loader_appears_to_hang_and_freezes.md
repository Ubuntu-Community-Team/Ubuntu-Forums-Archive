---
title: "Wubi Loader appears to hang and freezes"
date: 2007-08-27
forum: General Help
---

### Post by baronne on 2007-08-27
Hi folks,
I am having a go at Wubi on my Dell Inspiron D520. All seemed to ok with the install, exept I have had real problems to actually get Ubuntu to load.
Initially it seemed like it was hanging on the bit where it says something like:
Loading Ubuntu
Filesystem type ntfs, etc. etc.

So I rebooted a few times to see if it was some weird blip, but no go. Then I spotted that you have to press Esc on the loader menus. The first menu you can choose the menu.lst - so I chose the wubi one, then you can press Esc again just when the loader starts and you can choose which Ubuntu kernel you want to run - original, recovery mode, etc.
Only very occasionally I manage to somehow get it to work if I Esc and go into those menus. Seems very odd. Could it be fragmentation on the disk or perhaps some other problem?
Any ideas would be great!!
cheers
Baronne

---

### Post by tuxcantfly on 2007-08-27
> So I rebooted a few times to see if it was some weird blip, but no go. Then I spotted that you have to press Esc on the loader menus. The first menu you can choose the menu.lst - so I chose the wubi one, then you can press Esc again just when the loader starts and you can choose which Ubuntu kernel you want to run - original, recovery mode, etc.
Only very occasionally I manage to somehow get it to work if I Esc and go into those menus. Seems very odd. Could it be fragmentation on the disk or perhaps some other problem?

To get a better diagnosis of the problem, first do the same process with "ESC", only before booting the "Ubuntu, kernel ... " entry, press "e", and it'll get you to another screen, go to the "kernel /wubi/boot/linux ... " line, press "e" to edit that line, and at the end, remove the option "splash", press enter, and press "b" to boot, and you should get more info; post the messages you get here. If you still don't get any info, do the same process, only in addition to removing "splash", also remove the "quiet" option as well, and press enter and press b to boot.

---

