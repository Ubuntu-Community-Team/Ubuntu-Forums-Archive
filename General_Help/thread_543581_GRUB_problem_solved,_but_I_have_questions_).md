---
title: "GRUB problem solved, but I have questions :)"
date: 2007-09-05
forum: General Help
---

### Post by Nachimir on 2007-09-05
I just had a problem with grub, which is solved, and I'm wondering if anyone can shed any light on what caused it.

Briefly:
Something caused Grub to start looking for Ubuntu on the wrong partition, yet I'd made no changes to the physical configuration of my drives, nor had I edited anything to do with them in Ubuntu or Grub.

Easy to fix, but what caused it mystifies me.


Details:
I'm running a dual boot system with XP and Feisty. I've made no changes to the hard disks or BIOS in the last week, nor have i touched fstab. In fact, the only changes to the system in months have been Ubuntu updates. It has three hard disks, with XP on one with a couple of other partitions, Feisty on another disk with swap and two other partitions, and the third HDD is general file storage.

I last used it on monday and everything seemed fine. This morning, on boot, grub loaded, could start WinXP ok, but every Ubuntu kernel option caused it to return "Error 15 file not found".

The first thing I tried was restoring grub, both from a live CD terminal and a grub boot CD. In both cases, the prcedure would stall on "find /boot/grub/stage1" with Error 15.

I rebooted, poked around a little in the grub menu, and found it was trying to boot Ubuntu from (hd1,0). So using the edit command from the grub menu, tried booting ubuntu from (hd0,0). It worked.

Once back into my installed copy of Feisty, I again tried restoring grub from a terminal window, but it couldn't find /boot/grub/menu.lst. It was still there of course, it just seems it was looking on the wrong partition. Editing it manually, I changed all of the kernel entries from (hd1,0) to (hd0,0) and, upon rebooting, grub works perfectly again.

Any idea what might have caused menu.lst entries to change to (hd1,0), or (hd1,0) to become an incorrect designation?

---

### Post by rsambuca on 2007-09-05
There was a kernel update recently which also updates your grub.  Have you made any changes to your setup since the last kernel upgrade, which was some time ago?

---

### Post by Warren Watts on 2007-09-05
I have a PC that I triple boot Ubuntu, Wolvix and FreeDOS on, and the last kernel update re-wrote my GRUB menu.lst file.  It completely removed my entries for Wolvix and FreeDOS.
Luckily, I had just edited menu.lst the day before and created a backup, so all I had to do was cut and paste my other boot option back into menu.lst.

This is the sort of thing that throws newbies off Ubuntu and Linux.  If I were less experienced, I would have been baffled.

---

### Post by louieb on 2007-09-05
> **Warren Watts said:**
> It completely removed my entries for Wolvix and FreeDOS.


Make sure your entries for other OS'es are outside  the automagic section. If you had them inside; a kernel update is going to wipe them out or at the least mess them up so bad they won't boot.   

> **Nachimir said:**
> ...Any idea what might have caused menu.lst entries to change to (hd1,0), or (hd1,0) to become an incorrect designation?


Look for the **groot**  statement line, it is used at kernel update time when the new kernel entry is written your menu.lst.

---

