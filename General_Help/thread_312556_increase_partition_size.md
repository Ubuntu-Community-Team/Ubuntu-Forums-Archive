---
title: "increase partition size"
date: 2006-12-04
forum: General Help
---

### Post by Jack of Fables on 2006-12-04
is it possible to increase the size of a partition, or would i have to erase the partition and start all over again?

---

### Post by yabbadabbadont on 2006-12-04
It depends on the type of the partition, the type of the filesystem used, and what physically comes after the partition on the disk.

---

### Post by taurus on 2006-12-04
You can use gparted from the LiveCD to resize your harddrive.  No need to reinstall if you don't have to.  As always, _back up_ your important files first before you do any resizing!!!

---

### Post by Jack of Fables on 2006-12-04
i need more space on one partition and less on another, is it possible or not.

---

### Post by yabbadabbadont on 2006-12-04
What does "sudo fdisk -l" print out?

---

### Post by Jack of Fables on 2006-12-06
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4328    34764628+  83  Linux
/dev/sda2   *        4329       10855    52428127+   7  HPFS/NTFS
/dev/sda3           10856       11976     9004432+  83  Linux
/dev/sda4           11977       12161     1486012+   5  Extended
/dev/sda5           11977       12161     1485981   82  Linux swap / Solaris


so is it possible to resize the sda2 to make it bigger if i'm shrinking sda1?

---

### Post by yabbadabbadont on 2006-12-06
It might be possible with something like PartitionMagic, but most of the free utilities won't let you grow a partition "down" towards the beginning of the disk.  You may be able to move sda2 down (without resizing it) after shrinking sda1 and then be able to expand it, but it would depend on the tool you use.  I don't know which tools support what currently, sorry.

---

### Post by Get_Ya_Wicked_On on 2006-12-06
This is exactly what I'm trying to do.

```

   Device Boot      Start         End      Blocks   Id  System

/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        4871    39070080    7  HPFS/NTFS
/dev/sda3            4872        7303    19535040   83  Linux
/dev/sda4            7304        9726    19462747+   5  Extended
/dev/sda5            7429        9726    18458685    b  W95 FAT32
/dev/sda6            7304        7427      995967   82  Linux swap / Solaris

```

That is my output. I just want to give more space to Ubuntu.

But as I've been reading, it seems the only way is to do all this copying mess.

---

### Post by Jack of Fables on 2006-12-06
if i shrink the size of sda1, it puts space between it and sda2. but it won't let me enlarge sda2. so i need partitionmagic or something? from a live cd?
is it possible to change the filesystem of a partition without losing anything?

---

### Post by drphilngood on 2006-12-06
The graph located here:

[GParted Features]("http://gparted.sourceforge.net/features.php")

shows exactly what features are available on each file system in GParted.

---

### Post by Jack of Fables on 2006-12-06
i know, thats y i asked if i could change the file system of a partition somehow without losing anything

---

### Post by drphilngood on 2006-12-06
> **Jack of Fables said:**
> i know, thats y i asked if i could change the file system of a partition somehow without losing anything

No, you asked about shrinking one partition to enlarge another with the freed space.

> **Jack of Fables said:**
> is it possible to increase the size of a partition, or would i have to erase the partition and start all over again?[QUOTE=Jack of Fables;1853864]i need more space on one partition and less on another, is it possible or not.[/QUOTE]

If you ¨change the file system of a partition¨ then you lose everything on it, that you haven´t backed up, when formatting to the new file system.  However, according to what file system you have, you might be able to shrink one partition and then enlarge another with the freed space.

---

### Post by Jack of Fables on 2006-12-07
thats was a while ago, i need to move a ext3 partition and a ntfs partition and my problems will be gone, sorda.

---

### Post by drphilngood on 2006-12-07
> **Jack of Fables said:**
> thats was a while ago, i need to move a ext3 partition and a ntfs partition and my problems will be gone, sorda.

Does it have anything to do with this thread you posted?

> **Jack of Fables said:**
> please someone help, im stuck using my live cd because i reinstalled gnome and now i can't get through it. i have 3 partitions that have os's installed on them, i was stuck on windows. someone said to reinstall gnome to switch between them at boot, but i can't get through gnome!

[switch between partitions]("http://www.ubuntuforums.org/showthread.php?t=311662")

Just want to know where we´re at...

---

### Post by Jack of Fables on 2006-12-07
no, one is switching between partitions, and the other is just about me asking for help enlaring a partition and shrinking another. i started both threads at different times and are about different problems. on this one i need a app that  can move ntfs and ext3 partitions.

---

### Post by drphilngood on 2006-12-07
> **Jack of Fables said:**
> no, one is switching between partitions, and the other is just about me asking for help enlaring a partition and shrinking another. i started both threads at different times and are about different problems. on this one i need a app that  can move ntfs and ext3 partitions.

According to GParted´s feature list that I posted earlier:

[GParted Features]("http://gparted.sourceforge.net/features.php")

You can use GParted to shrink your NTFS partition and then grow your ext3 partition with the freed space.  However, I caution you to hold off until you finish with bulldog in your other thread and backup your data before attempting this.

Good luck!

---

### Post by Jack of Fables on 2006-12-07
you've got it mixed up. i need to do it the otherway around. but i can't do what i want to do if i can't move ntfs AND ext3 partitions. thats why i said that i need to find an app that will move them that i can use on a live cd.

---

### Post by yabbadabbadont on 2006-12-07
The only truly safe solution for you would be to do a full backup of all your data (both windows and linux), then repartition the way you want, and finally restore your data from backup.

---

### Post by Jack of Fables on 2006-12-07
i just want to move the locations of the partitions on my disc, any apps come to mind?

---

### Post by Get_Ya_Wicked_On on 2006-12-07
> **yabbadabbadont said:**
> The only truly safe solution for you would be to do a full backup of all your data (both windows and linux), then repartition the way you want, and finally restore your data from backup.

What would be the most efficient way for me to make a backup of my current linux partion, that I would later be able to "toss", in effect, on to my newly created partion.

And would I have to go through the default Ubuntu installation & initiate my backup or could I make my backup the "installation". As you can tell, I'm not well-versed in the partitioning area.

---

### Post by drphilngood on 2006-12-07
> **Jack of Fables said:**
> i just want to move the locations of the partitions on my disc, any apps come to mind?

I have only used GParted with the Alternate Installer CD and it does allow you to copy from one partition to another but I don´t know if it would work across file systems of different types.  However, you could backup all your data to a Fat32 partition, do whatever partitioning is necessary and then import the data from within Windows or Linux or just use Fat32 for all of your cross-platform needs.

---

### Post by yabbadabbadont on 2006-12-07
> **Get_Ya_Wicked_On said:**
> What would be the most efficient way for me to make a backup of my current linux partion, that I would later be able to "toss", in effect, on to my newly created partion.

And would I have to go through the default Ubuntu installation & initiate my backup or could I make my backup the "installation". As you can tell, I'm not well-versed in the partitioning area.

I sent you a PM as I didn't want to hijack the thread.

---

### Post by Jack of Fables on 2006-12-07
i can copy a partition without losing anything and make it a different format than the original?

---

### Post by Jack of Fables on 2006-12-07
but if i format the the parition, wouldn't it erase everything, if i can format it without losing everything, there would be no problem.

---

