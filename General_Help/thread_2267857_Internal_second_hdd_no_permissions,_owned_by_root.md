---
title: "Internal second hdd no permissions, owned by root"
date: 2015-03-04
forum: General Help
---

### Post by 010c-davis010 on 2015-03-04
New to Ubuntu and Linux in general but have been wanting to try it out. Finally took the plunge and installed Ubuntu 14.04 LTS which I really like so far but I am having an issue with my secondary hdd that I use for storage. I have no permissions on it and don't appear to be the owner of that drive.

I have the OS installed on my main 160gb drive (sdb) and my secondary 250gb drive (sda) I can't do anything with. I need to know how to change ownership of that drive so that I can use it. I have looked over many post and to be honest I'm not sure how many or if any of them apply to me so here I am.

Another post has having a similar problem and was told to run a few commands and report back what they said so I'll post those below to hopfully give you guys more info.





```
*-disk                  
       description: ATA Disk
       product: WDC WD2500AAJS-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WCAT1A764518
       size: 232GiB (250GB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=d15daf38-1036-4ea5-8784-40da1cbe4807 sectorsize=512
  *-disk
       description: ATA Disk
       product: Hitachi HDS72161
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: P22O
       serial: PVG904ZF062ETV
       size: 149GiB (160GB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=edc368e0-f6ce-4173-89a4-8bbed50b1648 sectorsize=512
  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GH22NS40
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       version: NL01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

```


```

*-volume                
       description: EXT4 volume
       vendor: Linux
       physical id: 1
       bus info: scsi@2:0.0.0,1
       logical name: /dev/sda1
       logical name: /media/zane/22e322d8-ac5e-4625-98c0-4c4c2b94916a
       version: 1.0
       serial: 22e322d8-ac5e-4625-98c0-4c4c2b94916a
       size: 232GiB
       capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
       configuration: created=2015-03-03 19:32:41 filesystem=ext4 modified=2015-03-04 10:50:11 mount.fstype=ext4 mount.options=rw,nosuid,nodev,relatime,data=ordered mounted=2015-03-04 10:50:11 state=mounted
  *-volume:0
       description: Windows FAT volume
       vendor: mkfs.fat
       physical id: 1
       bus info: scsi@3:0.0.0,1
       logical name: /dev/sdb1
       logical name: /boot/efi
       version: FAT32
       serial: 03d6-4f95
       size: 510MiB
       capacity: 511MiB
       capabilities: boot fat initialized
       configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
  *-volume:1
       description: EFI partition
       vendor: Linux
       physical id: 2
       bus info: scsi@3:0.0.0,2
       logical name: /dev/sdb2
       logical name: /boot
       version: 1.0
       serial: ee7a5ee0-1c02-4c75-8d3f-2f8a99c8c95c
       size: 244MiB
       capabilities: extended_attributes ext2 initialized
       configuration: filesystem=ext2 lastmountpoint=/boot modified=2015-03-04 07:24:24 mount.fstype=ext2 mount.options=rw,relatime mounted=2015-03-04 07:24:24 state=mounted
  *-volume:2
       description: LVM Physical Volume
       vendor: Linux
       physical id: 3
       bus info: scsi@3:0.0.0,3
       logical name: /dev/sdb3
       serial: 4v2hLh-cZKO-4Nh3-JGp8-Oxzf-tox4-cXNzZx
       size: 148GiB
       capabilities: multi lvm2

```



Any and all help would be greatly appreciated, thank you in advance!

---

### Post by oldfred on 2015-03-04
It looks like you have LVM, which is an advanced logical format overlaying the standard physical partitions. 
I do not know LVM, did you use it because you wanted full drive encryption?

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

If you have a non-LVM install you do have to install the lvm2 drivers to mount the LVM partitions.

---

### Post by 010c-davis010 on 2015-03-04
Not sure about the LVM, may have been an error on my part during installation. The drive encryption doesnt matter to me much and there is nothing currently on that drive, I just need it usable.

---

### Post by 010c-davis010 on 2015-03-04
Fixed, thanks for the help! After a bit more reading I decided to see what would happen if I unmounted it and after I did I saw the option to format the drive which I did which fixed everything, thanks again.

---

### Post by Bucky Ball on 2015-03-04
Good move. Yes, the partitions need to be unmounted to manipulate them. Consequently, if you were looking to resize your OS partition '/', you need to boot from live media so you can unmount the partition.

Please mark as solved (see the second link in my signature).

Enjoy. ;)

---

