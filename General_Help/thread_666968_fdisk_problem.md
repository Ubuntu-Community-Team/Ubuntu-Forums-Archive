---
title: "fdisk problem"
date: 2008-01-13
forum: General Help
---

### Post by tvetter05 on 2008-01-13
I am trying to edit my menu.lst file to dual boot.  I have 2 sata drives in raid 0 with Windows XP and a IDE drive with ubuntu installed.  When I $ sudo fdisk -l i get:  

[HTML]Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13720258

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       18700   150207718+  83  Linux
/dev/hdc2           18701       19457     6080602+   5  Extended
/dev/hdc5           18701       19457     6080571   82  Linux swap / Solaris
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5

Unable to seek on /dev/sda

[/HTML]

Why wont the sata drives show?

---

### Post by articpenguin on 2008-01-13
i think they are corrupted partitions. Post your fstab.     

> cat /etc/fstab

---

### Post by tvetter05 on 2008-01-13
[HTML]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=045197c6-50dd-41fa-b2e1-35e6833d6c8d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=7961f40c-e020-476d-a2d0-73828b44dcb0 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
[/HTML]

I am able to run Windows on that array though.  Oh and while they are in a RAID 0 array, In Windows they are 2 separate NTFS partitions.

---

### Post by articpenguin on 2008-01-13
if those 2 partitions are NTFS you need ntfs-3g to mount them in linux.

read this about NTFS

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

---

### Post by polmir on 2008-01-13
```
 sudo lshw
```
and copy info about your disk.

---

### Post by tvetter05 on 2008-01-13
that requires knowing the names of the NTSF drives and the directions are for 7.04 and I am using 7.10, will its still work?

---

### Post by tvetter05 on 2008-01-13
lshw:
[HTML]        *-ide:1
             description: IDE Channel 1
             physical id: 1
             bus info: ide@1
             logical name: ide1
             clock: 66MHz
           *-disk
                description: ATA Disk
                product: ST3160023A
                vendor: Seagate
                physical id: 0
                bus info: ide@1.0
                logical name: /dev/hdc
                version: 3.06
                serial: 3JS24AST
                size: 149GB
                capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                configuration: mode=udma3 smart=on
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: ide@1.0,1
                   logical name: /dev/hdc1
                   capacity: 143GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: ide@1.0,2
                   logical name: /dev/hdc2
                   size: 5938MB
                   capacity: 5938MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/hdc5
                      capacity: 5938MB
                      capabilities: nofs
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-storage
          description: RAID bus controller
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi2
          logical name: scsi3
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: storage pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk:0
             description: SCSI Disk
             product: WDC WD2500KS-00M
             vendor: ATA
             physical id: 0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 02.0
             serial: WD-WCANK1846359
             size: 232GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
           *-volume
                description: HPFS/NTFS partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                capacity: 241GB
                capabilities: primary bootable
        *-disk:1
             description: SCSI Disk
             product: WDC WD2500KS-00M
             vendor: ATA
             physical id: 1
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: 02.0
             serial: WD-WCANK1846196
             size: 232GB
             configuration: ansiversion=5
[/HTML]
looks like its either sda or sda2

---

### Post by polmir on 2008-01-13
```
sudo fdisk -l /dev/hdc
```

 ```
sudo fdisk -l /dev/sda
```

 ```
sudo fdisk -l /dev/sdb
```

---

### Post by tvetter05 on 2008-01-13
[HTML]Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13720258

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       18700   150207718+  83  Linux
/dev/hdc2           18701       19457     6080602+   5  Extended
/dev/hdc5           18701       19457     6080571   82  Linux swap / Solaris
tristan@tristan-desktop:~$ sudo fdisk -l /dev/sda
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
tristan@tristan-desktop:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000201

Disk /dev/sdb doesn't contain a valid partition table
[/HTML]

---

### Post by polmir on 2008-01-14
```
sudo apt-get instal ntfs-3g
```

```
sudo apt-get install mdadm
```

and red man mdadm

---

### Post by tvetter05 on 2008-01-14
ok....what did that do?

---

### Post by polmir on 2008-01-14
mdadm is a program that can be used to create, manage, and monitor MD
arrays (e.g. software RAID, multipath devices)

[http://www.gentoo.org/doc/en/gentoo-x86-tipsntricks.xml]("http://www.gentoo.org/doc/en/gentoo-x86-tipsntricks.xml")

---

### Post by polmir on 2008-01-14
RAID is a problem.

---

### Post by polmir on 2008-01-14
Other info:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Create_A_Mount_Point_For_The_RAID_Set]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Create_A_Mount_Point_For_The_RAID_Set")

---

### Post by polmir on 2008-01-14
Please, read this:
[http://ubuntuforums.org/showthread.php?t=630644&highlight=raid]("http://ubuntuforums.org/showthread.php?t=630644&highlight=raid")
[https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")
[https://help.ubuntu.com/community/FakeRaidDebug]("https://help.ubuntu.com/community/FakeRaidDebug")
[http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation#Installation_on_RAID_0]("http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation#Installation_on_RAID_0")

---

### Post by tvetter05 on 2008-01-14
will i be able to do any of this without formating the RAID partitions?

---

### Post by tvetter05 on 2008-01-19
every time i do fdisk -l i get
[HTML]Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5

Unable to seek on /dev/sda
[/HTML]

---

