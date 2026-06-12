---
title: "Boot errors"
date: 2018-03-28
forum: General Help
---

### Post by ansgar.snow on 2018-03-28
Hey.My pc is booting really slow, can we fix it somehow? 

I did journalctl -b into this file:

[https://pastebin.com/fBtJYcwY](https://pastebin.com/fBtJYcwY)


```
#lshw -short :

H/W path                   Device           Class          Description
======================================================================
                                            system         MS-7728 (To be filled by O.E.M.)
/0                                          bus            MS-7728
/0/0                                        memory         64KiB BIOS
/0/4                                        processor      Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz
/0/4/5                                      memory         32KiB L1 cache
/0/4/6                                      memory         256KiB L2 cache
/0/4/7                                      memory         3MiB L3 cache
/0/2a                                       memory         6GiB System Memory
/0/2a/0                                     memory         2GiB DIMM DDR3 Synchronous 1333 MHz (0,8 ns)
/0/2a/1                                     memory         4GiB DIMM DDR3 Synchronous 1333 MHz (0,8 ns)
/0/100                                      bridge         2nd Generation Core Processor Family DRAM Controller
/0/100/1                                    bridge         Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
/0/100/1/0                                  display        GM107 [GeForce GTX 750 Ti]
/0/100/1/0.1                                multimedia     NVIDIA Corporation
/0/100/16                                   communication  6 Series/C200 Series Chipset Family MEI Controller #1
/0/100/1a                                   bus            6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
/0/100/1a/1                usb1             bus            EHCI Host Controller
/0/100/1a/1/1                               bus            Integrated Rate Matching Hub
/0/100/1a/1/1/1                             multimedia     USB Audio CODEC
/0/100/1a/1/1/2                             input          USB Keyboard
/0/100/1b                                   multimedia     6 Series/C200 Series Chipset Family High Definition Audio Controller
/0/100/1c                                   bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 1
/0/100/1c.4                                 bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 5
/0/100/1c.4/0                               bus            ASM1042 SuperSpeed USB Host Controller
/0/100/1c.4/0/0            usb3             bus            xHCI Host Controller
/0/100/1c.4/0/1            usb4             bus            xHCI Host Controller
/0/100/1c.5                                 bridge         6 Series/C200 Series Chipset Family PCI Express Root Port 6
/0/100/1c.5/0              enp4s0           network        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/1d                                   bus            6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
/0/100/1d/1                usb2             bus            EHCI Host Controller
/0/100/1d/1/1                               bus            Integrated Rate Matching Hub
/0/100/1d/1/1/1                             generic        802.11 n WLAN
/0/100/1d/1/1/2                             input          USB Device
/0/100/1d/1/1/5            scsi6            storage        USB to S-ATA
/0/100/1d/1/1/5/0.0.0      /dev/sdc         disk           500GB SCSI Disk
/0/100/1d/1/1/5/0.0.0/1    /dev/sdc1        volume         46GiB EXT4 volume
/0/100/1d/1/1/5/0.0.0/2    /dev/sdc2        volume         7628MiB Linux swap volume
/0/100/1d/1/1/5/0.0.0/3    /dev/sdc3        volume         477MiB Windows FAT volume
/0/100/1d/1/1/5/0.0.0/4    /dev/sdc4        volume         411GiB Extended partition
/0/100/1d/1/1/5/0.0.0/4/5  /dev/sdc5        volume         186GiB EXT4 volume
/0/100/1d/1/1/5/0.0.0/4/6  /dev/sdc6        volume         49GiB HPFS/NTFS partition
/0/100/1d/1/1/5/0.0.0/4/7  /dev/sdc7        volume         27GiB EXT4 volume
/0/100/1d/1/1/5/0.0.0/4/8  /dev/sdc8        volume         3838MiB Linux swap volume
/0/100/1d/1/1/5/0.0.0/4/9  /dev/sdc9        volume         95GiB Linux filesystem partition
/0/100/1d/1/1/5/0.0.0/4/a  /dev/sdc10       volume         48GiB EXT4 volume
/0/100/1d/1/1/6            scsi7            storage        Mass Storage
/0/100/1d/1/1/6/0.0.0      /dev/sdd         disk           4027MB Flash Disk
/0/100/1d/1/1/6/0.0.0/0    /dev/sdd         disk           4027MB 
/0/100/1d/1/1/6/0.0.0/0/2  /dev/sdd2        volume         64MiB Windows FAT volume
/0/100/1f                                   bridge         H61 Express Chipset Family LPC Controller
/0/100/1f.2                                 storage        6 Series/C200 Series Chipset Family SATA AHCI Controller
/0/100/1f.3                                 bus            6 Series/C200 Series Chipset Family SMBus Controller
/0/1                       scsi0            storage        
/0/1/0.0.0                 /dev/sda         disk           500GB WDC WD5000AAKX-0
/0/1/0.0.0/1               /dev/sda1        volume         699MiB Windows FAT volume
/0/1/0.0.0/2               /dev/sda2        volume         397GiB Windows NTFS volume
/0/1/0.0.0/3               /dev/sda3        volume         58GiB EXT4 volume
/0/1/0.0.0/4               /dev/sda4        volume         9000MiB Linux swap volume
/0/2                       scsi1            storage        
/0/2/0.0.0                 /dev/sdb         disk           80GB SAMSUNG SP0812C
/0/2/0.0.0/1               /dev/sdb1        volume         350MiB Windows NTFS volume
/0/2/0.0.0/2               /dev/sdb2        volume         73GiB Windows NTFS volume
/0/2/0.0.0/3               /dev/sdb3        volume         848MiB Windows NTFS volume
/1                                          power          To Be Filled By O.E.M.
/2                                          power          To Be Filled By O.E.M.
/3                         wlx00e45c09429a  network        Wireless interface



```

```

$ uname -a
Linux android 4.13.0-37-generic #42-Ubuntu SMP Wed Mar 7 14:13:23 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

If anybody can help me with this one I would be happy!

---

### Post by oldfred on 2018-03-28
What brand/model system?
I see Android, so not a standard PC?
What flavor of Ubuntu?

Often slow boot relates to video driver not correct or correctly configured or hard drive issues.

---

### Post by ansgar.snow on 2018-03-29
Hi.I run ubuntu budgie, android is just a hostname.
I would say that video driver seems to be installed correctly.
Disk errors more likely could be the case, but how should I fix it without destroying filesystems?

---

### Post by oldfred on 2018-03-29
Post these.
Sometimes the UUIDs of swap or some other partition get mixed up.
       sudo blkid -c /dev/null -o list 
cat /etc/fstab

And you can run fsck.
      
 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by ansgar.snow on 2018-03-29
```
$ sudo blkid -c /dev/null -o listdevice     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/loop0 squashfs         /snap/core/4110 
/dev/loop1 squashfs         /snap/pycharm-community/51 
/dev/loop2 squashfs         /snap/pycharm-educational/3 
/dev/loop3 squashfs         /snap/pycharm-community/56 
/dev/loop4 squashfs         /snap/core/4206 
/dev/sda1  vfat             (not mounted)  10BB-7A1D
/dev/sda2  ntfs             (not mounted)  7748281F3426F581
/dev/sda3  ext4             (not mounted)  a4491222-fcc0-491a-a566-5808366789bb
/dev/sda4  swap             (not mounted)  cdce95a6-76b2-407d-bf4c-9b1837340e92
/dev/sdb1  ntfs    System Reserved (not mounted) 3AC8F13FC8F0FA49
/dev/sdb2  ntfs             (not mounted)  4E3201E23201D03F
/dev/sdb3  ntfs             (not mounted)  CAE8B972E8B95D7F
/dev/sdc1  ext4             /              5aeec94f-62d7-45c8-a83a-0f9bdf87bff3
/dev/sdc2  swap             (not mounted)  b0cd166b-1b09-4ef8-8d60-d7e7c92dc9dc
/dev/sdc3  vfat             (not mounted)  9C61-D5CB
/dev/sdc5  ext4    home     /home          21cb77e5-996f-447e-887c-4b9df9340535
/dev/sdc6  ext4             (not mounted)  6c511469-886d-4fbd-be09-785b661d927d
/dev/sdc7  swap             (not mounted)  a780dab4-439e-4882-9666-7c78c7b46aba
/dev/sdc8  crypto_LUKS      (not mounted)  11984279-448b-4df3-99e1-54fb48d73381
/dev/sdc9  ext4             (not mounted)  58bb48b0-487a-427e-94c1-10d968d1f952
/dev/sdc10 ext4             (not mounted)  c946be98-e324-4150-8ba1-4a3b7141db07
/dev/sdd1  iso9660 MJRO1717 (not mounted)  2018-03-27-19-11-24-00
/dev/sdd2  vfat    MISO_EFI (not mounted)  5C2A-FAE6



```

/etc/fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass># / was on /dev/sdc1 during installation
UUID=5aeec94f-62d7-45c8-a83a-0f9bdf87bff3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc5 during installation
UUID=21cb77e5-996f-447e-887c-4b9df9340535 /home           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=c7c694fc-5a19-4647-9bf2-bf9d5f3fe994 none            swap    sw              0       0
# swap was on /dev/sdc2 during installation
UUID=e155d7ed-913b-4091-af32-ff6d7735edab none            swap    sw              0       0
# swap was on /dev/sdc9 during installation
UUID=01fc0a3b-8793-471a-a2be-9231c83a308e none            swap    sw              0       0



```

Okay, so soon I will try to run fsck from live usb and will be back here with result.
Ty for your replies.

---

### Post by oldfred on 2018-03-29
You are showing 3 different swaps being mounted in fstab.
You only need one.

And none of the ones in fstab match UUIDs of swap partitions.

I did end up adding swap partition on every drive. And a new install finds them all. And sometimes it reformatted it changing UUID.
So I comment out all but one swap, and make sure UUID matches.

If you have more than 4GB of RAM, you may not even need any swap, but I like to have a little bit.

---

