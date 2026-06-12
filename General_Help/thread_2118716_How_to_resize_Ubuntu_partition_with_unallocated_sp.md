---
title: "How to resize Ubuntu partition with unallocated space w/GParted &amp; LiveCD"
date: 2013-02-22
forum: General Help
---

### Post by fzara2000 on 2013-02-22
I currently have one hard drive with 3 partitions and 2  partitions of unallocated space.  I am dual booting Windows 7 (1  partition) and another partition for Ubuntu 12.04. 
  I'm using Gparted and Ubuntu 12.04 Live CD with all drives unmounted, this is what i'm seeing:


  /dev/sda1. NTFS.  325gb, 292gb used. Boot flag. = WINDOWS 7 

/dev/sda2. EXTENDED. 92.95gb.  lba flag. 

       /dev/sda5.  EXT4.  89gb.  = UBUNTU 

       unallocated. 3.82gb


 unallocated. 39.75gb = ??? 

/dev/sda4. NTFS.  Respawn Recovery. 7.79gb. 4.27gb used. 

unallocated. 3.02mb.
  

I CAN resize sda4 to include the 40gb of unallocated space but  obviously I dont see the point in doing that to a recovery partition. 



I CAN resize sda5 to include the unallocated space of 3.82gb but would  this help?
  

Help?

---

### Post by dino99 on 2013-02-22
on that screenshot, sda5 seems having an issue (red warning on the line), so you need to know why.

here is how ubuntu should be installed:
[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

on unmounted partition (boot from a livecd/liveusb), gparted can resize/move it as you like, simply let the windows partition starting at the very beginning of the hdd.

---

### Post by fzara2000 on 2013-02-22
> **dino99 said:**
> on that screenshot, sda5 seems having an issue (red warning on the line), so you need to know why.

here is how ubuntu should be installed:
[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

on unmounted partition (boot from a livecd/liveusb), gparted can resize/move it as you like, simply let the windows partition starting at the very beginning of the hdd.

Thanks for the quick response.  The error relates to not having the correct package to support ext4 file support, E2FSProgs v1.41+.   How do I go about fixing the error?

---

### Post by fzara2000 on 2013-02-22
This is the error message:

---

### Post by dino99 on 2013-02-22
set the "boot" flag on it with gparted

---

### Post by plucky on 2013-02-22
> How to resize Ubuntu partition with unallocated space w/GParted & LiveCD

Select /dev/sda2 and resize it to include all of the un-allocated space.

Then,as all of the un-allocated space will be behind the /dev/sda5 partition,you can now select it and resize it to include the un-allocated space. 

Good Luck

---

### Post by fzara2000 on 2013-02-23
> **plucky said:**
> Select /dev/sda2 and resize it to include all of the un-allocated space.

Then,as all of the un-allocated space will be behind the /dev/sda5 partition,you can now select it and resize it to include the un-allocated space. 

Good Luck

Thanks to both of you above. 

Unfortunately, I seem to get another type of gParted error. I tried Googling but couldn't find an answer. 
'unable to satisfy all constraints on partition..'

I tried creating a small amount of unallocated space at the beginning of sda5 but im still getting the same error..?

---

### Post by Mark Phelps on 2013-02-23
You are booting from a USB or CD while you're trying to do this, right? Because, you can't work on partitions that are in use.

Have you run fsck on that partition? The screenshot is alarming because GParted doesn't show used and free space inside the partition.  I would run fsck on it to see if there are any filesystem errors.

---

### Post by oldfred on 2013-02-23
You have to resize the extended partition sda2 to include the unallocated before you can add it to sda5 as plucky posted above. Screen shot does not show you have yet moved extended partition to include unallocated yet. Run that command before making any other changes with gparted.

---

