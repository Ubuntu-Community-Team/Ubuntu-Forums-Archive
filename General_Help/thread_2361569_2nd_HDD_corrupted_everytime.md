---
title: "2nd HDD corrupted everytime"
date: 2017-05-18
forum: General Help
---

### Post by s-ghorai2 on 2017-05-18
I am using ubuntu 16.04 with Lenovo Desktop.
Also i have update with additional HDD and mounted properly to /hdd2
        $ sudo mkfs.ext4 -j -O extent -L "hdd2" /dev/sdb
        $ mkdir /hdd2
        $ sudo blkid /dev/sdb1
        $ sudo vim /etc/fstab
                UUID=2ad7029e-8a30-4f2a-9825-b9c1e916f925 /hdd2  ext4  relatime,errors=remount-ro  0  1
        $ sudo mount /dev/sdb1 /hdd2/


Worked fine for sometime. 


However /dev/sdb1 get corrupted in overnight (without doing anything)
1. Disk IO error in reboot
2. sudo mount /dev/sdb1 /hdd2/
mount: /dev/sdb1: can't read superblock

This issue i observed respectively two times and with two different HDD.

---

### Post by HermanAB on 2017-05-18
Bad disk controller, bad PSU, bad motherboard.... the list goes on and on.

---

### Post by oldfred on 2017-05-18
You may be using a mount that conflicts.

Before sda, drives were hda, so you could have hdd2 as 4th drive and second partition. Do not know how system now works but would avoid anything that might look like standard system name/label/mount.

---

### Post by VMC on 2017-05-18
What is the output of:
[COLOR=#000000]sudo blkid[/COLOR]

---

### Post by s-ghorai2 on 2017-05-22
Its very easy to reproduce and behavior followed:
* checked with two different HDD and observation same
* format to ext2/ext4 and mount, create/delete file working.
* leave the setup idle for over night.
* next day reboot and try to mount: 
$ sudo mount /dev/sdb1  /hdd2/
[sudo] password for sgh:
mount: /dev/sdb1: can't read superblock

Issue with secondary HDD only.

$ sudo blkid
/dev/sda1: UUID="d23d6d34-e798-4d25-8491-f9bc8b261a37" TYPE="ext4" PARTUUID="cb5d74f1-01"
/dev/sda5: UUID="7ea2ddb3-38d3-42fc-a902-6b8b378aadb9" TYPE="swap" PARTUUID="cb5d74f1-05"

dmesg--
[    3.607539] ata3.00: exception Emask 0x0 SAct 0x800000 SErr 0x0 action 0x0
[    3.607541] ata3.00: irq_stat 0x40000008
[    3.607542] ata3.00: failed command: READ FPDMA QUEUED
[    3.607544] ata3.00: cmd 60/08:b8:00:08:00/00:00:00:00:00/40 tag 23 ncq 4096 in
                        res 41/40:08:00:08:00/00:00:00:00:00/00 Emask 0x409 (media error) <F>
[    3.607545] ata3.00: status: { DRDY ERR }
[    3.607546] ata3.00: error: { UNC }
[    3.677279] ata3.00: configured for UDMA/133
[    3.677284] sd 2:0:0:0: [sdb] tag#23 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    3.677286] sd 2:0:0:0: [sdb] tag#23 Sense Key : Medium Error [current] [descriptor]
[    3.677288] sd 2:0:0:0: [sdb] tag#23 Add. Sense: Unrecovered read error - auto reallocate failed
[    3.677289] sd 2:0:0:0: [sdb] tag#23 CDB: Read(10) 28 00 00 00 08 00 00 00 08 00
[    3.677290] blk_update_request: I/O error, dev sdb, sector 2048
[    3.677293] ata3: EH complete

---

### Post by Bashing-om on 2017-05-22
s-ghorai2; wellll ..

> 
[ 3.677290] blk_update_request: I/O error, dev sdb, sector 2048

does not bode well ! -> file system errors and maybe hard drive failure .....
a) fsck
b) smartctl

On two different hard drives .. makes one question the hardware .
a) power supply
b) sata cable
c) sata controller

[INDENT][INDENT]that process of elimination
[/INDENT][/INDENT]

---

### Post by s-ghorai2 on 2017-05-23
The reason i am checking with Ubuntu forum -
-  issue happen([COLOR=#000000]can't read superblock)[/COLOR] when system is not used for long time (~6hr)

After reboot when HDD2 not usable, i try to format again - its saying "Found a dos partition table"
$ sudo mkfs.ext4 -j -O extent -L "hdd2" /dev/sdb
mke2fs 1.42.13 (17-May-2015)
Found a dos partition table in /dev/sdb
Proceed anyway? (y,n)

---

### Post by s-ghorai2 on 2017-05-24
Some extend I am agree, that issue with my Lenovo desktop.
And i did not face such issue with my other assembled PC.

---

