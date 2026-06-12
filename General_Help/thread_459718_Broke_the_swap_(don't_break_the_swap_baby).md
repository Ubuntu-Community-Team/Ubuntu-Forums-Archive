---
title: "Broke the swap (don't break the swap baby)"
date: 2007-05-31
forum: General Help
---

### Post by adampyre on 2007-05-31
Sorry for the stupid title, but you are reading this now. I think I broke the swap. If I check the system monitor, it says used swap, 0bytes/0bytes. Initially when my system was working fine, I had 2 partitions, first partition was Ubuntu, second was swap. I then needed to reinstall windows. So, I used Gparted live CD. I took some space from Ubuntu so it read:

ubuntu partition/unused space/swap

then I rearranged it:

ubuntu partition/swap/unused space

then i formatted

ubuntu partition/swap/ntfs partition

So, I installed XP and of course it destroyed grub. I reinstalled grub (windows doesn't show up on the list) and upon rebooting ubuntu it did a disk error check, found errors, supposedly fixed them and rebooted. I started Ubuntu and it seems to work fine (took a little longer to boot than usual) but I noticed looking at my settings it doesn't see the swap any more. Any suggestions on how to fix this?

Thanks.

UPDATE if needed:

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1986    15952513+  83  Linux
/dev/hda2            1987        2050      514080   82  Linux swap / Solaris
/dev/hda3   *        2051        2432     3068415    7  HPFS/NTFS

Disk /dev/sda: 519 MB, 519569408 bytes
255 heads, 63 sectors/track, 63 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          64      507360+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(62, 254, 63) logical=(63, 42, 43)

also, reading around i decided to do sudo mount -a in a command line and it says line 4 of my fstab is bad?

fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0         # /dev/sda1
UUID=340221c5-e9d7-4af4-9d51-4c892b351ae4 /               ext3    defaults,errors=remount-ro,noatime,auto,rw,de$
# /dev/sda2
UUID=ea60be46-98ad-4aad-984d-97e9afe91035 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by merlinus on 2007-05-31
With all of your changes, the UUIDs may now be different.

sudo fdisk -l 

will give you the partitions.

blkid

will give the UUIDs.

Compare them with entries in /etc/fstab

Also, with the kernel upgrade some of the partitions may have changed from sd's to hd's.

hth...

-merlin

---

### Post by adampyre on 2007-05-31
Thanks Merlin, that was the issue. I copied the UUID for the swap from blkid into my fstab and i it fixed it. Also, my partitions in fstab were listed as "sda"'s and i changed them to "hda"'s. should i change it back?

> **merlinus said:**
> With all of your changes, the UUIDs may now be different.

sudo fdisk -l 

will give you the partitions.

blkid

will give the UUIDs.

Compare them with entries in /etc/fstab

Also, with the kernel upgrade some of the partitions may have changed from sd's to hd's.

hth...

-merlin

---

### Post by merlinus on 2007-05-31
Glad it worked.    :D

Since your partitions are loading from their UUIDs, I do not think the other issue matters.

sudo fdisk -l

should give you the way ubuntu is recognizing your partitions.  If it says /dev/hda1, for example, then it might do to change that in fstab, and it seems like you did this already.

But those lines beginning with a hash mark (#) are commented out, so it does not matter.

-merlin

---

