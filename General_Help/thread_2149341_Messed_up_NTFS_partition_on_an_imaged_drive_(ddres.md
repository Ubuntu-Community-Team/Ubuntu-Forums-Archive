---
title: "Messed up NTFS partition on an imaged drive (ddrescue)"
date: 2013-05-28
forum: General Help
---

### Post by trendle on 2013-05-28
The history..
I found some corrput files on my 2TB external drive and ran ddrescue, created an image, and wrote that image onto another 2TB drive hoping to keep the data.
Although the original drive was formatted NTFS most of its use was backing up my Linux data.  
But the new drive would not mount under Linux.
It mounted under WinXP (until I tried to repair the partition :confused: ).  
I found that the original drive had
255 heads, 63 sectors/track, 243201 cylinders
but the new drive had
255 heads, 63 sectors/track, 243200 cylinders
So the image ran off the end of the drive,  seems like that's OK with windows,  but not with Linux, which is why I tried to repair it with the instructions from Gparted, here : [http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk]("http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk")

So now I have a drive that is not readable by Linux nor WinXP.
Here's what testdisk has to say ...
```
TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdl - 2000 GB / 1863 GiB - CHS 243201 255 63
     Partition               Start        End    Size in sectors
>P HPFS - NTFS              0   1  1 243200 204 59 3907020848
 * HPFS - NTFS              0   1  1 243200 254 63 3907024002 [Iomega HDD]








[COLOR="#FF0000"]Structure: Bad[/COLOR]. Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type,
     Enter: to continue
2000 GB / 1863 GiB

```

This is the result of running testdisk and asking for BACKUP (not written).


I'd greatly appreciate any ideas on fixing this.    (Before anyone says it.. the original drive is not available anymore).

---

### Post by dino99 on 2013-05-28
as it is an ntfs, you should run chkdsk and the other hdd tests from windows, to try fixing it. Cleaning it (with ccleaner for example) then defraging it should also help.

---

### Post by Mark Phelps on 2013-05-28
As an alternative, if you know someone with a Windows PC, have them download and burn the Minitool Partition Wizard Boot CD.

Then, boot from that and use the Check option against the partition in question.  That will run CHKDSK for you.

---

