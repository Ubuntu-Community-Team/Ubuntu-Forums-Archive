---
title: "How to delete Ubuntu's partition and make it part of XP's partition again"
date: 2007-12-29
forum: General Help
---

### Post by BlastOButter42 on 2007-12-29
I need to reinstall Windows XP, and I want to first get rid of the ext3 partition that Ubuntu is on and make it part of Windows's NTFS partition, the way it was before I installed Ubuntu. How would I do this?

Right now my hard drive has four partitions: the largest at 29 GB and using NTFS is my Windows XP partition; Ubuntu's is 4.65 GB in ext3; the others are a 3.76 GB FAT32 partition for Dell PC Recovery and a 47 MB FAT partition called "DellUtility".

---

### Post by Lostincyberspace on 2007-12-29
Download the partedmagic iso from here 
[http://www.partedmagic.com/](http://www.partedmagic.com/)
and delete the ubuntu partition and grow the xp one.

---

### Post by rune0077 on 2007-12-29
Boot up in Windows XP and use Partition Magic to format the Ubuntu partition. This will delete Ubuntu. Then, still with Partition Magic, right click the entry for the XP partition and choose something called "Increase size of partition" or something along those lines, which will let you increase the partition by adding unused drive space to it.

---

### Post by dim_hyder on 2007-12-29
Download the gparted live CD iso from [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Burn the iso to a CD.

Boot the PC from the CD.

Delete the Ubuntu partition.

Enlarge the XP partition.

This might take some time depending on disk sizes.

P.S It's always recommended to backup your data before any repartition /resizing.

Cheers,

Dim Hyder

---

### Post by eggdeng on 2007-12-29
redundant

---

### Post by BlastOButter42 on 2007-12-29
As Lostincyberspace suggested, I used Partition Magic to delete the Ubuntu partition and expand the Windows XP partition. Problem is, now when I turn on the computer, Windows doesn't boot; GRUB still comes up and says it's loading, but then just says "Error 22". How do I get Windows to boot?

---

### Post by dim_hyder on 2007-12-30
Boot from a windows XP CD and when prompted press R to enter the recovery console.

Once at the command line of the recovery console type

fixmbr

this should restore the windows boot loader.

Cheers,

Dim Hyder

---

### Post by clapper65 on 2008-01-16
Thanks to all on this thread.  I was running Ubuntu dual booted with XP.  I loaded Ubuntu stand alone on a different PC and was able to get my Windows machine back to the same before I dual booted.  The gparted from the ISO along with fixmbr did the trick!

Thanks again!:guitar:

---

