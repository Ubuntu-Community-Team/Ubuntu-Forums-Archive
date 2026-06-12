---
title: "Grub Issues"
date: 2017-07-31
forum: General Help
---

### Post by Alexd4 on 2017-07-31
I hope I'm not hijacking a thread, but..;

I have run boot-repair after having difficultly booting into Xubuntu which had been successfully installed on a former Windows 7 machine (no UEFI). 

I want to confirm that GRUB has been re-installed without rebooting for fear of bricking the machine. Below the the read out from boot-repair after running Reccomended Repair

```
 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 

xubuntu-vg-root: _______________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.2 LTS
    Boot files:        /etc/fstab

xubuntu-vg-swap_1: _____________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       999,423       997,376  83 Linux
/dev/sda2           1,001,470   234,440,703   233,439,234   5 Extended
/dev/sda5           1,001,472   234,440,703   233,439,232  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 299713d0-3e64-4d75-a8ff-fb96ff0dd2f6   swap       
/dev/mapper/sda5_crypt Kkf0MV-TlZf-0n6J-qX6C-bxdF-J0WK-pxvGpd LVM2_member 
/dev/mapper/xubuntu--vg-root 4b6d79fb-2c74-49e9-885d-494cdf42cc66   ext4       
/dev/mapper/xubuntu--vg-swap_1 dcaeec95-dc76-4cb4-b351-266effbca98f   swap       
/dev/sda1        65d62319-798d-45bb-98f3-df226737ae50   ext2       
/dev/sda5        0cb0e0bd-7395-46d4-8654-3b444a43d3a5   crypto_LUKS 

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jul 31 21:49 ata-SPCC_Solid_State_Disk_2FA60764120804224382 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 31 21:49 ata-SPCC_Solid_State_Disk_2FA60764120804224382-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul 31 21:49 ata-SPCC_Solid_State_Disk_2FA60764120804224382-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul 31 21:49 ata-SPCC_Solid_State_Disk_2FA60764120804224382-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Jul 31 21:13 ata-TSSTcorp_CDDVDW_TS-L633F_R8BR6GEB740985 -> ../../sr0
lrwxrwxrwx 1 root root 10 Jul 31 21:49 dm-name-cryptswap1 -> ../../dm-3
lrwxrwxrwx 1 root root 10 Jul 31 21:49 dm-name-sda5_crypt -> ../../dm-0
lrwxrwxrwx 1 root root 10 Jul 31 21:49 dm-name-xubuntu--vg-root -> ../../dm-1
lrwxrwxrwx 1 root root 10 Jul 31 21:49 dm-name-xubuntu--vg-swap_1 -> ../../dm-2
lrwxrwxrwx 1 root root 10 Jul 31 21:49 dm-uuid-CRYPT-LUKS1-0cb0e0bd739546d486543b444a43d3a5-sda5_crypt -> ../../dm-0
lrwxrwxrwx 1 root root 10 Jul 31 21:49 dm-uuid-CRYPT-PLAIN-cryptswap1 -> ../../dm-3
lrwxrwxrwx 1 root root 10 Jul 31 21:49 dm-uuid-LVM-fXey010LM56vkLXaOxJYFEeOJLMbx9Pd9cDcuLBCE2ZANGlhFwcrdu5RKe0ahVSN -> ../../dm-1
lrwxrwxrwx 1 root root 10 Jul 31 21:49 dm-uuid-LVM-fXey010LM56vkLXaOxJYFEeOJLMbx9Pda0IfGq0fFqHtOdGc6CBpjMAjdo2oZF5Z -> ../../dm-2
lrwxrwxrwx 1 root root 10 Jul 31 21:49 lvm-pv-uuid-Kkf0MV-TlZf-0n6J-qX6C-bxdF-J0WK-pxvGpd -> ../../dm-0

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1
sda5_crypt
xubuntu--vg-root
xubuntu--vg-swap_1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/xubuntu--vg-root /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda1        /boot                    ext2       (rw,relatime,block_validity,barrier,user_xattr,acl)


============================= sda1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
        

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.329430580 = 0.353723392    grub/grub.cfg                                  6
   0.391900063 = 0.420799488    grub/i386-pc/core.img                          2
   0.268082619 = 0.287851520    vmlinuz-4.4.0-57-generic                       8
   0.269547462 = 0.289424384    vmlinuz-4.4.0-67-generic                      10
   0.327886581 = 0.352065536    vmlinuz-4.4.0-72-generic                      11
   0.269059181 = 0.288900096    vmlinuz-4.4.0-77-generic                      11
   0.271988869 = 0.292045824    vmlinuz-4.4.0-78-generic                       9
   0.273453712 = 0.293618688    vmlinuz-4.4.0-83-generic                      10
   0.382585526 = 0.410798080    vmlinuz-4.4.0-87-generic                       9
   0.424562454 = 0.455870464    initrd.img-4.4.0-57-generic                   16
   0.416103363 = 0.446787584    initrd.img-4.4.0-67-generic                   17
   0.463624954 = 0.497813504    initrd.img-4.4.0-72-generic                   18
   0.460779190 = 0.494757888    initrd.img-4.4.0-77-generic                   15
   0.354249954 = 0.380372992    initrd.img-4.4.0-78-generic                   23
   0.475585938 = 0.510656512    initrd.img-4.4.0-83-generic                   22
   0.476561546 = 0.511704064    initrd.img-4.4.0-87-generic                   47

========================== xubuntu-vg-root/etc/fstab: ==========================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/xubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=65d62319-798d-45bb-98f3-df226737ae50 /boot           ext2    defaults        0       2
#/dev/mapper/xubuntu--vg-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

============== xubuntu-vg-root: Location of files loaded by Grub: ==============

           GiB - GB             File                                 Fragment(s)

   0.381608963 = 0.409749504    vmlinuz                                        9
   0.272477150 = 0.292570112    vmlinuz.old                                   10
   0.475584984 = 0.510655488    initrd.img                                    47
   0.474609375 = 0.509607936    initrd.img.old                                22

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda5

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  78 74 73 2d 70 6c 61 69  |........xts-plai|
00000030  6e 36 34 00 00 00 00 00  00 00 00 00 00 00 00 00  |n64.............|
00000040  00 00 00 00 00 00 00 00  73 68 61 32 35 36 00 00  |........sha256..|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 10 00 00 00 00 40  |...............@|
00000070  c3 b4 75 1f 66 e6 07 50  1c 3c d8 56 a8 37 2d 6c  |..u.f..P.<.V.7-l|
00000080  7c 59 55 b7 7d be f6 28  9f 3e e1 84 18 9c 3b e2  ||YU.}..(.>....;.|
00000090  31 5b 35 34 71 dd 99 52  75 32 08 5c 8b 9a d7 db  |1[54q..Ru2.\....|
000000a0  26 d8 7a aa 00 00 43 df  30 63 62 30 65 30 62 64  |&.z...C.0cb0e0bd|
000000b0  2d 37 33 39 35 2d 34 36  64 34 2d 38 36 35 34 2d  |-7395-46d4-8654-|
000000c0  33 62 34 34 34 61 34 33  64 33 61 35 00 00 00 00  |3b444a43d3a5....|
000000d0  00 ac 71 f3 00 01 0f bc  81 4e 3e 12 4a 24 34 ef  |..q......N>.J$4.|
000000e0  cd 58 3f c5 4f ed 32 3a  3a 76 f2 5c b6 b3 c1 9f  |.X?.O.2::v.\....|
000000f0  44 ef 14 f2 d3 f0 52 cc  00 00 00 08 00 00 0f a0  |D.....R.........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 02 00 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 03 f8 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 05 f0 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 07 e8 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 09 e0 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/10668/mounts) leaked on lvs invocation. Parent PID 17870: bash
File descriptor 63 (pipe:[244452]) leaked on lvs invocation. Parent PID 17870: bash
File descriptor 9 (/proc/10668/mounts) leaked on lvchange invocation. Parent PID 18763: bash
File descriptor 63 (pipe:[244452]) leaked on lvchange invocation. Parent PID 18763: bash
File descriptor 9 (/proc/10668/mounts) leaked on lvchange invocation. Parent PID 18763: bash
File descriptor 63 (pipe:[244452]) leaked on lvchange invocation. Parent PID 18763: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 2017-07-31__21h49 ===================
boot-repair version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa40
BLKID BEFORE LVM ACTIVATION:
/dev/mapper/sda5_crypt: UUID="Kkf0MV-TlZf-0n6J-qX6C-bxdF-J0WK-pxvGpd" TYPE="LVM2_member"
/dev/mapper/xubuntu--vg-root: UUID="4b6d79fb-2c74-49e9-885d-494cdf42cc66" TYPE="ext4"
/dev/sda1: UUID="65d62319-798d-45bb-98f3-df226737ae50" TYPE="ext2" PARTUUID="8a2d19fc-01"
/dev/sda5: UUID="0cb0e0bd-7395-46d4-8654-3b444a43d3a5" TYPE="crypto_LUKS" PARTUUID="8a2d19fc-05"
/dev/mapper/xubuntu--vg-swap_1: UUID="dcaeec95-dc76-4cb4-b351-266effbca98f" TYPE="swap"
/dev/dm-3: UUID="299713d0-3e64-4d75-a8ff-fb96ff0dd2f6" TYPE="swap"
MODPROBE
VGSCAN
File descriptor 9 (/proc/10668/mounts) leaked on vgscan invocation. Parent PID 10681: /bin/bash
Reading all physical volumes.  This may take a while...
Found volume group "xubuntu-vg" using metadata type lvm2
VGCHANGE
File descriptor 9 (/proc/10668/mounts) leaked on vgchange invocation. Parent PID 10681: /bin/bash
2 logical volume(s) in volume group "xubuntu-vg" now active
File descriptor 9 (/proc/10668/mounts) leaked on lvscan invocation. Parent PID 10681: /bin/bash
LVSCAN:
ACTIVE            '/dev/xubuntu-vg/root' [107.31 GiB] inherit
ACTIVE            '/dev/xubuntu-vg/swap_1' [3.98 GiB] inherit
Successfully activated LVM.
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Y a-t-il un RAID sur cet ordinateur ? no
File descriptor 9 (/proc/10668/mounts) leaked on lvs invocation. Parent PID 12495: /bin/sh
Error: /dev/mapper/sda5_crypt: unrecognised disk label
Error: /dev/mapper/sda5_crypt: unrecognised disk label
boot-repair is executed in installed-session (Ubuntu 16.04.2 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/vmlinuz-4.4.0-83-generic root=/dev/mapper/xubuntu--vg-root ro quiet splash vt.handoff=7
Set sda as corresponding disk of mapper/xubuntu--vg-root
Set sda as corresponding disk of mapper/xubuntu--vg-root
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/sda5 : Error code 32

=================== os-prober:
/dev/mapper/xubuntu--vg-root:L'OS actuellement utilisé - Ubuntu 16.04.2 LTS CurrentSession:linux

=================== blkid:
/dev/mapper/sda5_crypt: UUID="Kkf0MV-TlZf-0n6J-qX6C-bxdF-J0WK-pxvGpd" TYPE="LVM2_member"
/dev/mapper/xubuntu--vg-root: UUID="4b6d79fb-2c74-49e9-885d-494cdf42cc66" TYPE="ext4"
/dev/sda1: UUID="65d62319-798d-45bb-98f3-df226737ae50" TYPE="ext2" PARTUUID="8a2d19fc-01"
/dev/sda5: UUID="0cb0e0bd-7395-46d4-8654-3b444a43d3a5" TYPE="crypto_LUKS" PARTUUID="8a2d19fc-05"
/dev/mapper/xubuntu--vg-swap_1: UUID="dcaeec95-dc76-4cb4-b351-266effbca98f" TYPE="swap"
/dev/mapper/cryptswap1: UUID="299713d0-3e64-4d75-a8ff-fb96ff0dd2f6" TYPE="swap"

Set sda as corresponding disk of mapper/xubuntu--vg-root

1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

mount: unknown filesystem type 'crypto_LUKS'
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/sda5 : Error code 32

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Jul 31 21:42 grub.d
total 80
-rwxr-xr-x 1 root root  9791 Jun 17  2016 00_header
-rwxr-xr-x 1 root root  6258 Mar 15  2016 05_debian_theme
-rwxr-xr-x 1 root root 12512 Mar  1 21:01 10_linux
-rwxr-xr-x 1 root root 11082 Jun 17  2016 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 11692 Jun 17  2016 30_os-prober
-rwxr-xr-x 1 root root  1418 Jun 17  2016 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jun 17  2016 40_custom
-rwxr-xr-x 1 root root   216 Jun 17  2016 41_custom
-rw-r--r-- 1 root root   483 Jun 17  2016 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



/boot detected in the fstab of mapper/xubuntu--vg-root: UUID=65d62319-798d-45bb-98f3-df226737ae50  (sda1)

=================== UEFI/Legacy mode:
This installed-session is not in EFI-mode.
SecureBoot disabled.


=================== PARTITIONS & DISKS:
mapper/xubuntu--vg-root    : sda,    not-sepboot,    grubenv-ok    grub2,    signed grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-has-goodBOOT,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    .
sda1    : sda,    is-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /boot.
sda5    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA SPCC Solid State (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size   Type      File system  Flags
1      1049kB  512MB  511MB  primary   ext2         boot
2      513MB   120GB  120GB  extended
5      513MB   120GB  120GB  logical


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 4269MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:

Number  Start  End     Size    File system     Flags
1      0.00B  4269MB  4269MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/xubuntu--vg-swap_1: 4270MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:

Number  Start  End     Size    File system     Flags
1      0.00B  4270MB  4270MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/xubuntu--vg-root: 115GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:

Number  Start  End    Size   File system  Flags
1      0.00B  115GB  115GB  ext4


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/sda5_crypt: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

=================== parted -lm:

BYT;
/dev/sda:120GB:scsi:512:512:msdos:ATA SPCC Solid State:;
1:1049kB:512MB:511MB:ext2::boot;
2:513MB:120GB:120GB:::;
5:513MB:120GB:120GB:::;

BYT;
/dev/mapper/cryptswap1:4269MB:dm:512:512:loop:Linux device-mapper (crypt):;
1:0.00B:4269MB:4269MB:linux-swap(v1)::;

BYT;
/dev/mapper/xubuntu--vg-swap_1:4270MB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:4270MB:4270MB:linux-swap(v1)::;

BYT;
/dev/mapper/xubuntu--vg-root:115GB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:115GB:115GB:ext4::;

BYT;
/dev/mapper/sda5_crypt:120GB:dm:512:512:unknown:Linux device-mapper (crypt):;

=================== lsblk:
KNAME TYPE  FSTYPE        SIZE LABEL
sda   disk              111.8G
sda1  part  ext2          487M
sda2  part                  1K
sda5  part  crypto_LUKS 111.3G
dm-0  crypt LVM2_member 111.3G
dm-1  lvm   ext4        107.3G
dm-2  lvm   swap            4G
dm-3  crypt swap            4G
sr0   rom                1024M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      0  0  0 running
sda1     0  0  0         /boot
sda2     0  0  0
sda5     0  0  0
dm-0     0  0  0 running
dm-1     0  0  0 running /
dm-2     0  0  0 running
dm-3     0  0  0 running [SWAP]
sr0      1  0  1 running


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1991484k,nr_inodes=497871,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=402612k,mode=755)
/dev/mapper/xubuntu--vg-root on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=31,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda1 on /boot type ext2 (rw,relatime,block_validity,barrier,user_xattr,acl)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=402612k,mode=700,uid=1000,gid=1000)
/home/.ecryptfs/kevin/.Private on /home/kevin type ecryptfs (rw,nosuid,nodev,relatime,ecryptfs_fnek_sig=5907a76fff7d7748,ecryptfs_sig=e5198ad4322647ab,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)


=================== ls:
/sys/block/dm-0 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-1 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-2 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-3 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dm-0 dm-1 dm-2 dm-3 dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kfd kmsg kvm lightnvm log mapper mcelog media0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout toshiba_acpi uhid uinput urandom usb userio v4l vfio vga_arbiter vhci vhost-net video0 xubuntu-vg zero
ls /dev/mapper:  control cryptswap1 sda5_crypt xubuntu--vg-root xubuntu--vg-swap_1
ls: impossible d'accéder à '': Aucun fichier ou dossier de ce type

=================== df -Th:

Filesystem                   Type      Size  Used Avail Use% Mounted on
udev                         devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs                        tmpfs     394M  6.3M  387M   2% /run
/dev/mapper/xubuntu--vg-root ext4      106G   95G  6.0G  95% /
tmpfs                        tmpfs     2.0G  208K  2.0G   1% /dev/shm
tmpfs                        tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/sda1                    ext2      472M  366M   82M  82% /boot
tmpfs                        tmpfs     394M   44K  394M   1% /run/user/1000
/home/kevin/.Private         ecryptfs  106G   95G  6.0G  95% /home/kevin

=================== fdisk -l:
Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x8a2d19fc

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048    999423    997376   487M 83 Linux
/dev/sda2       1001470 234440703 233439234 111.3G  5 Extended
/dev/sda5       1001472 234440703 233439232 111.3G 83 Linux




Disk /dev/mapper/sda5_crypt: 111.3 GiB, 119518789632 bytes, 233435136 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/xubuntu--vg-root: 107.3 GiB, 115225919488 bytes, 225050624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/xubuntu--vg-swap_1: 4 GiB, 4269801472 bytes, 8339456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/cryptswap1: 4 GiB, 4269277184 bytes, 8338432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to enable-lvm) and reinstall the grub2 of mapper/xubuntu--vg-root into the MBR of sda, using the following options:        sda1/boot,
Additional repair would be performed: unhide-bootmenu-10s


=================== Advice in case of suggested repair
Vous souhaiterez peut-être ré-essayer après avoir déchiffré vos partitions. (http://doc.ubuntu-fr.org/ecryptfs)
Voulez-vous continuer ?


=================== User settings
The settings chosen by the user will not act on the boot.





```

I am very grateful for any advice. 

Was it successful?

---

### Post by wildmanne39 on 2017-07-31
*Thread moved to **General Help**.*

---

### Post by oldfred on 2017-07-31
You have an LVM partitioned drive with full drive encryption.
For Boot-Repair to correctly reinstall grub you must un-encrypt / (root) so Boot-Repair/grub installer can see /.  If that was done then it should be correct.

But if a new user, you may not want the added complications of LVM. But if you need full drive encryption then you get LVM. Somewhat like jumping into the deep end of the pool to learn to swim. You need to learn about LVM.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)
[https://linuxconfig.org/linux-lvm-logical-volume-manager](https://linuxconfig.org/linux-lvm-logical-volume-manager)
[https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](https://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))

---

### Post by Alexd4 on 2017-08-01
Hi Old Fred, 

Thanks for your response. I am certainly happy to learn more about LVM--the accessibility of good encryption in Linux distros is a major "selling" point in our modern world. 

The drive was decrypted at the time I ran boot-repair (i.e. it was not ran using a live CD/USB)

---

