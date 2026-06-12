---
title: "unable to open hdd in ubuntu"
date: 2016-11-25
forum: General Help
---

### Post by richlyn9 on 2016-11-25
unable to explore my HDD in ubuntu.
It shows up in manage devices in Win 7 but not in Gparted in Ubuntu.
i am now using a 1604 LTS live usb and  ran the below......



Its an WD 500 GB 3.5'' internal HDD which i am using as an external , connected to my laptop via usb.
in some code outputs its showing up as SDC.

```
ubuntu@ubuntu:~$** sudo fdisk -l**
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.3 GiB, 1433468928 bytes, 2799744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x21c1f6c2

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 404686847 404480000 192.9G  7 HPFS/NTFS/exFAT
/dev/sda3       404686848 614402047 209715200   100G  f W95 Ext'd (LBA)
/dev/sda4       614402048 976771071 362369024 172.8G  7 HPFS/NTFS/exFAT
/dev/sda5       404688896 614402047 209713152   100G  7 HPFS/NTFS/exFAT

Partition table entries are not in disk order.




Disk /dev/sdb: 15.1 GiB, 16219373568 bytes, 31678464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x05d54ab4

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 31678463 31676416 15.1G  c W95 FAT32 (LBA)


```

out put for ** sudo mount /dev/sdc /mnt**
```
ubuntu@ubuntu:~$** sudo mount /dev/sdc /mnt**
mount: /dev/sdc: can't read superblock
ubuntu@ubuntu:~$ **lsusb**
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 002 Device 006: ID 0cf3:3004 Atheros Communications, Inc. AR3012 Bluetooth 4.0
Bus 002 Device 003: ID 5986:055d Acer, Inc 
Bus 002 Device 008: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. JM20329 SATA Bridge
Bus 002 Device 002: ID 8564:1000 Transcend Information, Inc. JetFlash
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
ubuntu@ubuntu:~$ **dmesg | tail -n 20**
[ 1772.103103] sd 6:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 3a 38 5f 80 00 00 08 00
[ 1772.103109] blk_update_request: critical medium error, dev sdc, sector 976772992
[ 1772.103115] Buffer I/O error on dev sdc, logical block 122096624, async page read
[ 2247.061386] sd 6:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2247.061396] sd 6:0:0:0: [sdc] tag#0 Sense Key : Medium Error [current] 
[ 2247.061402] sd 6:0:0:0: [sdc] tag#0 Add. Sense: Unrecovered read error
[ 2247.061408] sd 6:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 3a 38 5f 80 00 00 08 00
[ 2247.061413] blk_update_request: critical medium error, dev sdc, sector 976772992
[ 2249.983117] sd 6:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2249.983125] sd 6:0:0:0: [sdc] tag#0 Sense Key : Medium Error [current] 
[ 2249.983130] sd 6:0:0:0: [sdc] tag#0 Add. Sense: Unrecovered read error
[ 2249.983135] sd 6:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 3a 38 5f 80 00 00 08 00
[ 2249.983138] blk_update_request: critical medium error, dev sdc, sector 976772992
[ 2249.983143] Buffer I/O error on dev sdc, logical block 122096624, async page read
[ 2254.197233] sd 6:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2254.197243] sd 6:0:0:0: [sdc] tag#0 Sense Key : Medium Error [current] 
[ 2254.197249] sd 6:0:0:0: [sdc] tag#0 Add. Sense: Unrecovered read error
[ 2254.197255] sd 6:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 00 00 00 00 00 00 01 00
[ 2254.197260] blk_update_request: critical medium error, dev sdc, sector 0
[ 2254.197310] FAT-fs (sdc): unable to read boot sector

```

Out put for  df -h
```
ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           791M  9.6M  781M   2% /run
/dev/sdb1        16G  1.4G   14G  10% /cdrom
/dev/loop0      1.4G  1.4G     0 100% /rofs
/cow            3.9G   47M  3.9G   2% /
tmpfs           3.9G  232K  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs           3.9G  132K  3.9G   1% /tmp
tmpfs           791M   96K  791M   1% /run/user/999
ubuntu@ubuntu:~$
```

