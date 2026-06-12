---
title: "Partitions and Filesystems Corrupted / Confused"
date: 2007-01-03
forum: General Help
---

### Post by nrwilk on 2007-01-03
I have an HP laptop with dual SATA hard drives.  The first drive has 3 Windows partitions and one fat32 partition for backups and music storage.  The second drive has 2 ext3 partitions and 1 swap partition.  The 3 Windows partitions on the first drive are: 1, the main partition, 2, a recovery partition, 3, a vfat partition with software for playing DVDs without starting the computer up completely.

All of a sudden I got a failed fsck check during the automated check that runs every 7 boots during the startup process.  After checking fstab, all of the partitions are correctly listed.

But, some weird stuff happens when I list my partitions with qtParted or gParted.  These are the wierd things:

/dev/sda2/ - I think this is the Quickplay DVD partition.  It should be very small, but both qtParted and gParted report this partition as 38GB.  Also, it should be vfat, but these programs also report this partition as being ext3.  When browsing the files on it, it is clear that it is a Windows partition.

/dev/sda4/ - This is my backup/music partition.  It should be around 30GB, but it is reported as 1GB.  Also, it is reported as NTFS, and it should be a vfat partition.  When browsing the files on it, it is clearly my backup partition, and it clearly has much more data on it than 1GB.

Also, fdisk -l reports these partitions the same as gParted and qtParted.

Here is that output:
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        8376    36563940   83  Linux
/dev/sda3            8377        9598     9815715    c  W95 FAT32 (LBA)
/dev/sda4            9599        9729     1052257+  d7  Unknown

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2611    20972826   83  Linux
/dev/sdb2            2612        9623    56323890   83  Linux
/dev/sdb3            9624        9729      851445   82  Linux swap / Solaris

```

Here is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb2       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
/dev/sda2       /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       0
/dev/sda3       /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
/dev/sda4       /media/sda4     ext3    defaults        0       2
/dev/sdb3       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Does anyone know, not only how to fix this without borking my Windows partitions, but also why it could have happened?

Thanks very much for any help at all.  I cannot startup the machine without it catching these errors.  Every time I have to exit from a command prompt before X starts up.

If any other information is required, just let me know.

nrwilk

---

### Post by nrwilk on 2007-01-03
I just checked in kcontrol, in the Disk & Filesystems module, and it actually reports the two problem partitions with the correct filesystems, but it still displays the wrong sizes.

I have no idea if this helps at all, but there it is.

nrwilk

---

### Post by taurus on 2007-01-03
I am a little confused from looking at your outputs.  In your partition table, you have /dev/sda2 as ext3 but you mount it as vfat in /etc/fstab!  Then, you mount /dev/sda4 as ext3 but according to "fdisk-l", it's an unknown partition--d7!!!

Not sure exactly what's going on here...

---

### Post by nrwilk on 2007-01-03
> **taurus said:**
> I am a little confused from looking at your outputs.  In your partition table, you have /dev/sda2 as ext3 but you mount it as vfat in /etc/fstab!  Then, you mount /dev/sda4 as ext3 but according to "fdisk-l", it's an unknown partition--d7!!!

Not sure exactly what's going on here...

I'm not sure if you didn't read my whole post, or what.  But, what you have described here is exactly my problem.  /dev/sda2 is **supposed** to be vfat, but it is reported as ext3.  /dev/sda4 is **supposed** to be vfat, but it is reported as NTFS, or "Windows".  In addition, both of their sizes are misrepresented.  Because of these things, the auto-fsck which runs at startup is thrown off.

I've temporarily disabled these partitions by commenting them in fstab, but this is just a dirty workaround.   :???:

Does anyone have any suggestions?

nrwilk

---

### Post by taurus on 2007-01-03
Yes, I read your whole post and that is why I don't understand.  You say they are different filesystems than the kernel reports!!!  Did you somehow use gparted to format them?

---

### Post by nrwilk on 2007-01-04
> **taurus said:**
> Did you somehow use gparted to format them?

No, in fact I installed qtParted and gParted in order to check them out as a last resort.

These are all partitions that I created during the Kubuntu install process.  They have all worked through using dapper, and also using edgy.  This problem occured all-of-a-sudden after these partitions had been used correctly and successfully many times.  I am pretty sure that they should both be fat32 partitions.

Here is a new question:
Assuming that (for some reason that I cannot fathom) these partition's sizes are being miscalculated, what would happen if I just deleted /dev/sda4 and recreated it?  Would I just be messing things up more?  The other three partitions on that drive are ones that I never use.  I keep them there because HP has a sketchy return policy, and I couldn't get them to give me a straight answer as to whether I would still be eligible for service under warranty should I delete Windows.  Rather than risk it, I kept Windows around, along with the recovery and the QuickPlay partitions.  So, I kind of want those partitions to remain intact.

Thank you for your effort, taurus! :D 

nrwilk

---

### Post by nrwilk on 2007-01-04
Well, I must admit that I was wrong.  Neither of the two partitions should have contained fat32 filesystems.  But, the problem did still exist as I has stated it.

Something must have re-written my /etc/fstab because these two partitions, which had previously worked, somehow got their filesystems changed in fstab.

/dev/sda2 should have been ext3, and it was listed as vfat.

/dev/sda4 should have been ntfs, and it was listed as ext3.

So, it turns out that I was confusing the two.  This means that their sizes are correct.  My fault.  But, something did change their fiesystems in fstab.

I've made the changes in fstab, and everything is back to normal.

Thank you for your help, taurus.  :D 

nrwilk

---

### Post by taurus on 2007-01-04
> **nrwilk said:**
> Well, I must admit that I was wrong.  Neither of the two partitions should have contained fat32 filesystems.  But, the problem did still exist as I has stated it.

Something must have re-written my /etc/fstab because these two partitions, which had previously worked, somehow got their filesystems changed in fstab.

/dev/sda2 should have been ext3, and it was listed as vfat.

/dev/sda4 should have been ntfs, and it was listed as ext3.

So, it turns out that I was confusing the two.  This means that their sizes are correct.  My fault.  But, something did change their fiesystems in fstab.

I've made the changes in fstab, and everything is back to normal.

Thank you for your help, taurus.  :D 

nrwilk

I am still confused!!!  :twisted:

---

### Post by Mena.T.L on 2007-01-04
[B][COLOR="Blue"]OKay And mee Too Have Aproblem But Is That When I Refrmate My Partitions To ext3 

I Found That The File System Patition 

[IMG]http://i114.photobucket.com/albums/n246/menaabood/Screenshot.png[/IMG]

[IMG]http://i114.photobucket.com/albums/n246/menaabood/Screenshot-2.png[/IMG]
and Get This Thing Whay This Happened......... Thanks



ANd also Cant FInd My Patitions 


[COLOR="Red"]PLZ NEED HELP........... Thanks[/COLOR][/B][/COLOR]

---

