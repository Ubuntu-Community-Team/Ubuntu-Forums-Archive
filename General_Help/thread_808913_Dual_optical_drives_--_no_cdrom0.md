---
title: "Dual optical drives -- no cdrom0"
date: 2008-05-27
forum: General Help
---

### Post by Cerberus 81 on 2008-05-27
Having a lingering problem with Xubuntu 64-bit 8.04 Hardy Heron; I use a custom-built computer with dual optical drives -- an LG CD-RW drive on my ATA bus, and a SATA ASUS DVD-RW drive.  I was trying to install some system files in order to use NVIDIA's graphics driver (in order to make my dual-monitor configuration work as expected), but I received a prompt to insert my installation disc into a CD-ROM drive even though it already was.  The system would not recognize the CD-ROM in the proper drive, which I pinpointed to the fact that neither of my optical drives are mounting as "cdrom0" and thus are not being recognized as the system disks.  I did search for relevant information before, but the other threads I found had suggestions that didn't work in my case :(  Is anyone able to help a rank amateur with editing disk mount points in Linux?

Some (hopefully) relevant information:
```
????@????-desktop:~$ sudo lshw -C disk
  *-cdrom                 
       description: CD-R/CD-RW writer
       product: CD-RW GCE-8527B
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.04
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom2
  *-disk
       description: ATA Disk
       product: WDC WD5000AACS-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WCASU1740240
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d1d04d96
  *-disk
       description: ATA Disk
       product: ST3120813AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdb
       version: 3.AA
       serial: 4LS03R0T
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=a08fa08f
  *-cdrom
       description: DVD-RAM writer
       product: DRW-1814BLT
       vendor: ASUS
       physical id: 0
       bus info: scsi@6:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /media/Xubuntu 8.04 amd64
       version: 1.13
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/Xubuntu 8.04 amd64
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
  *-disk
       description: ATA Disk
       product: WDC WD2500KS-00M
       vendor: Western Digital
       physical id: 1
       bus info: scsi@7:0.0.0
       logical name: /dev/sdc
       version: 02.0
       serial: WD-WCANKE356363
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=456a4569
  *-disk:0
       description: SCSI Disk
       product: STORAGE DEVICE
       vendor: Generic
       physical id: 0.0.0
       bus info: scsi@8:0.0.0
       logical name: /dev/sdd
       version: 9317
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdd
  *-disk:1
       description: SCSI Disk
       product: STORAGE DEVICE
       vendor: Generic
       physical id: 0.0.1
       bus info: scsi@8:0.0.1
       logical name: /dev/sde
       version: 9317
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sde
  *-disk
       description: SCSI Disk
       product: Photosmart 3210
       vendor: HP
       physical id: 0.0.0
       bus info: scsi@9:0.0.0
       logical name: /dev/sdf
       version: 1.00
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sdf

```

---