---

### Post by richlyn9 on 2016-11-25
also run the below

ubuntu@ubuntu:~$ ls /dev/ | grep sd
sda
sda1
sda2
sda3
sda4
sda5
sdb
sdb1
sdc


Its the SDC thats having the issue

---

### Post by richlyn9 on 2016-11-25
i ran fdisk Again and got a different output.
however unable to mount 

```
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.3 GiB, 1433468928 bytes, 2799744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x21c1f6c2

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 404686847 404480000 192.9G  7 HPFS/NTFS/exFAT
/dev/sda3       404686848 614402047 209715200   100G  f W95 Ext'd (LBA)
/dev/sda4       614402048 976771071 362369024 172.8G  7 HPFS/NTFS/exFAT
/dev/sda5       404688896 614402047 209713152   100G  7 HPFS/NTFS/exFAT

Partition table entries are not in disk order.




Disk /dev/sdb: 15.1 GiB, 16219373568 bytes, 31678464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x05d54ab4

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 31678463 31676416 15.1G  c W95 FAT32 (LBA)


Disk /dev/sdc: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xae1f8566

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdc1              63 512007614 512007552 244.1G 83 Linux
/dev/sdc2       512007615 976768064 464760450 221.6G 83 Linux

```

ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
mount: special device /dev/sdc1 does not exist
ubuntu@ubuntu:~$ sudo mount /dev/sdc2 /mnt
mount: special device /dev/sdc2 does not exist
ubuntu@ubuntu:~$

---

### Post by Bucky Ball on 2016-11-26
Please use code tags for terminal output. There is a green link for how to use them in the first line of my signature at the bottom of this post. Neater, space saving and easier to read.

Not sure what we're looking for as you don't tell us how to identify the drive. Open a terminal, run this:

```
sudo blkid
```

See your drive there or any of the partitions on it? 

You give virtually no details about this drive so hard to say much. Internal? External? You are expecting it to show up as sd*? Your first internal drive should be sda, second and consequent drives sdb, sdc, etc. The partitions are designated by numbers, for instance, first partition on first drive would be sda1.

(Presuming the drive you are having issues with is sdc. What filesystem are the partitions? EXT? NFTS?)

PS: Not sure this has anything to do with your current issue.

> Partition table entries are not in disk order.

I picked that out from the code you've posted.

---

### Post by richlyn9 on 2016-11-26
Apologies for the improper Formatting...
Edited now.

Yes Its sdc
Its a WD 500 Gig, 3.5 external HDD which i have now connected via USB to a laptop to try and fix the issue.
Partitions i believe is EXT.

---

### Post by richlyn9 on 2016-11-26
> **Bucky Ball said:**
> 
PS: Not sure this has anything to do with your current issue.



I picked that out from the code you've posted.

I too am not sure about this...

---

### Post by richlyn9 on 2016-11-26
output for blkid
```

ubuntu@ubuntu:~$ blkid
/dev/sda1: LABEL="System Reserved" UUID="3664591F6458E363" TYPE="ntfs" PARTUUID="21c1f6c2-01"
/dev/sda2: UUID="4032F1A632F1A0D8" TYPE="ntfs" PARTUUID="21c1f6c2-02"
/dev/sda4: LABEL="New Volume" UUID="48D0D465D0D45AB0" TYPE="ntfs" PARTUUID="21c1f6c2-04"
/dev/sda5: LABEL="New Volume" UUID="8228E8BE28E8B1F9" TYPE="ntfs" PARTUUID="21c1f6c2-05"
/dev/sdb1: LABEL="UBUNTU 16_0" UUID="AAA7-203C" TYPE="vfat" PARTUUID="05d54ab4-01"
/dev/loop0: TYPE="squashfs"
ubuntu@ubuntu:~$ 
```

---

### Post by richlyn9 on 2016-11-26
fsck output

```
ubuntu@ubuntu:~$ sudo fsck /dev/sdc
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdc

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

ubuntu@ubuntu:~$ 

```

---

