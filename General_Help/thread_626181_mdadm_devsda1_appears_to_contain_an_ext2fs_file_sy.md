---
title: "mdadm: /dev/sda1 appears to contain an ext2fs file system"
date: 2007-11-28
forum: General Help
---

### Post by fenifur on 2007-11-28
I am using the latest version of Ubuntu desktop - 7.10.  I have three 500Gb SATA harddrives. I also have an 120GB IDE drive which Ubuntu is installed on.  I am attempting to create four raid5 arrays.  What i've done so far:

Using gparted I partitioned each drive four ways approximately 116.44GB each partition.
gparted shows filesystem as ext3,  Raid flag is set.  I have attached the screen shot of gparted for the first drive.  All other drives are identical.  

I have the results from fdisk -l at the bottom.  I am attempting to create my raid volumes
with the following commands as root:

mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1
mdadm --create --verbose /dev/md1 --level=5 --raid-devices=3 /dev/sda2 /dev/sdb2 /dev/sdc2
mdadm --create --verbose /dev/md2 --level=5 --raid-devices=3 /dev/sda3 /dev/sdb3 /dev/sdc3
mdadm --create --verbose /dev/md3 --level=5 --raid-devices=3 /dev/sda4 /dev/sdb4 /dev/sdc4

When I execute these in a bash shell I get the following error:

mdadm: /dev/sda1 appears to contain an ext2fs file system
    size=122093968K  mtime=Sun Nov 25 16:39:37 2007
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=122093968K  mtime=Sun Nov 25 16:39:35 2007
mdadm: /dev/sdc1 appears to contain an ext2fs file system
    size=122093968K  mtime=Sun Nov 25 16:39:21 2007
mdadm: size set to 122093888K
Continue creating array? n

All four arrays produce the same error.  I attempted to stop each array using

mdadm --stop /dev/md0  

and then re-execute mdadm commands.  I'm not sure what I did wrong.  Any help would be greatly appreciated.

fdisk -l returns:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d30ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15200   122093968+  fd  Linux raid autodetect
/dev/sda2           15201       30401   122102032+  fd  Linux raid autodetect
/dev/sda3           30402       45601   122094000   fd  Linux raid autodetect
/dev/sda4           45602       60801   122094000   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00003cdd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15200   122093968+  fd  Linux raid autodetect
/dev/sdb2           15201       30401   122102032+  fd  Linux raid autodetect
/dev/sdb3           30402       45601   122094000   fd  Linux raid autodetect
/dev/sdb4           45602       60801   122094000   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c6288

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       15200   122093968+  fd  Linux raid autodetect
/dev/sdc2           15201       30401   122102032+  fd  Linux raid autodetect
/dev/sdc3           30402       45601   122094000   fd  Linux raid autodetect
/dev/sdc4           45602       60801   122094000   fd  Linux raid autodetect

Disk /dev/hda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c6745bd

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13991   112382676   83  Linux
/dev/hda2           13992       14589     4803435    5  Extended
/dev/hda5           13992       14589     4803403+  82  Linux swap / Solaris

---

### Post by fjgaude on 2007-11-28
I would ignore the error and continue to create the arrays. Then do:

sudo mdadm -D /dev/md0

And show us what you get.

---

### Post by fenifur on 2007-11-29
I got

mdadm: array /dev/md0 started.
mdadm: array /dev/md1 started.
mdadm: array /dev/md2 started.
mdadm: array /dev/md3 started.

I guess that is a good sign.

Thanks

---

### Post by fenifur on 2007-11-29
However, when I run fdisk -l I get

Disk /dev/md0: 250.0 GB, 250048282624 bytes
2 heads, 4 sectors/track, 61046944 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 250.0 GB, 250064797696 bytes
2 heads, 4 sectors/track, 61050976 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md2: 250.0 GB, 250048282624 bytes
2 heads, 4 sectors/track, 61046944 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md3: 250.0 GB, 250048282624 bytes
2 heads, 4 sectors/track, 61046944 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md3 doesn't contain a valid partition table


Is that because I am not done yet?

---

### Post by fenifur on 2007-11-29
I ran watch cat /proc/mdstat and this is what I see:

recovery = 18% (and climbing) on md0

Is this what is supposed to happen?

---

### Post by fenifur on 2007-11-29
Full file (/proc/mdstat):

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md3 : active raid5 sdc4[3] sdb4[1] sda4[0]
      244187776 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
        resync=DELAYED
      
md2 : active raid5 sdc3[3] sdb3[1] sda3[0]
      244187776 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
        resync=DELAYED
      
md1 : active raid5 sdc2[3] sdb2[1] sda2[0]
      244203904 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
        resync=DELAYED
      
md0 : active raid5 sdc1[3] sdb1[1] sda1[0]
      244187776 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
      [====>................]  recovery = 22.6% (27674504/122093888) finish=25.5min speed=61640K/sec
      
unused devices: <none>

---

