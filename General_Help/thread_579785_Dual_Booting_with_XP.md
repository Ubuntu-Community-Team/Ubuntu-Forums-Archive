---
title: "Dual Booting with XP"
date: 2007-10-18
forum: General Help
---

### Post by AlexanderH on 2007-10-18
I just burned off the latest version of Ubuntu to disk and started to run it.  I'm converting both of my PCs (desktop and Laptop) to linux over the next few days. Each has a large amount of data on them, consisting of photos, music(to a smaller degree), project data (maya, photoshop, manga studio)  as well as many of my Development packages such as those mentioned previously.  While my Desktop has two hard drives by laptop only has one, but i don't want to lose my data when ubuntu formats the drive to install it self, which is what i believe will happen since i kept having trouble choosing any other option because the partitions gave a error message regarding "root" something and to correct it in the partition menu or something like that.  

My question is,  what method should i try to dual boot Ubuntu 7 onto my one Hdd laptop without losing the ability to boot into windows when necessary?  Is it possible to do this without damaging or losing all my windows-side data?

Thank you for your assistance.

---

### Post by p_quarles on 2007-10-18
You should be able to use the installation disk to resize the existing Windows partition, and then install Ubuntu on the newly freed-up space. If this option doesn't show up, you can choose the "manual partition" method.

Before you do this, though, there are a couple of absolutely necessary steps:
1) Make sure that any critical data on the hard drive is backed up. The partition editor that comes with Ubuntu is relatively safe, but repartitioning itself is *always* a little risky. Be safe and back up.
2) To minimize the risk of data loss or corruption, you should defrag the Windows drive *twice* before attempt to edit the partition table. 

Here's a link to a more detailed guide through the process:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

