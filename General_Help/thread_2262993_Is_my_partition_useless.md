---
title: "Is my partition useless?"
date: 2015-01-28
forum: General Help
---

### Post by john355 on 2015-01-28
I used gparted to install a new partition, but the partition seems useless.  I can see the partition in Disk Management, but it has no properties--it's empty.  I tried installing ubuntu on it--and I thought I succeeded--but the partition was empty after ubuntu stopped installing.  Disk Management shows the partition has 60.29 GBs available and 100% free space, but it also shows nothing listed under volume or file system.   What is wrong with my partition?  Hopefully, the screen shot below will help you help me.  Thanks
[ATTACH=CONFIG]259567[/ATTACH]

---

### Post by Mike_Walsh on 2015-01-28
Hallo, John.

After less than a year with Linux (though more than 35 with 'puters in general!), I believe your problem could be that you tried using gparted to create a partition under a Windows system. As I understand it, if you're attempting to free up space on a drive that is running Windows, in order to make room to install a Linux O/S, then that operation needs to be carried out using Window's own Disk Management tools; it will not work using gparted.

I assume you are attempting to dual-boot with Windows/Linux, i.e., run the two alongside each other on the same machine.

I'm more than willing to be corrected on this; I yet have MUCH to learn concerning Linux.....but I believe this is the root of your problem.


Regards,

Mike. ;)

---

### Post by efflandt on 2015-01-28
Windows knows nothing about Linux partition types, so Windows Disk Management never shows anything on Linux partitions. The question is, is it able to boot, or what does **gparted** or **sudo fdisk -l** (small L) show on it from live/install iso booted into a live system? And can it be mounted if you click on that ~60 GB partition from a live Linux system?

If the drive is failing, it might appear to format from Linux or even install. But if that part of the drive is failing, gparted might show a question mark for that partition afterwards.

---

### Post by Impavidus on 2015-01-28
Windows doesn't know about Linux partitions. If you installed Ubuntu there, it's only natural that Windows doesn't tell you. Why it says the space is not used I don't know. Windows cannot determine the partition type, so it has no way of knowing whether it's used or not.

Try looking at the partition using the tools on the Ubuntu live disk. Those will tell you if anything is on that partition.

---

