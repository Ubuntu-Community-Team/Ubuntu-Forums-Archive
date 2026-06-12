---
title: "Attempting to retrieve data from a BAD disk"
date: 2015-11-24
forum: General Help
---

### Post by PlainVanilla on 2015-11-24
I have a 500GB SATA hard drive (/dev/sdb) that I think is failing. I am currently using it as my secondary HDD and want to get any data that I can out of it. I can not mount any of the three partitions. I get the following error:

[mounting error.jpg]("http://s11.postimg.org/jgmml8fsj/Mounting_Error.jpg")

Doing sudo fdisk -l gives:

```
Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00044529

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    32798719    16398336   83  Linux
/dev/sda2        32800766    39069695     3134465    5  Extended
/dev/sda5        32800768    39069695     3134464   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005170c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   195314547    97656250   83  Linux
/dev/sdb2       195315710   976771071   390727681    5  Extended
/dev/sdb5       970504192   976771071     3133440   82  Linux swap / Solaris
/dev/sdb6       195315712   585938943   195311616   83  Linux
/dev/sdb7       585940992   970502143   192280576   83  Linux

Partition table entries are not in disk order

```

I tried to recover the file system with an alternative superblock

```
sudo mke2fs -n /dev/sdb6
mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
12214272 inodes, 48827904 blocks
2441395 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
1491 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872

```

```
sudo fsck.ext4 -v -y -b 163840 /dev/sdb6
Superblock needs_recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
/dev/sdb6: recovering journal
Error reading block 24151711 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes
Force rewrite? yes
~About 3200 more of these error reading block messages~
/dev/sdb6: ********** WARNING: Filesystem still has errors **********

```

And then I tried to mount the device

```

sudo mount -v /dev/sdb6 /mnt/data1
mount: you didn't specify a filesystem type for /dev/sdb6
       I will try all types mentioned in /etc/filesystems or /proc/filesystems
Trying ext3
Trying ext2
Trying ext4
Trying vfat
mount: /dev/sdb6: can't read superblock
```

I tried recovery with another superblock 

```
sudo fsck.ext4 -v -y -b 229376 /dev/sdb6 
e2fsck 1.42.9 (4-Feb-2014)
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb6
Could this be a zero-length partition? 
```

hmm.. when I checked fdisk -l again the drive was not there anymore

```
sudo fdisk -l 

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00044529

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    32798719    16398336   83  Linux
/dev/sda2        32800766    39069695     3134465    5  Extended
/dev/sda5        32800768    39069695     3134464   82  Linux swap / Solaris

```

I had to shutdown and restart the machine to get it to recognize /dev/sdb
Can anybody explain what is going on here and if there is anyway I can retrieve my data

---

### Post by PlainVanilla on 2015-11-24
I attempted to mount the drive after a system shutdown and restart and this is what I got

