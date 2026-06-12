---
title: "Partition resizing"
date: 2014-09-20
forum: General Help
---

### Post by Blix775 on 2014-09-20
HI! I just setup my laptop for a dual-booth with Lubuntu 14.04 and Windows and I need to make the windows partition bigger since it's got just 2 Gigs left. I was wondering if there's any way I can re-size it with 
gparted and if there's anything I should be aware. I noticed that -for whatever the reasons- the new gparted did not let me create logical partitions so all of these partitions are primary. I've ot a 34GB one for Windows, a 400GB for storage and around 24GB for linux. That's how it's setup going off the top of my head.

---

### Post by yancek on 2014-09-20
You will need to post more information for anyone to be able to do more than guess.  Are you using MBR or EFI boot?  Post the output of the command:  sudo fdisk -l(Lower Case Letter L in the command) or post an image showing drives/partitions from GParted or post the output of parted -l(Again Lower Case L) so we have something to work with.

---

### Post by Mark Phelps on 2014-09-20
>  I need to make the windows partition bigger since it's got just 2 Gigs   left. I was wondering if there's any way I can re-size it with gparted and if there's anything I should be aware. 

If the Windows version is Vista or newer, do NOT, repeat NOT, use gparted to resize it.  Recent Windows have their own Disk Management utility and you should use that.

---

### Post by Blix775 on 2014-09-21
> **yancek said:**
> You will need to post more information for anyone to be able to do more than guess.  Are you using MBR or EFI boot?  Post the output of the command:  sudo fdisk -l(Lower Case Letter L in the command) or post an image showing drives/partitions from GParted or post the output of parted -l(Again Lower Case L) so we have something to work with.
I'm using MBR and the output from  sudo fdis -l is this:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0007a699


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    62916607    31457280    7  HPFS/NTFS/exFAT
/dev/sda2        62916608   913858559   425470976    7  HPFS/NTFS/exFAT
/dev/sda3       913858560   922247167     4194304   82  Linux swap / Solaris
/dev/sda4       922247168   976773119    27262976   83  Linux


 
```
parted -l is not outputting anything. 

And mark, how do I use window's partition manager? I'm running Windows 7 on this machine.

---

