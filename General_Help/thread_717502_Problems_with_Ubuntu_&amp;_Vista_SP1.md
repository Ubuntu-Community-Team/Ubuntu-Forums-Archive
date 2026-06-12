---
title: "Problems with Ubuntu &amp; Vista SP1"
date: 2008-03-07
forum: General Help
---

### Post by SebK on 2008-03-07
**Hi,**

I had an old build of Vista SP1, and I wanted to uninstall it. So I uninstalled the Service Pack for Microsoft Windows (*KB936330*) and followed the instructions that appeared on the screen to complete the uninstall process. 

During step 2/3, my PC rebooted and it doesn't work anymore. I get the Vista boot screen, I wait for about 5mins, then a black screen appears and that's it. I tried to insert my Vista CD to repair, but after loading the CD files, I get the same black screen, as if something was loading. I tried to reboot in safe mode, doesn't work either. I waited on the black screen(s) for more than 3 hours, nothing. 

Luckily, a few days ago, I installed Ubuntu [dual-boot]. I can still access my files from Ubuntu, but internet *doesn't* work on it. Is there a way I can fix/format/do something to repair Vista? Can I reinstall Vista via Ubuntu? Halp!

*Cheers,*
**SebK**

---

### Post by nlz on 2008-03-07
Install gparted from the repositories and format the vi$ta partition. If you want to add those partition to your /home or /, then you'll have to download te gparted cd because these partitions have to be unmounted to be enlarged or shrinked. If you want to reinstall Vista or XP, you don;t need the gparted livecd since ubuntu partitions are untouched..

The internet should just work if it has always worked in Ubuntu..

---

### Post by SebK on 2008-03-07
> **nlz said:**
> Install gparted from the repositories and format the vi$ta partition. If you want to add those partition to your /home or /, then you'll have to download te gparted cd because these partitions have to be unmounted to be enlarged or shrinked. If you want to reinstall Vista or XP, you don;t need the gparted livecd since ubuntu partitions are untouched..

The internet should just work if it has always worked in Ubuntu..

I use a PPPoE connection and it doesn't work in Ubuntu. How can I install gparted? Is there a way I can backup my files?

---

### Post by nlz on 2008-03-08
you install gparted from synaptic ( system > administration > synaptic )
you can download the liveCD by google-ing  gparted livecd dowload.

if you can back up your files depends on what filesystem vista used. you can check it with the system monitor (system > administration > system monitor ) and then click tab file systems..

if you found out what filesystems vista is own, look it up on this forum, a lot has been written about that topic.

---

