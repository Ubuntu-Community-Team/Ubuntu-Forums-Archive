---
title: "Mount Windows Partitions and &quot;UUID&quot;?"
date: 2007-12-08
forum: General Help
---

### Post by sandorf on 2007-12-08
Hi, I've just installed Gusty Gibbon, which correctly detected my Windows partitions and mounted them. Problem is when I was installing Ubuntu I still had an unformatted partition in Windows. Now  that I've formatted the partition and want to manually mount this partition, but all the guides I can find don't mention the "UUID" part in /etc/fstab. I also want the manually mounted partition to appear in  'Place' menu as well as the desktop. Will simply modifying fstab and 'mount -a' do this?

Thanks!

---

### Post by rsambuca on 2007-12-08
Yes.  First create a folder in /media.  Then it will appear in your desktop and places menu.  ie.  sudo mkdir /media/newpartitionname.

Then use the command 'blkid' to get your uuid number for the new partition, and then edit your fstab.

---

### Post by sandorf on 2007-12-10
thanks, but blkid only displays the UUIDs of the partitions that have already been mounted. Still looking for a solution...

---

### Post by sandorf on 2007-12-10
This Windows partition of mine is formatted AFTER ubuntu is installed. I wonder if there's anyway to make ubuntu redo the Windows partition detection & mounting process when it was installed.

---

### Post by rsambuca on 2007-12-10
That is strange.  blkid gives me all of the partitions, even unmounted ones.  Try this instead:

ls /dev/disk/by-uuid/ -alh

---

### Post by rsambuca on 2007-12-10
Also, can you post the output of 

sudo fdisk -l

---

### Post by sandorf on 2007-12-10
Yeah, I find the UUID under the by-UUID folder, and mounted the partition successfully.
Strangely 'blkid' still doesn't display the UUID even after the disk is mounted


fang@fang-desktop:~$ blkid
/dev/sda1: UUID="E81A-7D09" TYPE="vfat" 
/dev/sda6: UUID="e454adec-e03e-47b1-972e-d5b38fb3655e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="013a5917-6f66-443e-a126-47bf2e73f774" TYPE="swap" 
/dev/sda8: UUID="80eeb95f-9a0a-428f-9de6-bea8f488252b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="747C03037C02C03A" LABEL="F.L.C." TYPE="ntfs" 

fang@fang-desktop:~$ ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root 160 2007-12-11 10:56 .
drwxr-xr-x 6 root root 120 2007-12-11 10:56 ..
lrwxrwxrwx 1 root root  10 2007-12-11 18:56 013a5917-6f66-443e-a126-47bf2e73f774 -> ../../sda7
lrwxrwxrwx 1 root root  10 2007-12-11 10:56 747C03037C02C03A -> ../../sdb1
lrwxrwxrwx 1 root root  10 2007-12-11 18:56 80eeb95f-9a0a-428f-9de6-bea8f488252b -> ../../sda8
lrwxrwxrwx 1 root root  10 2007-12-11 18:56 A46D-5CD9 -> ../../sda5
lrwxrwxrwx 1 root root  10 2007-12-11 18:56 e454adec-e03e-47b1-972e-d5b38fb3655e -> ../../sda6
lrwxrwxrwx 1 root root  10 2007-12-11 18:56 E81A-7D09 -> ../../sda1

fang@fang-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a2c1a2b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551        9729    57665317+   f  W95 Ext'd (LBA)
/dev/sda5            2551        5100    20482843+   b  W95 FAT32
/dev/sda6            5101        7176    16675438+  83  Linux
/dev/sda7            7177        7297      971901   82  Linux swap / Solaris
/dev/sda8            7298        9729    19535008+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f1ff68b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS

---

### Post by rsambuca on 2007-12-10
So you have it fixed then?  And FAT32!?

---

### Post by sandorf on 2007-12-11
yes, i fixed it. fat32? why not?

---

### Post by rsambuca on 2007-12-11
FAT32 is really an antiquated filesystem that is no longer required.  It requires high maintenance, has no journalling, file size limitations...  NTFS or Ext3 would have been a much better choice.

---

### Post by vanadium on 2007-12-11
I do not agree with this. When you use ntfs, you are dependent on Windows. Yes, Linux can read and write ntfs partitions, but Linux cannot repair them. FAT32 is a much simpler file system, and does not require higher maintenance, quite contrary. Because of its simplicity, the performance is high. Compatibility is 100% (Win, Mac, Linux). The limits in file size is the most important limitation: you cannot store 4 GB+ files. I would only advice ntfs if you need interoperability with Windows for exchanging 4 GB+ files, and if you have easy access to a Windows system.

---

### Post by rsambuca on 2007-12-11
> **vanadium said:**
> I do not agree with this. When you use ntfs, you are dependent on Windows. Yes, Linux can read and write ntfs partitions, but Linux cannot repair them. FAT32 is a much simpler file system, and does not require higher maintenance, quite contrary. Because of its simplicity, the performance is high. Compatibility is 100% (Win, Mac, Linux). The limits in file size is the most important limitation: you cannot store 4 GB+ files. I would only advice ntfs if you need interoperability with Windows for exchanging 4 GB+ files, and if you have easy access to a Windows system.

Yeah, I guess we definitely disagree on this one!  The 4GB limit is not really a big deal to most people these days.

As far as dependence on Windows, well the OP has Windows, so there is no problem here.  As far as repairing NTFS, well, as I said the OP has Windows.

FAT32 actually DOES require higher maintenance as the fragmentation that occurs from regular use is much worse than other filesystems, both ntfs and ext3.  The fault tolerance of FAT32 filesystems is much lower than ntfs, resulting in a greater number of errors and complete failures, and when problems do arise, the crash recovery abilities of FAT32 are much less than any of the other systems.

---

### Post by vanadium on 2007-12-11
I surely agree with you for this case, where the user has also Windows. However, putting a general stating that FAT32 is really an antiquated filesystem that is no longer required is a bridge too far. It is a lousy file system but it is the only one that can be read on almost any system.

---

### Post by maybeway36 on 2007-12-11
ext driver for windows? :)

---

### Post by vanadium on 2007-12-11
This leaves ext3 as the better choice over ntfs, but still you can walk to an apple machine ...

---

### Post by rsambuca on 2007-12-11
> **vanadium said:**
> I surely agree with you for this case, where the user has also Windows. However, putting a general stating that FAT32 is really an antiquated filesystem that is no longer required is a bridge too far. It is a lousy file system but it is the only one that can be read on almost any system.

Yes, I should have been more specific.

---

### Post by rsambuca on 2007-12-11
> **maybeway36 said:**
> ext driver for windows? :)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by strabes on 2007-12-11
By the way, you don't **need** to use uuids in fstab. You could just use its /dev location.

---

### Post by vanadium on 2007-12-13
Easiest, but not anymore done in recent Ubuntu distributions because of possible problems. UUID= offers a more persistent reference to the disk, but also the disk label (LABEL=) can be used. However, you have to be careful that the labels are unique. The chance that UUDS, which are "autogenerated", are unique is practically zero. Not so for labels.

---

### Post by rsambuca on 2007-12-13
Going back to the /dev/hda type designations is a lot more handy for us distro-hoppers.  I like to test new distros, and have 5 logical partitions for this.  Removing the UUID's has the benefit of not having to edit the other fstabs everytime I install a new distro.

---

