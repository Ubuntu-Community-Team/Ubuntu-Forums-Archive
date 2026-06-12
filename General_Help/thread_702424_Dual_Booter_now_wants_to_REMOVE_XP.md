---
title: "Dual Booter now wants to REMOVE XP"
date: 2008-02-20
forum: General Help
---

### Post by strange_cathect on 2008-02-20
Hello,

I am currently dual booting XP and Ubuntu.  Now that I've found a way to use wine to make use of my one killer ap, I no longer need XP for anything and want to clear my life of Microsoft.

Here's my problem: I want to get rid of the XP and reclaim the disk space, but I want to make sure that I do this safely so that I don't screw up my boot to Ubuntu.

I thought about just deleting the XP partition that I have using Gparted, but I'm not sure if that might break my system.

Can anyone share any wisdom on this problem?

Thanks.

---

### Post by p_quarles on 2008-02-20
Deleting the XP partition will essentially break the bootloader, but that's relatively straightforward to fix (by reinstalling GRUB):
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Battie on 2008-02-20
> **strange_cathect said:**
> Hello,

I am currently dual booting XP and Ubuntu.  Now that I've found a way to use wine to make use of my one killer ap, I no longer need XP for anything and want to clear my life of Microsoft.

Here's my problem: I want to get rid of the XP and reclaim the disk space, but I want to make sure that I do this safely so that I don't screw up my boot to Ubuntu.

I thought about just deleting the XP partition that I have using Gparted, but I'm not sure if that might break my system.

Can anyone share any wisdom on this problem?

Thanks.

I have done this.  It is, technically, safe, but backup your valuables anyway.  My original setup was a Linux partition, a Windows partition, and Linux home, Windows documents, and swap.  I deleted the Windows partitions and merged them with my home partition.

Once you're in GParted it's fairly straightforward, but be warned that if you have a large drive it will take a loooong time (the last time I rearranged it took over four hours to complete on a 500 GB SATA!)

When I did this, GRUB was not messed up.  I just commented out the Windows boot information afterward.  Of course, since ymmv, keep a copy of Super Grub Disk just in case.

Good luck!

---

