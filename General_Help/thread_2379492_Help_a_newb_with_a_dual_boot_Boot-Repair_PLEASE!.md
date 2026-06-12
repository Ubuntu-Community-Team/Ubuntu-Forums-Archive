---
title: "Help a newb with a dual boot Boot-Repair PLEASE!"
date: 2017-12-06
forum: General Help
---

### Post by jaypier0788 on 2017-12-06
Hello,

I am trying to figure out how to boot into Ubuntu after downloading and installing windows 7, currently I am able to boot into Windows just fine. Previously I was using Ubuntu (version 16.04, I think?) I messed around with making a partition and somehow messed something up. I even tried re-downloading Ubuntu and creating a new flash drive with a new ISO image of Ubuntu on it. Every time I run Boot-Repair from terminal it says that the repair was successful and that it is okay to go ahead and restart the computer. I have included the information from the paste bin provided from Boot-repair. I am pretty new to everything Linux and have only been toying with Ubuntu now for a few months I am sure this is an easy fix or something I have made a simple mistake on. It would be much appreciated if someone could please help me out by pointing out what it is I am doing wrong as I can not get booted into Ubuntu for the life of me. Thanks in advance for any help given, I very much appreciate it. Also, if I am unable to boot into Ubuntu I really would just like to access the files I had on that partition. Is it possible to do this from windows? Although that's not what I want to do if that is the only way to recover my media files that seem to be stuck in a partition that I cannot find now that Ubuntu was previously installed on, that would be fine. [B]Thank You!
[/B]
[B]Boot-repair info pasted below or could be viewed here
 [/B]        [http://paste.ubuntu.com/26123394/](http://paste.ubuntu.com/26123394/) 
  
```
Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sda.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32776 of /dev/sdf1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    31,676,415    31,674,368  83 Linux
/dev/sda2    *     31,676,416   310,540,287   278,863,872   7 NTFS / exFAT / HPFS
/dev/sda3         310,542,334   625,141,759   314,599,426   5 Extended
/dev/sda5         601,028,608   625,141,759    24,113,152  82 Linux swap / Solaris
/dev/sda6         310,542,336   601,028,607   290,486,272  83 Linux


Drive: sdf _____________________________________________________________________
Disk /dev/sdf: 7.6 GiB, 8166703104 bytes, 15950592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1    *          2,048    15,950,591    15,948,544   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        adda1633-63cd-424f-873f-0ad3cd63fe57   ext4       
/dev/sda2        220C8676712E0937                       ntfs       
/dev/sda5        bc729b25-f3bc-441a-be37-546f27d2dd85   swap       
/dev/sda6        a7eb2230-4547-4516-a792-de2c8965f63a   ext4       
/dev/sdf1        E8B0-61B2                              vfat       UBUNTU 17_1

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Dec  6 07:07 ata-WDC_WD3200AAJS-22B4A0_WD-WCAT12170925 -> ../../sda
lrwxrwxrwx 1 root root 10 Dec  6 07:07 ata-WDC_WD3200AAJS-22B4A0_WD-WCAT12170925-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Dec  6 07:07 ata-WDC_WD3200AAJS-22B4A0_WD-WCAT12170925-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Dec  6 07:07 ata-WDC_WD3200AAJS-22B4A0_WD-WCAT12170925-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Dec  6 07:07 ata-WDC_WD3200AAJS-22B4A0_WD-WCAT12170925-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Dec  6 07:07 ata-WDC_WD3200AAJS-22B4A0_WD-WCAT12170925-part6 -> ../../sda6
lrwxrwxrwx 1 root root  9 Dec  6 07:03 ata-hp_DDVDW_TS-H653R_R3786GAS92433600 -> ../../sr0
lrwxrwxrwx 1 root root  9 Dec  6 07:03 usb-Generic-_Compact_Flash_20060413092100000-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  9 Dec  6 07:03 usb-Generic-_MS_MS-Pro_20060413092100000-0:3 -> ../../sde
lrwxrwxrwx 1 root root  9 Dec  6 07:03 usb-Generic-_SD_MMC_20060413092100000-0:2 -> ../../sdd
lrwxrwxrwx 1 root root  9 Dec  6 07:03 usb-Generic-_SM_xD-Picture_20060413092100000-0:1 -> ../../sdc
lrwxrwxrwx 1 root root  9 Dec  6 07:07 usb-PNY_USB_2.0_FD_0416000000007615-0:0 -> ../../sdf
lrwxrwxrwx 1 root root 10 Dec  6 07:07 usb-PNY_USB_2.0_FD_0416000000007615-0:0-part1 -> ../../sdf1
lrwxrwxrwx 1 root root  9 Dec  6 07:07 wwn-0x50014ee1011fbd51 -> ../../sda
lrwxrwxrwx 1 root root 10 Dec  6 07:07 wwn-0x50014ee1011fbd51-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Dec  6 07:07 wwn-0x50014ee1011fbd51-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Dec  6 07:07 wwn-0x50014ee1011fbd51-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Dec  6 07:07 wwn-0x50014ee1011fbd51-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Dec  6 07:07 wwn-0x50014ee1011fbd51-part6 -> ../../sda6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdf1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdf1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------

=================== sdf1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdf1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  4d 77 50 49 44 67 36 54  2f 33 4e 49 50 2b 48 37  |MwPIDg6T/3NIP+H7|
00000010  47 47 62 50 42 2f 5a 54  32 4a 42 2f 68 65 2f 69  |GGbPB/ZT2JB/he/i|
00000020  64 46 46 66 47 6f 36 65  66 50 33 7a 6d 59 52 39  |dFFfGo6efP3zmYR9|
00000030  69 66 33 71 59 46 33 71  32 64 48 37 76 58 35 65  |if3qYF3q2dH7vX5e|
00000040  67 71 72 4c 68 6d 36 56  54 57 56 5a 6b 51 71 61  |gqrLhm6VTWVZkQqa|
00000050  49 6c 61 4d 71 71 50 7a  75 2b 46 53 31 38 2f 64  |IlaMqqPzu+FS18/d|
00000060  54 79 39 68 2f 49 48 54  61 78 68 2f 34 47 51 56  |Ty9h/IHTaxh/4GQV|
00000070  64 76 2f 75 47 39 43 33  32 64 4f 4a 2f 43 6a 63  |dv/uG9C32dOJ/Cjc|
00000080  52 77 47 77 52 58 78 76  44 58 68 2b 44 75 6c 6e  |RwGwRXxvDXh+Duln|
00000090  4a 70 79 66 59 31 32 66  50 32 58 31 6f 46 63 70  |JpyfY12fP2X1oFcp|
000000a0  35 5a 58 69 43 6e 78 64  6d 50 38 79 44 58 72 68  |5ZXiCnxdmP8yDXrh|
000000b0  38 65 6d 4a 79 2b 63 78  35 66 76 31 35 34 50 49  |8emJy+cx5fv154PI|
000000c0  38 6e 61 78 6f 6a 4a 72  39 30 35 46 45 32 58 54  |8naxojJr905FE2XT|
000000d0  73 43 78 68 35 48 6b 35  63 66 74 66 79 34 79 4a  |sCxh5Hk5cftfy4yJ|
000000e0  75 38 51 79 59 31 4a 66  2b 78 55 68 65 66 4e 57  |u8QyY1Jf+xUhefNW|
000000f0  4c 68 32 78 33 70 59 64  49 50 4c 7a 65 4e 34 5a  |Lh2x3pYdIPLzeN4Z|
00000100  59 50 73 41 45 5a 2b 44  48 65 4c 4c 33 64 50 48  |YPsAEZ+DHeLL3dPH|
00000110  30 39 2f 61 6e 34 2b 73  6c 76 52 44 4d 39 45 4d  |09/an4+slvRDM9EM|
00000120  71 57 71 58 35 7a 33 6d  46 74 68 76 2f 2f 75 57  |qWqX5z3mFthv//uW|
00000130  43 58 6b 43 50 54 34 44  79 4d 79 45 31 63 38 4d  |CXkCPT4DyMyE1c8M|
00000140  35 4f 65 48 37 67 74 66  54 2f 55 4c 53 6c 71 39  |5OeH7gtfT/ULSlq9|
00000150  67 6c 38 76 62 68 50 79  42 66 61 6a 41 4a 69 31  |gl8vbhPyBfajAJi1|
00000160  69 50 78 37 30 44 65 58  4d 2b 7a 35 51 38 6a 33  |iPx70DeXM+z5Q8j3|
00000170  76 76 32 64 64 4c 35 78  38 33 6d 45 2f 67 42 38  |vv2ddL5x83mE/gB8|
00000180  47 37 44 37 6b 75 6a 76  54 63 46 2b 35 58 5a 33  |G7D7kujvTcF+5XZ3|
00000190  2f 61 57 62 6e 36 63 79  7a 76 37 37 32 5a 63 54  |/aWbn6cyzv772ZcT|
000001a0  39 57 2f 41 35 77 45 62  4c 79 66 36 32 51 50 50  |9W/A5wEbLyf62QPP|
000001b0  7a 73 4c 66 50 54 66 68  39 52 55 48 56 54 00 fe  |zsLfPTfh9RUHVT..|
000001c0  ff ff 82 fe ff ff 02 78  50 11 00 f0 6f 01 00 fe  |.......xP...o...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 78 50 11 00 00  |...........xP...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/5344/mountinfo) leaked on lvs invocation. Parent PID 11841: bash
File descriptor 63 (pipe:[74938]) leaked on lvs invocation. Parent PID 11841: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 20171206_0707 ===================
boot-repair version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
boot-repair is executed in live-session (Ubuntu 17.10, artful, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --- maybe-ubiquity
ls: cannot access '/home/usr/.config': No such file or directory

=================== os-prober:
/dev/sda2:Windows 7:Windows:chain

=================== blkid:
/dev/sda1: UUID="adda1633-63cd-424f-873f-0ad3cd63fe57" TYPE="ext4" PARTUUID="aead869a-01"
/dev/sda2: UUID="220C8676712E0937" TYPE="ntfs" PARTUUID="aead869a-02"
/dev/sda6: UUID="a7eb2230-4547-4516-a792-de2c8965f63a" TYPE="ext4" PARTUUID="aead869a-06"
/dev/sdf1: LABEL="UBUNTU 17_1" UUID="E8B0-61B2" TYPE="vfat" PARTUUID="14e8e4a1-01"
/dev/loop0: TYPE="squashfs"
/dev/sda5: UUID="bc729b25-f3bc-441a-be37-546f27d2dd85" TYPE="swap" PARTUUID="aead869a-05"


1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.


=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sda2.
sda6    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sda6.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:320GB:scsi:512:512:msdos:ATA WDC WD3200AAJS-2:;
1:1049kB:16.2GB:16.2GB:ext4::;
2:16.2GB:159GB:143GB:ntfs::boot;
3:159GB:320GB:161GB:::;
6:159GB:308GB:149GB:ext4::;
5:308GB:320GB:12.3GB:linux-swap(v1)::;

BYT;
/dev/sdf:8167MB:scsi:512:512:msdos:PNY USB 2.0 FD:;
1:1049kB:8167MB:8166MB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
loop0 loop squashfs   1.3G
sda   disk          298.1G
sda1  part ext4      15.1G
sda2  part ntfs       133G
sda3  part              1K
sda5  part swap      11.5G
sda6  part ext4     138.5G
sdf   disk            7.6G
sdf1  part vfat       7.6G UBUNTU 17_1
sr0   rom            1024M

KNAME ROTA RO RM STATE   MOUNTPOINT
loop0    1  1  0         /rofs
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0         /mnt/boot-sav/sda2
sda3     1  0  0
sda5     1  0  0         [SWAP]
sda6     1  0  0         /mnt/boot-sav/sda6
sdf      1  0  1 running
sdf1     1  0  1         /cdrom
sr0      1  0  1 running


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=2874040k,nr_inodes=718510,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=584956k,mode=755)
/dev/sdf1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=30,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=13379)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
mqueue on /dev/mqueue type mqueue (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=584952k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw,relatime,data=ordered)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type ext4 (rw,relatime,data=ordered)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda3 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdf1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency cuse disk dri dvd dvdrw ecryptfs fb0 fd full fuse fw0 hidraw0 hidraw1 hidraw2 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 initctl input kmsg lightnvm log mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda5 sda6 sdb sdc sdd sde sdf sdf1 sg0 sg1 sg2 sg3 sg4 sg5 sg6 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb userio vfio vga_arbiter vhci vhost-net vhost-vsock zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 58 e3 01  |........?....X..|
00000020  00 00 00 00 80 00 80 00  ff 1f 9f 10 00 00 00 00  |................|
00000030  04 00 00 00 00 00 00 00  ff f1 09 01 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  37 09 2e 71 76 86 0c 22  |........7..qv.."|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  2.8G     0  2.8G   0% /dev
tmpfs          tmpfs     572M  8.9M  563M   2% /run
/dev/sdf1      vfat      7.6G  1.4G  6.2G  19% /cdrom
/dev/loop0     squashfs  1.4G  1.4G     0 100% /rofs
/cow           overlay   2.8G   78M  2.8G   3% /
tmpfs          tmpfs     2.8G     0  2.8G   0% /dev/shm
tmpfs          tmpfs     5.0M  8.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.8G     0  2.8G   0% /sys/fs/cgroup
tmpfs          tmpfs     2.8G     0  2.8G   0% /tmp
tmpfs          tmpfs     572M   56K  572M   1% /run/user/999
/dev/sda1      ext4       15G   40M   14G   1% /mnt/boot-sav/sda1
/dev/sda2      fuseblk   133G  8.4G  125G   7% /mnt/boot-sav/sda2
/dev/sda6      ext4      137G   60M  130G   1% /mnt/boot-sav/sda6

=================== fdisk -l:
Disk /dev/loop0: 1.3 GiB, 1425731584 bytes, 2784632 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xaead869a

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048  31676415  31674368  15.1G 83 Linux
/dev/sda2  *     31676416 310540287 278863872   133G  7 HPFS/NTFS/exFAT
/dev/sda3       310542334 625141759 314599426   150G  5 Extended
/dev/sda5       601028608 625141759  24113152  11.5G 82 Linux swap / Solaris
/dev/sda6       310542336 601028607 290486272 138.5G 83 Linux

Partition table entries are not in disk order.




Disk /dev/sdf: 7.6 GiB, 8166703104 bytes, 15950592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x14e8e4a1

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdf1  *     2048 15950591 15948544  7.6G  c W95 FAT32 (LBA)



=================== Recommended repair
The default repair of the Boot-Repair utility will restore the [(generic mbr)] MBR in sda, and make it boot on sda2.
Additional repair will be performed: unhide-bootmenu-10s


Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr/mbr.bin of=/dev/sda
0+1 records in
0+1 records out

Boot successfully repaired.

You can now reboot your computer.
```

---

### Post by jaweewo on 2017-12-06
So much text O.o

Okay so, if you want to boot Ubuntu, if you have it in a different disk(not partition) you will be able to boot it using your boot menu in your computer. If it is in a different partition you wont be able, windows delete linux partitions, its a bug. So, you can check your data and save it using a live linux.

Hope it helps.

---

### Post by oldfred on 2017-12-06
Please use code tags if posting terminal or longer output. Easy to add in forum's advanced editor and # icon.
Also post clickable links. With Boot-Repairs post to pastebin site, that is all you really need.

You show two Linux partitions, but script is not showing any Linux bootable files. It normally shows kernel, grub & fstab.

---

### Post by dragonfly41 on 2017-12-06
Answering this question ...
> [COLOR=#000000]Also, if I am unable to boot into Ubuntu I really would just like to access the files I had on that partition. Is it possible to do this from windows?[/COLOR][COLOR=#000000]
There are these ..

[/COLOR][https://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](https://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/)

Also ...
[http://www.r-tt.com/free_linux_recovery/](http://www.r-tt.com/free_linux_recovery/)

[COLOR=#000000]

[/COLOR]

---

### Post by oldfred on 2017-12-06
Generally better to use Windows tools for Windows and Linux tools for Linux.

If Linux partition has issues Windows add in drivers will not work. Where Linux live installer should let you copy data, of if issues run repairs.

But always better to just reformat & restore from your backup.

---