```
sudo mount -v /dev/sdb6 /mnt/data1
mount: you didn't specify a filesystem type for /dev/sdb6
       I will try type ext4
    mount: wrong fs type, bad option, bad superblock on /dev/sdb6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

The system syslog had the following as a result of the above mount attempt

```
Nov 24 12:53:28 shaik-home-18GB kernel: [  238.407484] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Nov 24 12:53:28 shaik-home-18GB kernel: [  238.407492] ata3.00: BMDMA stat 0x24
Nov 24 12:53:28 shaik-home-18GB kernel: [  238.407498] ata3.00: failed command: READ DMA EXT
Nov 24 12:53:28 shaik-home-18GB kernel: [  238.407507] ata3.00: cmd 25/00:f0:38:b8:28/00:00:17:00:00/e0 tag 0 dma 122880 in
Nov 24 12:53:28 shaik-home-18GB kernel: [  238.407507]          res 71/04:04:9d:00:32/04:00:00:00:00/e0 Emask 0x1 (device error)
Nov 24 12:53:28 shaik-home-18GB kernel: [  238.407513] ata3.00: status: { DRDY DF ERR }
Nov 24 12:53:28 shaik-home-18GB kernel: [  238.407516] ata3.00: error: { ABRT }
Nov 24 12:53:28 shaik-home-18GB kernel: [  238.500065] ata3.00: both IDENTIFYs aborted, assuming NODEV
Nov 24 12:53:28 shaik-home-18GB kernel: [  238.500072] ata3.00: revalidation failed (errno=-2)
Nov 24 12:53:28 shaik-home-18GB kernel: [  238.500086] ata3: soft resetting link
Nov 24 12:53:28 shaik-home-18GB kernel: [  238.688068] ata3.00: both IDENTIFYs aborted, assuming NODEV
Nov 24 12:53:28 shaik-home-18GB kernel: [  238.688075] ata3.00: revalidation failed (errno=-2)
Nov 24 12:53:33 shaik-home-18GB kernel: [  243.656040] ata3: soft resetting link
Nov 24 12:53:33 shaik-home-18GB kernel: [  243.868066] ata3.00: both IDENTIFYs aborted, assuming NODEV
Nov 24 12:53:33 shaik-home-18GB kernel: [  243.868073] ata3.00: revalidation failed (errno=-2)
Nov 24 12:53:33 shaik-home-18GB kernel: [  243.868078] ata3.00: disabled
Nov 24 12:53:33 shaik-home-18GB kernel: [  243.868097] ata3: EH complete
Nov 24 12:53:33 shaik-home-18GB kernel: [  243.868126] sd 2:0:0:0: [sdb] Unhandled error code
Nov 24 12:53:33 shaik-home-18GB kernel: [  243.868132] sd 2:0:0:0: [sdb]  
Nov 24 12:53:33 shaik-home-18GB kernel: [  243.868136] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Nov 24 12:53:33 shaik-home-18GB kernel: [  243.868140] sd 2:0:0:0: [sdb] CDB: 
Nov 24 12:53:33 shaik-home-18GB kernel: [  243.868143] Read(10): 28 00 17 28 b8 38 00 00 f0 00
Nov 24 12:53:33 shaik-home-18GB kernel: [  243.868160] end_request: I/O error, dev sdb, sector 388544568
Nov 24 12:53:33 shaik-home-18GB kernel: [  243.868179] JBD2: Failed to read block at offset 3598
Nov 24 12:53:33 shaik-home-18GB kernel: [  243.868212] end_request: I/O error, dev sdb, sector 0
Nov 24 12:53:33 shaik-home-18GB kernel: [  243.868223] JBD2: recovery failed
Nov 24 12:53:33 shaik-home-18GB kernel: [  243.868229] EXT4-fs (sdb6): error loading journal
```

---

### Post by tgalati4 on 2015-11-24
Did you reseat the power and SATA cable at both ends?  Try changing SATA ports.  Put it in a different computer in case your power supply is not providing enough current to spin the drive up to speed to mount correctly.

If you get the same behavior in a different computer, then you can be reasonably sure that the disk drive is having electronic/hardware problems, and not simply a filesystem error that can be fixed with an *fsck*.

---

### Post by PlainVanilla on 2015-11-24
I tried reseating the power and SATA cable at both ends but there is no difference. Now I have to try putting it in a different computer. I might add that the problem started after a power outage when the system shut down abruptly. The SMART check in the bios shows that the drive is BAD but its been showing that for the last two months so I didnt think it was serious. Apparently it is serious now. 
I will try installing the drive in another computer maybe tomorrow and update the thread.

---

### Post by tgalati4 on 2015-11-24
You were supposed to back up your data 2 months ago.  That is the purpose of SMART, to give you a heads up when a drive is failing.  Power outages and the voltage spike that happens when the power returns can damage power supplies.  It's possible that your PSU is failing as well.  So you could have two hardware issues--keep that in mind while you are troubleshooting.

---

### Post by dragonfly41 on 2015-11-24
It might be prudent to clone your (bad?) image over to a new drive (same size) as soon as you can.   
Then recover your data from the good drive, keeping the failing disk in reserve.

---

