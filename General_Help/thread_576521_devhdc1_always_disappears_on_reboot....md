---
title: "/dev/hdc1 always disappears on reboot..."
date: 2007-10-15
forum: General Help
---

### Post by etherag on 2007-10-15
Ok, so I have an ubuntu 7.04 system with a 5x250gb software Raid-5
array.

On boot, I get dropped to the recovery console, at which point /dev/
hdc1 is missing.  /dev/hdc is present, and running fdisk -l /dev/hdc
shows the proper partition is present.  Running partprobe doesnt pick
up the partition, and it isn't listed in /proc/partitions.

the way I have fixed this temporarily is as follows:

fdisk /dev/hdc
immediately hit w to rewrite the partition as it's currently setup.
mdadm /dev/md0 -a /dev/hdc1
mdadm -R /dev/md0

The array rebuilds, I fsck the array, mount the drive, boot into
ubuntu.

The problem is, I have to go through this every single time I
reboot.

So, does anyone have any thoughts as to why this is happening?

kernel version is 2.6.20-16-generic smp
ubuntu 7.04, completely updated as of last week.
motherboard is a  via P4-PB400.

```

--------------------------------------------------------
--  /etc/mdadm.conf:
--------------------------------------------------------

DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=5 UUID=4d06b8f6:35bfaa9f:
41b132e7:e26acd80
   spares=1

# This file was auto-generated on Fri, 01 Jun 2007 22:00:13 -0400
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $


```
```


--------------------------------------------------------
--  Excerpts from /var/log/dmesg
--------------------------------------------------------

[    5.376000]     ide1: BM-DMA at 0xdc08-0xdc0f, BIOS settings:
hdc:DMA, hdd:DMA
[    7.080000] Probing IDE interface ide1...
[    7.500000] hdc: WDC WD2500LB-55EDA0, ATA DISK drive
[    7.780000] hdd: WDC WD2500LB-55EDA0, ATA DISK drive
[    7.948000] hdc: max request size: 512KiB
[    7.952000] hdc: 488397168 sectors (250059 MB) w/2048KiB Cache,
CHS=30401/255/63, UDMA(33)
[    7.952000] hdc: cache flushes supported
[    7.952000]  hdc: hdc1
[    8.252000] md: md0 stopped.
[    8.252000] md: unbind<sdb1>
[    8.252000] md: export_rdev(sdb1)
[    8.252000] md: unbind<sda1>
[    8.252000] md: export_rdev(sda1)
[    8.504000] Attempting manual resume
[    8.504000] swsusp: Resume From Partition 3:5
[    8.504000] PM: Checking swsusp image.
[    8.504000] PM: Resume from disk failed.
[    8.508000] md: invalid raid superblock magic on sda
[    8.508000] md: sda has invalid sb, not importing!
[    8.508000] md: md_import_device returned -22
[    8.508000] md: invalid raid superblock magic on sda
[    8.508000] md: sda has invalid sb, not importing!
[    8.508000] md: md_import_device returned -22
[    8.508000] md: bind<sda1>
[    8.512000] md: bind<hdc>
[    8.512000] md: bind<sdb1>
[    8.544000] EXT3-fs: INFO: recovery required on readonly
filesystem.
[    8.544000] EXT3-fs: write access will be enabled during recovery.
[    8.844000] md: md0 stopped.
[    8.844000] md: unbind<sdb1>
[    8.844000] md: export_rdev(sdb1)
[    8.844000] md: unbind<hdc>
[    8.844000] md: export_rdev(hdc)
[    8.844000] md: unbind<sda1>
[    8.844000] md: export_rdev(sda1)
[    9.104000] md: bind<hdd1>
[    9.104000] md: bind<sda1>
[    9.104000] md: bind<hdb1>
[    9.112000] md: bind<hdc>
[    9.112000] md: bind<sdb1>
[    9.368000] md: md0 stopped.
[    9.368000] md: unbind<sdb1>
[    9.368000] md: export_rdev(sdb1)
[    9.368000] md: unbind<hdc>
[    9.368000] md: export_rdev(hdc)
[    9.368000] md: unbind<hdb1>
[    9.368000] md: export_rdev(hdb1)
[    9.368000] md: unbind<sda1>
[    9.368000] md: export_rdev(sda1)
[    9.368000] md: unbind<hdd1>
[    9.368000] md: export_rdev(hdd1)
.. clean md0's FS ..
[    9.696000] md: bind<hdd1>
[    9.696000] md: bind<sda1>
[    9.708000] md: bind<hdb1>
[    9.720000] md: bind<hdc>
[    9.720000] md: bind<sdb1>
[    9.780000] EXT3-fs: mounted filesystem with ordered data mode.
[   25.952000] r8169: eth0: link up
[   26.256000] NET: Registered protocol family 10
[   26.256000] lo: Disabled Privacy Extensions
[   27.264000] md: md0 stopped.
[   27.264000] md: unbind<sdb1>
[   27.264000] md: export_rdev(sdb1)
[   27.264000] md: unbind<hdc>
[   27.264000] md: export_rdev(hdc)
[   27.264000] md: unbind<hdb1>
[   27.264000] md: export_rdev(hdb1)
[   27.264000] md: unbind<sda1>
[   27.264000] md: export_rdev(sda1)
[   27.264000] md: unbind<hdd1>
[   27.264000] md: export_rdev(hdd1)
[   27.472000] md: bind<hdd1>
[   27.472000] md: bind<sda1>
[   27.472000] md: bind<hdb1>
[   27.480000] md: bind<hdc>
[   27.480000] md: bind<sdb1>
[   27.480000] md: kicking non-fresh hdc from array!
[   27.480000] md: unbind<hdc>
[   27.480000] md: export_rdev(hdc)
[   27.484000] md: md0: raid array is not clean -- starting background
reconstruction
[   27.572000] raid5: device sdb1 operational as raid disk 0
[   27.572000] raid5: device hdb1 operational as raid disk 4
[   27.572000] raid5: device sda1 operational as raid disk 3
[   27.572000] raid5: device hdd1 operational as raid disk 2
[   27.572000] raid5: cannot start dirty degraded array for md0
[   27.572000] RAID5 conf printout:
[   27.572000]  --- rd:5 wd:4
[   27.572000]  disk 0, o:1, dev:sdb1
[   27.572000]  disk 2, o:1, dev:hdd1
[   27.572000]  disk 3, o:1, dev:sda1
[   27.572000]  disk 4, o:1, dev:hdb1
[   27.572000] raid5: failed to run raid set md0
[   27.572000] md: pers->run() failed ...

Then this is the output from after I fix it:
[ 1600.328000]  hdc: hdc1
[ 1602.332000]  hdc: hdc1
[ 1624.644000] md: bind<hdc1>
[ 1643.792000] raid5: device hdc1 operational as raid disk 1
[ 1643.792000] raid5: device sdb1 operational as raid disk 0
[ 1643.792000] raid5: device hdb1 operational as raid disk 4
[ 1643.792000] raid5: device sda1 operational as raid disk 3
[ 1643.792000] raid5: device hdd1 operational as raid disk 2
[ 1643.792000] raid5: allocated 5245kB for md0
[ 1643.792000] raid5: raid level 5 set md0 active with 5 out of 5
devices, algorithm 2
[ 1643.792000] RAID5 conf printout:
[ 1643.792000]  --- rd:5 wd:5
[ 1643.792000]  disk 0, o:1, dev:sdb1
[ 1643.792000]  disk 1, o:1, dev:hdc1
[ 1643.792000]  disk 2, o:1, dev:hdd1
[ 1643.792000]  disk 3, o:1, dev:sda1
[ 1643.792000]  disk 4, o:1, dev:hdb1
[ 1643.792000] md: resync of RAID array md0
[ 1643.792000] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[ 1643.792000] md: using maximum available idle IO bandwidth (but not
more than 200000 KB/sec) for resync.
[ 1643.792000] md: using 128k window, over a total of 244195904
blocks. 

```

Anyone have any idea how to fix this?  If there's any other info you need, I'll get it for you.

---

