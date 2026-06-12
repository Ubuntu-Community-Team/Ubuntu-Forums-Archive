---
title: "[SOLVED] Recover Raid1 after system change"
date: 2008-04-12
forum: General Help
---

### Post by bergwiesel on 2008-04-12
Hi,

After some major troubles I installed Ubuntu 8.04 on my PC. Everything works just fine except my Raid1.
```

~$ sudo fdisk -l
Platte /dev/sda: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spuren, 60801 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x0007c63b

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1        7769    62404461   83  Linux
/dev/sda2            7770       60801   425979540   83  Linux

Platte /dev/sdb: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spuren, 60801 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x0007c63b

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               1        7769    62404461   83  Linux
/dev/sdb2            7770       60801   425979540   83  Linux

Platte /dev/md0: 500.1 GByte, 500107771904 Byte
255 Köpfe, 63 Sektoren/Spuren, 60801 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x0007c63b

    Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/md0p1               1        7769    62404461   83  Linux
/dev/md0p2            7770       60801   425979540   83  Linux

```

```

:/dev$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Dec 29 00:35:21 2007
     Raid Level : raid1
     Array Size : 488386496 (465.76 GiB 500.11 GB)
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Apr 12 00:51:35 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 5e95d56f:1f667248:f87bd1e7:7e760c96 (local to host abisko)
         Events : 0.6

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8        0        1      active sync   /dev/sda

```

```

mdadm --query --detail /dev/md0p1
mdadm: cannot open /dev/md0p1: No such file or directory 

```
There is no sda1, sda2, sdb1, sdb2, md0p1 or md0p2 in /dev

All I want is my data..

---

### Post by fjgaude on 2008-04-12
Maybe all you need to do is mount the /dev/md0 array and you will see what's there.

You have to first have made a mount point for which to mount to:

```
sudo mkdir /home/raid
```

Or whatever you wish to call the mount point.

Then try to mount:

```
sudo mount -t ext3 /dev/md0 /home/raid
```

I assume the array has a filetype of ext3, if not change to whatever it is.

Let us know how you are doing.

---

### Post by bergwiesel on 2008-04-12
I think, what I did was that I createt first the partitions sda1/2 and sdb1/2 and created out of them 2 raids md0p1 and md0p2
Someone else told me that it seams like that I first created a raid out of the two whole disks and secondly created 2 partitions within the raid

```

:/dev$ sudo mount -t ext3 /dev/md0 /media/multimedia
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error

```

The two partitions are ext3. It is really not important that the whole raid start to work again. At this point I just want all the data from the disks...

---

### Post by fjgaude on 2008-04-12
Well, if that is the case then all you have to do is mount one of the drives, since they were in raid1, each has the same data, eh?

```
sudo mount /dev/sda2 /media
```

You can do this if you are just getting the data and then not mounting the drive again, else create on mount point just for this drive.

If sda2 doesn't have the data, try sdb2.

---

### Post by bergwiesel on 2008-04-12
First of all there was no /dev/sda2 so I used
```

sudo mknod /dev/sda2 b 8 1 

```
Was this allright? "MAKEDEV sd" didn't create sda2 neither...
After mounting like you told me I get
```

mount: /dev/sda2 is not a valid block device.

```

---

### Post by fjgaude on 2008-04-12
Try using just sda or sdb... Things are not as I normally see them. Your array shows, with the --detail command, just sda and sdb.

```
sudo mount /dev/sda /media
```

See you that gets you anyway.

---

### Post by bergwiesel on 2008-04-12
Ok, I tried it
```

sudo mount /dev/sda /media
mount: unknown filesystem type 'linux_raid_member'

```
Is it somehow possible to remove the raid tag on the disks, so I could use the partitions?

Ok, somewhere else I got a hint, but I don't know how to use it...
```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=5e95d56f:1f667248:f87bd1e7:7e760c96
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=f383199f:d57a7174:f87bd1e7:7e760c96
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=b958bdf4:dbb4b475:f87bd1e7:7e760c96

# This file was auto-generated on Wed, 09 Apr 2008 00:06:17 +0200
# by mkconf $Id$

```
I guess there is something wrong, but I have no clue if these lines with UUID are right and how to change them so they are right.

---

### Post by fjgaude on 2008-04-12
You can zero superblocks but I can't say if your data will remain or not.

```
sudo mdadm --zero-superblock /dev/sd[nn]
```

You might simply remove the "raid" tag using **gparted** in Ubuntu, with the drives **unmounted** and then see if you can do with the drive what you wish.

You can use **cfdisk** to do the same thing... depends on if you wish to learn new things from the command line.

You likely, if you haven't done so previously, have to install gparted and/or cfdisk using apt-get:

```
sudo apt-get install gparted cfdisk
```

Let me know what happens. <smile>

---

### Post by bergwiesel on 2008-04-13
That was the hint I needed... 
With GParted I activated and deactivated the raid flag. Then I closed GParted and was able to mount my partitions with
```

sudo mount /dev/sda2 /media/multimedia -oro -text3

```
thanks for your help

---

### Post by fjgaude on 2008-04-13
Gosh, I tell you, it sure feels good when we achieve success in some hard-fought adventure, eh? We each learn something new each day, each moment of our lives.

---

### Post by bsmith1051 on 2008-04-15
> **bergwiesel said:**
> 
```

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=5e95d56f:1f667248:f87bd1e7:7e760c96
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=f383199f:d57a7174:f87bd1e7:7e760c96
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=b958bdf4:dbb4b475:f87bd1e7:7e760c96

```

Shouldn't he have just commented-out one of the two redundant definitions of 'md0' ?  I barely understand how this stuff works but the duplicate references seems like a clear error.

---

### Post by fjgaude on 2008-04-15
> **bsmith1051 said:**
> Shouldn't he have just commented-out one of the two redundant definitions of 'md0' ?  I barely understand how this stuff works but the duplicate references seems like a clear error.

Yes, I'm sure the duplication didn't help... now as I understand it he is just accessing the drives without any raid involved.

---

