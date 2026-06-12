---
title: "boot messed after installed PopOS 20 to other nvme disk"
date: 2020-05-09
forum: General Help
---

### Post by stacygirl on 2020-05-09
[COLOR=#242729][FONT=Arial]I have a lenovo p73 laptop with nvidia GPU and happily using the ubuntu18.04 operation system. One day I decie to test PopOs 20.04 and installed it to my another NVME drive.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have to NVME Drive:[/FONT][/COLOR]
sudo parted -ls

Disk Flags: 

Model: SAMSUNG MZVLB1T0HBLR-000L7 (nvme)
Disk /dev/nvme0n1: 1024GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  512MB   511MB   ext2
 3      512MB   1050MB  538MB   fat32           EFI System Partition  boot, esp
 4      1050MB  1008GB  1007GB  ext4
 2      1008GB  1024GB  16.4GB  linux-swap(v1)


Model: SAMSUNG MZVLB1T0HBLR-000L7 (nvme)
Disk /dev/nvme1n1: 1024GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name      Flags
 1      2097kB  524MB   522MB   fat32                     boot, esp
 2      524MB   4819MB  4295MB  fat32           recovery  msftdata
 3      4819MB  1020GB  1015GB
 4      1020GB  1024GB  4295MB  linux-swap(v1)
[COLOR=#242729][FONT=Arial]Disk /dev/nvme0n1 is Ubuntu 18.04 Disk /dev/nvme1n1 is PoP OS 20.04 (LUKS encrypted)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]After I installed PopOs I coulnt boot my ubuntu 18 anymore. When I mount the ubuntu ext4 all my linux files all there . But I cant boot.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I try to boot with Refind The rEFInd Boot Manager which booting from usb and showing all the possible bootabe parts.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Its find the ubuntu but couldn boot . Its dropping the root and says:[/FONT][/COLOR]
The result is RESULT.
May 09 21:02:15 bcl systemd[1]: Dependency failed for File System Check on /dev/disk/by-uuid/D24C-0064.
-- Subject: Unit [email]systemd-fsck@dev-disk-by\x2duuid-D24C\x2d0064.servic[/email]e has failed
-- Defined-By: systemd
[COLOR=#242729][FONT=Arial]and many similar error . I attached the journalctl -xb output as text file along with the /etc/fstab (ubuntu 18).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I boot from ubuntu 18 usb stick and do fsck to devices all is clean.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How can I boot to my ubuntu ? Any help very appreciated.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]FSTAB:[/FONT][/COLOR]
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme1n1p4 during installation
UUID=b14e42e4-e9fd-4f71-b352-293deeb01af4 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=D24C-0064  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
[COLOR=#242729][FONT=Arial][JournalTxt]("https://pastebin.com/hN78GxYX")[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]BEST[/FONT][/COLOR]

---

### Post by oldfred on 2020-05-09
Have you tried dosfsck?

From:
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=D24C-0064  /boot/efi       vfat    umask=0077      0       1

then Make sure unmounted, or use live installer.
man dosfsck
sudo fsck.vfat -t -a /dev/nvme0n1p1

The -a seems to help in clearing dirty bit

---

