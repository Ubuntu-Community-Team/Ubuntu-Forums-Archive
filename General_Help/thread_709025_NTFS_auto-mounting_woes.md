---
title: "NTFS auto-mounting woes"
date: 2008-02-27
forum: General Help
---

### Post by GfµnK on 2008-02-27
I have been searching all night, but I haven't come across the answer to this problem.

I recently installed Gutsy on my desktop machine, which has two sata hard drives, a 400 gig and 500 gig one.  On the 400 gig, I have a 200 gig "XP Gaming" partition that contained a Performance XP install that was streamlined just for gaming.  I then have the remaining space partitioned for ubuntu.  This is the booting drive.  On the 500 gig drive, I have a 300 gig media partition, 100 gig partition where I kept games for my old XP install, then the remaining is my old XP installed, called "XP Workstation".  I had the XP bootloader set up to let me chose between either of these XP installs, and it worked quite nicely.

My problem is that, when booting into ubuntu, I can SEE all of these partitions (all in NTFS, if memory serves me correctly) in the places / computer folder, but they are grayed out until I click on each one, and the first one requires me to input my password.  Until I click on any of these, none of my programs can access any of the files on them.  This causes a big pain when I'm wanting to listen to music or load my virtualized XP, which has network drives that link to all of these partitions.

sudo fdisk -l gives me:

```

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb5bcb5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       26107   209704446    7  HPFS/NTFS
/dev/sda2   *       26108       47884   174923752+  83  Linux
/dev/sda3           47885       48641     6080602+   5  Extended
/dev/sda5           47885       48641     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44d60981

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7649    61440561    7  HPFS/NTFS
/dev/sdb2            7650       20397   102398310    7  HPFS/NTFS
/dev/sdb3           20398       60801   324545130    7  HPFS/NTFS

Disk /dev/sde: 2059 MB, 2059403264 bytes
64 heads, 62 sectors/track, 1013 cylinders
Units = cylinders of 3968 * 512 = 2031616 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   ?      196103      483782   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(196102, 51, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(483781, 40, 51)
Partition 1 does not end on cylinder boundary.
/dev/sde2   ?       42513      530423   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(42512, 30, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(530422, 52, 42)
Partition 2 does not end on cylinder boundary.
/dev/sde3   ?      471241      959151   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(471240, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(959150, 39, 39)
Partition 3 does not end on cylinder boundary.
/dev/sde4   ?           1      916640  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(916639, 47, 30)
Partition 4 does not end on cylinder boundary

```

and within fstab is:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c5713c76-b56f-4516-a724-007a7965da41 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1311359e-999b-4aa0-bb63-4877c4358d02 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

Thank you for any help, and I'm sorry if this has been posted before and I just suck at searching.

---

### Post by grittyminder on 2008-02-27
You need to edit your fstab file to auto-mount those drives.

Something like:

/dev/<ntfsPartition> /mnt/<mountPoint>     ntfs-3g     defaults 0 0

---

### Post by housam on 2008-02-27
look at [[COLOR="Red"]_this thread _[/COLOR]]("http://ubuntuforums.org/showthread.php?t=608348&highlight=mounting+ext3+partitions")it has the solution

---

### Post by GfµnK on 2008-02-27
> **housam said:**
> look at [[COLOR="Red"]_this thread _[/COLOR]]("http://ubuntuforums.org/showthread.php?t=608348&highlight=mounting+ext3+partitions")it has the solution

Thank you so much!  Everything is working flawlessly.  I'm just happy to be able to now run Ubuntu on my main machine for everything except gaming (I still plan to boot into the gaming XP partition when I want to do that).

---

### Post by housam on 2008-02-27
> **GfµnK said:**
> Thank you so much!  Everything is working flawlessly.  I'm just happy to be able to now run Ubuntu on my main machine for everything except gaming (I still plan to boot into the gaming XP partition when I want to do that).

Welcome to ubuntu and have fun.

---

