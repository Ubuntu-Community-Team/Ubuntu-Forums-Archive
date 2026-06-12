---
title: "Crash resizing Ubuntu partition with GParted; advice?"
date: 2019-10-02
forum: General Help
---

### Post by orthoducks on 2019-10-02
I've done a lot of partition wrangling in Windows, but this is my first  time working with GParted and it's not treating me nicely.

I'm trying to shrink the partitions on a 250 GB disk which originally looked like this (numbers are approximate):

[TABLE="width: 500"]
[TR]
[TD]sda1[/TD]
[TD]Windows 10[/TD]
[TD]115 GB[/TD]
[/TR]
[TR]
[TD]sda2[/TD]
[TD]Data[/TD]
[TD]20 GB[/TD]
[/TR]
[TR]
[TD]sda3[/TD]
[TD]Extended[/TD]
[TD]115 GB[/TD]
[/TR]
[TR]
[TD][INDENT]sda5
[/INDENT]
[/TD]
[TD]Ubuntu 18.04[/TD]
[TD]115 GB[/TD]
[/TR]
[/TABLE]

I want this:

[TABLE="width: 500"]
[TR]
[TD]sda1[/TD]
[TD]Windows 10[/TD]
[TD]56 GB[/TD]
[/TR]
[TR]
[TD]sda2[/TD]
[TD]Data[/TD]
[TD]12 GB[/TD]
[/TR]
[TR]
[TD]sda3[/TD]
[TD]Extended[/TD]
[TD]56 GB[/TD]
[/TR]
[TR]
[TD]sda5[/TD]
[TD][INDENT]Ubuntu 18.04[/INDENT]
[/TD]
[TD]56 GB[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]unallocated
[/TD]
[TD]126 GB[/TD]
[/TR]
[/TABLE]

Per recommendations I've read, I applied one operation at a time. I  moved/resized the Windows and Data partitions, and moved the extended  partition. The disk then looked like this:

[TABLE="width: 500"]
[TR]
[TD]sda1[/TD]
[TD]Windows 10[/TD]
[TD]56 GB[/TD]
[/TR]
[TR]
[TD]sda2[/TD]
[TD]Data[/TD]
[TD]12 GB[/TD]
[/TR]
[TR]
[TD]sda3[/TD]
[TD]Extended[/TD]
[TD]111 GB[/TD]
[/TR]
[TR]
[TD]sda5[/TD]
[TD][INDENT]Ubuntu 18.04
[/INDENT]
[/TD]
[TD]111 GB[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]unallocated
[/TD]
[TD]71 GB
[/TD]
[/TR]
[/TABLE]

The next step was to resize the Ubuntu partition. GParted reported  copying 9.28 of 10.19 GiB of data; at that point it apparently crashed  Ubuntu. The disk kept flailing away and the disk select light was on  solid, but the numbers ceased to change. The keyboard and mouse were  unresponsive.

I tried to reboot Ubuntu but got a blank purple screen.

I'm now restoring my backup to a fresh disk. Then I'll delete the  original disk's damaged Ubuntu partition and extended partition,  recreate the original extended partition, and copy the Ubuntu partition  to its original location from the new disk. That *should *restore the status quo ante, but I'll still need to move and shrink the extended partition and the Ubuntu partition.

What went wrong, and how can I prevent it from happening again?

(Final note: I'm aware that when I move the Ubuntu partition I may have  to repair the boot parameters. I understand how to do that and it's not  going to be an issue... I hope.)

---

### Post by HermanAB on 2019-10-03
Err... you are trying to change the disk of a running system?  That will only end in tears.

To change the main disk on a machine, you need to boot off something else, such as an install CD/USB dongle.  The disk that you want to change, should not be in use - it should be unmounted.

---

### Post by ajgreeny on 2019-10-03
And shrinking the Windows 10 partition is something that I suggest should be done using Window's own disk management utility; I've no idea how that's done in Win 10 as my last Windows use was XP, but it can be problematical to use Gparted, and it's much safer to use Windows itself.

---

### Post by orthoducks on 2019-10-03
Today I restored the disk, shrank the Windows partition, deleted and  recreated the shared data partition, and shrank the Ubuntu partition. I  still need to move the Ubuntu partition, but I can't do it until I  figure out what made it crash the first time.

Herman: No. I did all of that in live Ubuntu. I reread my message and realized that I never said that. My bad.

AJ: You're correct that changing a Win10 partition in Win10 seems safer, but GParted had no problem with that -- only with changing the *Ubuntu* partition. Today I used Win10 Disk Management to change the NTFS partitions (Windows and shared data). It worked just as well as Ubuntu, that is, perfectly. Windows seems to have no idea how to move a partition, though, which is why I had to recreate the data partition -- not a problem since it was empty, but irritating. I recall that Win7 had no such limitation.

---

### Post by oldfred on 2019-10-05
Better to post actual partitions. You can just copy & paste from Ubuntu or Ubuntu live installer to forum. Please use code tags (# icon in Forum's advanced editor).
sudo parted -l
or 
sudo fdisk -lu

Do not understand why you need to copy Ubuntu partition, it should just be a move left & expand right. And extended partition has to be first expanded to include all unallocated.

My other recommendation is just a new install.
I have now been able to do a new install in about 10 minutes. Reinstalling apps from exported list, running my config script to set most of my settings and within one hour I have a total new install. 
If just restoring a system, I can copy /home from backup & have all my settings. Then only reinstalling apps is longer than install. All my data is in a separate data partition used by several Ubuntu installs.

---

