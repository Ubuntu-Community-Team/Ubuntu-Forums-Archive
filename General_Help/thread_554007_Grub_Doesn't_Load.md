---
title: "Grub Doesn't Load"
date: 2007-09-18
forum: General Help
---

### Post by ejacobi on 2007-09-18
Alright, to preface, I have Windows XP Professional and Ubuntu installed on the same SATA HD on different partitions. Windows XP is on partition #1, Ubuntu on #2, Swap on #3 and an additional 2GB Fat32 on #4. When I installed Ubuntu for the first time, and when I update it, etc, I also change the Grub record so Windows is the first to load by default. I started with Feisty and am now using Gutsy Tribe 5. I restarted today, and noticed that Grub did not load... it just went straight to Windows. It had been working up until today, and I don't know what is wrong. I tried reinstalling Ubuntu Gutsy, being careful to mark partition #2 as "/" and to make sure that boot (for grub) would be on hd0,1 (which is where it's always been) and now it's not working. Can anybody shed light on this?

---

### Post by jamvegan on 2007-09-18
If you haven't reinstalled Windows, or restored the MBR via Windows, then grub is probably still loading.  There are a couple of settings in /boot/grub/menu.lst that could make it appear that grub is not loading.  The first is timeout.  If it is set to 0 then I believe that grub will just boot directly into the default OS without showing you the menu.  The other is hiddenmenu.  This causes the menu not to display, but you do get some sort of splash screen that you can hit escape during to get to the menu.  If it's not either of those then I can't imagine what it is, unless it's an issue with Gutsy (which I have not played with, yet).

---

### Post by ejacobi on 2007-09-18
I checked the Grub settings... timeout is set to 3, and I disabled hidden menu, but still now luck. Windows loads without me ever seeing Grub whatsoever.

---

