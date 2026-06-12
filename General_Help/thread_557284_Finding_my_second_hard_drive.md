---
title: "Finding my second hard drive"
date: 2007-09-22
forum: General Help
---

### Post by josefs on 2007-09-22
I've gotten myself a new laptop with Vista preinstalled and I've installed Ubuntu to dual boot alongside Vista. The computer is equipped with two 120gb hard drives, let's call them A and B. Drive A hosts both Vista, Ubuntu and the swap partition. Drive B is completely empty. Now to my problem: I have no way to get access to drive B from Ubuntu. It shows up perfectly in Vista but not a trace from it inside Ubuntu.

Here's the output from "sudo fdisk -l"
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8337    66962658    7  HPFS/NTFS
/dev/sda2           13764       14593     6666975    7  HPFS/NTFS
/dev/sda3            8338       13535    41752935   83  Linux
/dev/sda4           13536       13763     1831410    5  Extended
/dev/sda5           13536       13763     1831378+  82  Linux swap / Solaris

```
Any clue as to how to proceed is appreciated.

Cheers,

Josef

---

### Post by hendoc on 2007-09-22
try "lshw" to see if Ubuntu sees it.

---

### Post by josefs on 2007-09-22
Thanks for your fast reply hendoc!

Not much luck with "lshw -C disk":
```

  *-cdrom
       description: DVD-RAM writer
       product: Slimtype DVD A DS8A1H
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: WH66
       serial: 707170055833
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audi
o cd-r cd-rw dvd dvd-r dvd-ram
     *-disc
          physical id: 0
          logical name: /dev/hda
  *-disk
       description: SCSI Disk
       product: TOSHIBA MK1237GS
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: DL13
       serial: 77UGF4FXS
       size: 111GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: HPFS/NTFS partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 63GB
          capabilities: primary bootable
     *-volume:1
          description: HPFS/NTFS partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          capacity: 6510MB
          capabilities: primary
     *-volume:2
          description: Linux filesystem partition
          physical id: 3
          bus info: scsi@0:0.0.0,3
          logical name: /dev/sda3
          capacity: 39GB
          capabilities: primary
     *-volume:3
          description: Extended partition
          physical id: 4
          bus info: scsi@0:0.0.0,4
          logical name: /dev/sda4
          size: 1788MB
          capacity: 1788MB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume
             description: Linux swap / Solaris partition
             physical id: 5
             logical name: /dev/sda5
             capacity: 1788MB
             capabilities: nofs

```

---

