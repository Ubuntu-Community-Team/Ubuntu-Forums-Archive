---
title: "Disk Utility 3.0.2 doesn't have option to create FAT32 Volume?"
date: 2015-06-21
forum: General Help
---

### Post by victor36 on 2015-06-21
I've got a 64GB USB stick that I want to format as a FAT32 bootup disk with Hiren's BootCD.I go to Format Drive and select Master Boot Record.After the format is complete I do Create Partition but FAT32 isn't an option on the list.

---

### Post by yetimon_64 on 2015-06-21
Are you looking at the format option in the top right of the disk utility main window? If so look further down (below the partition layout table) for the "double cog icon". With the partition you want to format selected, click on that cog and select format. You will then get the option to choose "Compatible with all systems and devices (FAT)".

That section should format the partition to FAT32. See the attached screenshot, the cog icon to click is just above the orange "close window" button. I am showing the option for FAT32 highlighted in the "Type" pop up window there in the screenshot.  Yeti.

---

### Post by mc4man on 2015-06-21
Disk Utility 3.0.2 looks different than the screen above but the advice given is the same & correct, just choose FAT. The default for FAT is  FAT32

---

### Post by Vladlenin5000 on 2015-06-21
Here's the thing: _You CAN'T format a 64GB drive with FAT32 because its limit is up to 32GB only_. 

For 64GB you need to use different file systems: EXT4, NTFS or the new not-so-compatible [extFAT]("https://en.wikipedia.org/wiki/ExFAT")

---

### Post by coffeecat on 2015-06-21
> **Vladlenin5000 said:**
> Here's the thing: _You CAN'T format a 64GB drive with FAT32 because its limit is up to 32GB only_. 

That's only true for Windows - it's a limitation built into the operaing system's utility. Ironically, Windows will happily mount and read-write a drive >32GB and formatted FAT32, and you can format a drive/partition >32GB in Windows with 3rd party software. There's no problem with a Linux-based formatting utility. You can format a 500GB drive or partition with Disks or Gparted if you so wish. Whether or not that is a good idea is, of course, another matter.

---

### Post by victor36 on 2015-06-22
I see. Thanks.

They really should be more specific. FAT16? FAT32?

---