### Post by fenifur on 2007-11-29
## /bin
=>mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Wed Nov 28 23:00:33 2007
     Raid Level : raid5
     Array Size : 244187776 (232.88 GiB 250.05 GB)
  Used Dev Size : 122093888 (116.44 GiB 125.02 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Nov 28 23:00:33 2007
          State : clean, degraded, recovering
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 26% complete

           UUID : f8a108d6:f7ef20e9:d860297e:f26445fe (local to host bills)
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       3       8       33        2      spare rebuilding   /dev/sdc1

---

### Post by fjgaude on 2007-11-29
Yes, that is what is supposed to happen. If they all build completely then:

```
sudo mkfs -t ext3 /dev/md0
```

on each one. Then do the sudo mdadm -D again. You should be able to mount them now.

Do you know how to mount disks?

---

### Post by fenifur on 2007-11-29
Not in detail.  I know I use the mount command.  I'll research it and If I have any issues I will reply to this thread.  Thanks for your help!

---

### Post by fenifur on 2007-12-01
ok.  I've created directories /s01, /s02, /s03 and /s04.  I edited my /etc/fstab with the following entry:

# sata drives raid 5
/dev/md0        /s01    ext3    defaults        0       0
/dev/md1        /s02    ext3    defaults        0       0
/dev/md2        /s03    ext3    defaults        0       0
/dev/md3        /s04    ext3    defaults        0       0

then mounted each device with

mount /s01
mount /s02
mount /s03
mount /s04

df -k /s* produces

=>df -k /s*
Filesystem           1K-blocks        Used     Available      Use% Mounted on
/dev/md0             240348396    191772 227947236   1%      /s01
/dev/md1             240370560    191772 227968596   1%      /s02
/dev/md2             240348396    191772 227947236   1%      /s03
/dev/md3             240348396    191772 227947236   1%      /s04

I can navigate to each one of these mount points.  However, when I run fdisk -l it returns:

Disk /dev/md3: 250.0 GB, 250048282624 bytes
2 heads, 4 sectors/track, 61046944 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md3 doesn't contain a valid partition table

Disk /dev/md2: 250.0 GB, 250048282624 bytes
2 heads, 4 sectors/track, 61046944 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md1: 250.0 GB, 250064797696 bytes
2 heads, 4 sectors/track, 61050976 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md0: 250.0 GB, 250048282624 bytes
2 heads, 4 sectors/track, 61046944 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Does gparted create it's own partition table that fdisk doesn't recognize or did I screw something up that I won't realize until some time later?

---

### Post by fenifur on 2007-12-01
While surfing the net from my desktop the following message appeared:

The kernel is unable to re-read the partitiontables on the following devices:
- /dev/md0
- /dev/md1
- /dev/md2

---

### Post by fenifur on 2007-12-01
Actually I was opening gparted when this message appeared.

---

### Post by fjgaude on 2007-12-01
Gparted doesn't know what to do with a raid array. But as long as you don't try to use Gparted to do anything to the array, nothing bad happens. It also sees the drives of the array as unknown.

Now, I can't say what happened when you lost the arrays. From where did the error message appear?

---

### Post by fenifur on 2007-12-01
I opened gparted and while it scans all devices the error message appeared.

---

### Post by fjgaude on 2007-12-01
After mounting the arrays, can you write to them?

---

### Post by fenifur on 2007-12-02
Yes I am able to write to each of these mount points:

/s01:
total 20
drwx------ 2 root root 16384 2007-12-01 10:58 lost+found
-rw-r--r-- 1 root root    12 2007-12-02 10:31 s01.txt

/s02:
total 20
drwx------ 2 root root 16384 2007-12-01 11:00 lost+found
-rw-r--r-- 1 root root    29 2007-12-02 10:32 s02.txt

/s03:
total 20
drwx------ 2 root root 16384 2007-12-01 11:03 lost+found
-rw-r--r-- 1 root root    34 2007-12-02 10:33 s03.txt

/s04:
total 20
drwx------ 2 root root 16384 2007-12-01 11:06 lost+found
-rw-r--r-- 1 root root    38 2007-12-02 10:33 s04.txt

root@xxxx:~# df -k /s0*
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/md0             240348396    191776 227947232   1% /s01
/dev/md1             240370560    191776 227968592   1% /s02
/dev/md2             240348396    191776 227947232   1% /s03
/dev/md3             240348396    191776 227947232   1% /s04

---

### Post by fjgaude on 2007-12-02
Well I would simply use the arrays and see how they act from here on out. Let us know if any trouble shows, or is this simply a test of things you have been wanting to try?

---

### Post by fenifur on 2007-12-02
Eventually they will be used to store mp3s and movies to be networked to other rooms in the house.  I may start over and use cfdisk to partition drives instead of gparted.  Thanks again for all your help.

---

### Post by fjgaude on 2007-12-02
I've used both and they are equally good. Good luck with whatever you do.

---

