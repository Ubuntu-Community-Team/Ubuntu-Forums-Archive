---
title: "Hard drive skipped from boot loading"
date: 2012-12-18
forum: General Help
---

### Post by YasinG on 2012-12-18
Good evening. I just installed Ubuntu 12.04 using a USB, but right after the install, after restarting the machine, I get a message asking me to insert a bootable drive. My boot settings in Bios have the hard drive first, then DVD, then USB stick, and I have two systems installed, Windows 7 and Ubuntu 12.04. I suspected the hard drive got somehow disconnected internally, so I checked but everything was in place. I used the live USB to start Ubuntu, and I could see the hard drive and mount whatever partition I wanted. The one that contains the recently installed Ubuntu, looks the same. (It hasn't been deleted or anything).
I'm not sure if this is a hardware problem or a loader(grub) problem, because the hard drive is visible. Only it isn't seen by the BIOS. My only means of internet connection is a USB modem, which doesn't work when I'm using the live USB, so I have can't download anything from the internet, in case someone asks. I also reinstalled Ubuntu 12.04, to no avail.
This is my second problem with this laptop, and Ubuntu, and it's not even a week old (the first issued [here]("http://ubuntuforums.org/showthread.php?p=12407900#post12407900")). I hope this one gets solved.
Thank you.

---

### Post by Bashing-om on 2012-12-18
YasinG; Hi !

Right off hand I would think that you did not install grub to the hard drive.
See these links for instructions:
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) (more than you might want to know about grub).
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by oldfred on 2012-12-19
Is this a new system with UEFI?
What brand, model computer?
Generally if BIOS does not see drive, then nothing sees it. So it you can see it from flash drive BIOS must see it.

May be best to see all the details.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemic](https://help.ubuntu.com/community/UbuntuSecureRemic)

---

### Post by YasinG on 2012-12-19
Yes it does have EFI, I can see it is enabled in BIOS. The laptop is a Lenovo G580, Core i5 with a Nvidia graphics card, if that was relevant. I have another OS installed, windows Seven.
Yes, the BIOS definitely sees it, because I can see the type of my HD in the BIOS setup.
I'm downloading the Ubuntu-Secure-Remix right now, to try to get the Boot-info. I can't direclty download Bot-repair on the Lenovo machine because I only have a USB modem and it doesn't work on the live USB, for some reason.
I'll post the result when done.

---

### Post by oldfred on 2012-12-19
New systems with Windows 8 are always UEFI. But the systems with Windows 7 are usually BIOS, but a few just before Windows 8 came out were also UEFI but without secure boot.
Perhaps you are BIOS boot but changed to UEFI boot? If in UEFI mode and it does not see the efi partition it should use BIOS to boot. 
But a lot of the newer systems only boot based on settings and do not auto use BIOS if UEFI not found. So then if no efi partition in UEFI mode it would not boot?

If you see gpt and an efi partition you are UEFI. If msdos (MBR) with extended and logical partitions then you are BIOS.

       sudo parted /dev/sda unit s print

---

### Post by YasinG on 2012-12-19
I guess I'm not UEFI then.
This is the output when I used 'sudo parted /dev/sda unit s print':
```
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA HITACHI HTS54505 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start       End         Size        Type      File system     Flags
 1      63s         104872319s  104872257s  primary   ntfs
 2      104873982s  976768064s  871894083s  extended                  lba
 8      104873984s  379875327s  275001344s  logical   ext4
 7      379877376s  395503615s  15626240s   logical   linux-swap(v1)
 5      395504298s  686136149s  290631852s  logical   ntfs
 6      686136213s  976768064s  290631852s  logical   ntfs

```

---

### Post by YasinG on 2012-12-19
Here are the steps I have taken so far:

[LIST]
[*]I downloaded the Ubuntu secure remix iso.
[*]I made a live USB for it using Unetbootin.
[*]I used it to open Ubuntu on the defected machine, and ran boot-repair
[*]This is the result of boot-info:
[/LIST]
```
    Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info November 20th 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /wubildr

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /wubildr

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.........<....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:  Syslinux looks at sector 8919728 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   104,872,319   104,872,257   7 NTFS / exFAT / HPFS
/dev/sda2         379,877,374   976,768,064   596,890,691   f W95 Extended (LBA)
/dev/sda5         395,504,298   686,136,149   290,631,852   7 NTFS / exFAT / HPFS
/dev/sda6         686,136,213   976,768,064   290,631,852   7 NTFS / exFAT / HPFS
/dev/sda7         379,877,376   395,503,615    15,626,240  82 Linux swap / Solaris
/dev/sda3         104,873,984   379,875,327   275,001,344  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7747 MB, 7747397632 bytes
32 heads, 63 sectors/track, 7505 cylinders, total 15131636 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    15,130,079    15,130,017   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        8C3EDF533EDF34C4                       ntfs       
/dev/sda3        82028942-66d9-43b9-bd76-7e869006a89a   ext4       
/dev/sda5        01CDCEA8E37C1580                       ntfs       
/dev/sda6        01CDCEA8E414AC00                       ntfs       
/dev/sda7        5b6571a8-179a-443a-b926-da8573082478   swap       
/dev/sdb1        5CC0-CEAA                              vfat       MOYOYA

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 82028942-66d9-43b9-bd76-7e869006a89a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 82028942-66d9-43b9-bd76-7e869006a89a
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 82028942-66d9-43b9-bd76-7e869006a89a
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=82028942-66d9-43b9-bd76-7e869006a89a ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 82028942-66d9-43b9-bd76-7e869006a89a
    echo    'Loading Linux 3.2.0-29-generic ...'
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=82028942-66d9-43b9-bd76-7e869006a89a ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 82028942-66d9-43b9-bd76-7e869006a89a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 82028942-66d9-43b9-bd76-7e869006a89a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 8C3EDF533EDF34C4
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=82028942-66d9-43b9-bd76-7e869006a89a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=5b6571a8-179a-443a-b926-da8573082478 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 164.195690155 = 176.303779840  boot/grub/grub.cfg                             1
  50.645572662 = 54.380269568   boot/initrd.img-3.2.0-29-generic               2
  86.141334534 = 92.493553664   boot/vmlinuz-3.2.0-29-generic                  1
  50.645572662 = 54.380269568   initrd.img                                     2
  86.141334534 = 92.493553664   vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz.efi.signed
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz.efi.signed
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz.efi.signed
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --

label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz.efi.signed
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda5

00000000  eb 5b 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.[.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  ab b0 52 11 00 00 00 00  |..........R.....|
00000030  04 00 00 00 00 00 00 00  0a 2b 15 01 00 00 00 00  |.........+......|
00000040  f6 00 00 00 01 00 00 00  80 15 7c e3 a8 ce cd 01  |..........|.....|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 e8 16  |.3.....|........|
00000060  00 b8 00 0d 8e c0 33 db  c6 06 0e 00 10 e8 53 00  |......3.......S.|
00000070  68 00 0d 68 6a 02 cb 8a  16 24 00 b4 08 cd 13 73  |h..hj....$.....s|
00000080  05 b9 ff ff 8a f1 66 0f  b6 c6 40 66 0f b6 d1 80  |......f...@f....|
00000090  e2 3f f7 e2 86 cd c0 ed  06 41 66 0f b7 c9 66 f7  |.?.......Af...f.|
000000a0  e1 66 a3 20 00 c3 b4 41  bb aa 55 8a 16 24 00 cd  |.f. ...A..U..$..|
000000b0  13 72 0f 81 fb 55 aa 75  09 f6 c1 01 74 04 fe 06  |.r...U.u....t...|
000000c0  14 00 c3 66 60 1e 06 66  a1 10 00 66 03 06 1c 00  |...f`..f...f....|
000000d0  66 3b 06 20 00 0f 82 3a  00 1e 66 6a 00 66 50 06  |f;. ...:..fj.fP.|
000000e0  53 66 68 10 00 01 00 80  3e 14 00 00 0f 85 0c 00  |Sfh.....>.......|
000000f0  e8 b3 ff 80 3e 14 00 00  0f 84 61 00 b4 42 8a 16  |....>.....a..B..|
00000100  24 00 16 1f 8b f4 cd 13  66 58 5b 07 66 58 66 58  |$.......fX[.fXfX|
00000110  1f eb 2d 66 33 d2 66 0f  b7 0e 18 00 66 f7 f1 fe  |..-f3.f.....f...|
00000120  c2 8a ca 66 8b d0 66 c1  ea 10 f7 36 1a 00 86 d6  |...f..f....6....|
00000130  8a 16 24 00 8a e8 c0 e4  06 0a cc b8 01 02 cd 13  |..$.............|
00000140  0f 82 19 00 8c c0 05 20  00 8e c0 66 ff 06 10 00  |....... ...f....|
00000150  ff 0e 0e 00 0f 85 6f ff  07 1f 66 61 c3 a0 f8 01  |......o...fa....|
00000160  e8 09 00 a0 fb 01 e8 03  00 fb eb fe b4 01 8b f0  |................|
00000170  ac 3c 00 74 09 b4 0e bb  07 00 cd 10 eb f2 c3 0d  |.<.t............|
00000180  0a 41 20 64 69 73 6b 20  72 65 61 64 20 65 72 72  |.A disk read err|
00000190  6f 72 20 6f 63 63 75 72  72 65 64 00 0d 0a 4e 54  |or occurred...NT|
000001a0  4c 44 52 20 69 73 20 6d  69 73 73 69 6e 67 00 0d  |LDR is missing..|
000001b0  0a 4e 54 4c 44 52 20 69  73 20 63 6f 6d 70 72 65  |.NTLDR is compre|
000001c0  73 73 65 64 00 0d 0a 50  72 65 73 73 20 43 74 72  |ssed...Press Ctr|
000001d0  6c 2b 41 6c 74 2b 44 65  6c 20 74 6f 20 72 65 73  |l+Alt+Del to res|
000001e0  74 61 72 74 0d 0a 00 00  00 00 00 00 00 00 00 00  |tart............|
000001f0  00 00 00 00 83 a0 b3 c9  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda6

00000000  eb 5b 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.[.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  ab b0 52 11 00 00 00 00  |..........R.....|
00000030  04 00 00 00 00 00 00 00  0a 2b 15 01 00 00 00 00  |.........+......|
00000040  f6 00 00 00 01 00 00 00  00 ac 14 e4 a8 ce cd 01  |................|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 e8 16  |.3.....|........|
00000060  00 b8 00 0d 8e c0 33 db  c6 06 0e 00 10 e8 53 00  |......3.......S.|
00000070  68 00 0d 68 6a 02 cb 8a  16 24 00 b4 08 cd 13 73  |h..hj....$.....s|
00000080  05 b9 ff ff 8a f1 66 0f  b6 c6 40 66 0f b6 d1 80  |......f...@f....|
00000090  e2 3f f7 e2 86 cd c0 ed  06 41 66 0f b7 c9 66 f7  |.?.......Af...f.|
000000a0  e1 66 a3 20 00 c3 b4 41  bb aa 55 8a 16 24 00 cd  |.f. ...A..U..$..|
000000b0  13 72 0f 81 fb 55 aa 75  09 f6 c1 01 74 04 fe 06  |.r...U.u....t...|
000000c0  14 00 c3 66 60 1e 06 66  a1 10 00 66 03 06 1c 00  |...f`..f...f....|
000000d0  66 3b 06 20 00 0f 82 3a  00 1e 66 6a 00 66 50 06  |f;. ...:..fj.fP.|
000000e0  53 66 68 10 00 01 00 80  3e 14 00 00 0f 85 0c 00  |Sfh.....>.......|
000000f0  e8 b3 ff 80 3e 14 00 00  0f 84 61 00 b4 42 8a 16  |....>.....a..B..|
00000100  24 00 16 1f 8b f4 cd 13  66 58 5b 07 66 58 66 58  |$.......fX[.fXfX|
00000110  1f eb 2d 66 33 d2 66 0f  b7 0e 18 00 66 f7 f1 fe  |..-f3.f.....f...|
00000120  c2 8a ca 66 8b d0 66 c1  ea 10 f7 36 1a 00 86 d6  |...f..f....6....|
00000130  8a 16 24 00 8a e8 c0 e4  06 0a cc b8 01 02 cd 13  |..$.............|
00000140  0f 82 19 00 8c c0 05 20  00 8e c0 66 ff 06 10 00  |....... ...f....|
00000150  ff 0e 0e 00 0f 85 6f ff  07 1f 66 61 c3 a0 f8 01  |......o...fa....|
00000160  e8 09 00 a0 fb 01 e8 03  00 fb eb fe b4 01 8b f0  |................|
00000170  ac 3c 00 74 09 b4 0e bb  07 00 cd 10 eb f2 c3 0d  |.<.t............|
00000180  0a 41 20 64 69 73 6b 20  72 65 61 64 20 65 72 72  |.A disk read err|
00000190  6f 72 20 6f 63 63 75 72  72 65 64 00 0d 0a 4e 54  |or occurred...NT|
000001a0  4c 44 52 20 69 73 20 6d  69 73 73 69 6e 67 00 0d  |LDR is missing..|
000001b0  0a 4e 54 4c 44 52 20 69  73 20 63 6f 6d 70 72 65  |.NTLDR is compre|
000001c0  73 73 65 64 00 0d 0a 50  72 65 73 73 20 43 74 72  |ssed...Press Ctr|
000001d0  6c 2b 41 6c 74 2b 44 65  6c 20 74 6f 20 72 65 73  |l+Alt+Del to res|
000001e0  74 61 72 74 0d 0a 00 00  00 00 00 00 00 00 00 00  |tart............|
000001f0  00 00 00 00 83 a0 b3 c9  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

File descriptor 8 (/proc/3666/mounts) leaked on lvscan invocation. Parent PID 10846: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-12-20__02h28 ===================
boot-repair version : 3.195~ppa26~quantal
boot-sav version : 3.195~ppa26~quantal
glade2script version : 3.2.2~ppa45~quantal
boot-sav-extra version : 3.195~ppa26~quantal
boot-repair is executed in live-session (Ubuntu-Secure-Remix 12.10 30nov2012, quantal, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi.signed file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda3:Ubuntu 12.04.1 LTS (12.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="8C3EDF533EDF34C4" TYPE="ntfs"
/dev/sda3: UUID="82028942-66d9-43b9-bd76-7e869006a89a" TYPE="ext4"
/dev/sda5: UUID="01CDCEA8E37C1580" TYPE="ntfs"
/dev/sda6: UUID="01CDCEA8E414AC00" TYPE="ntfs"
/dev/sda7: UUID="5b6571a8-179a-443a-b926-da8573082478" TYPE="swap"
/dev/sdb1: LABEL="MOYOYA" UUID="5CC0-CEAA" TYPE="vfat"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== sda3/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
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




=================== sda3/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Aug 23 16:56 grub.d
total 56
-rwxr-xr-x 1 root root 6715 May 17  2012 00_header
-rwxr-xr-x 1 root root 5522 May 17  2012 05_debian_theme
-rwxr-xr-x 1 root root 7407 May 17  2012 10_linux
-rwxr-xr-x 1 root root 6335 May 17  2012 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 May 17  2012 30_os-prober
-rwxr-xr-x 1 root root  214 May 17  2012 40_custom
-rwxr-xr-x 1 root root   95 May 17  2012 41_custom
-rw-r--r-- 1 root root  483 May 17  2012 README


=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. Please report this message to yannubuntu@gmail.com


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda3    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-efi grub-pc,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.
sda6    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda6.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA HITACHI HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  53.7GB  53.7GB  primary   ntfs
3      53.7GB  194GB   141GB   primary   ext4
2      194GB   500GB   306GB   extended                  lba
7      194GB   202GB   8001MB  logical   linux-swap(v1)
5      202GB   351GB   149GB   logical   ntfs
6      351GB   500GB   149GB   logical   ntfs


Model: Kingston DataTraveler G3 (scsi)
Disk /dev/sdb: 7747MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  7747MB  7747MB  primary  fat32        boot

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:msdos:ATA HITACHI HTS54505;
1:32.3kB:53.7GB:53.7GB:ntfs::;
3:53.7GB:194GB:141GB:ext4::;
2:194GB:500GB:306GB:::lba;
7:194GB:202GB:8001MB:linux-swap(v1)::;
5:202GB:351GB:149GB:ntfs::;
6:351GB:500GB:149GB:ntfs::;

BYT;
/dev/sdb:7747MB:scsi:512:512:msdos:Kingston DataTraveler G3;
1:32.3kB:7747MB:7747MB:fat32::boot;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/ubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type ext4 (rw)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 rts51x0 sda sda1 sda2 sda3 sda5 sda6 sda7 sdb sdb1 sdc sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uinput urandom v4l vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.9G   26M  3.9G   1% /
udev           devtmpfs   3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs      1.6G  848K  1.6G   1% /run
/dev/sdb1      vfat       7.3G  4.3G  3.0G  59% /cdrom
/dev/loop0     squashfs   717M  717M     0 100% /rofs
tmpfs          tmpfs      3.9G   12K  3.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      3.9G   76K  3.9G   1% /run/shm
none           tmpfs      100M   36K  100M   1% /run/user
/dev/sda1      fuseblk     51G   30G   21G  59% /mnt/boot-sav/sda1
/dev/sda3      ext4       130G  2.3G  121G   2% /mnt/boot-sav/sda3
/dev/sda5      fuseblk    139G   31M  139G   1% /mnt/boot-sav/sda5
/dev/sda6      fuseblk    139G   31M  139G   1% /mnt/boot-sav/sda6

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc3ffc3ff

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   104872319    52436128+   7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/sda2       379877374   976768064   298445345+   f  W95 Ext'd (LBA)
Partition 2 does not start on physical sector boundary.
/dev/sda3       104873984   379875327   137500672   83  Linux
/dev/sda5       395504298   686136149   145315926    7  HPFS/NTFS/exFAT
Partition 5 does not start on physical sector boundary.
/dev/sda6       686136213   976768064   145315926    7  HPFS/NTFS/exFAT
Partition 6 does not start on physical sector boundary.
/dev/sda7       379877376   395503615     7813120   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 7747 MB, 7747397632 bytes
32 heads, 63 sectors/track, 7505 cylinders, total 15131636 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1c660c35

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    15130079     7565008+   b  W95 FAT32


=================== Final advice in case of recommended repair


A broken Wubi has been detected. Please fix it this way:
https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu

=================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sda3 into the MBR of sda.
The boot flag would be placed on sda1.
Additional repair would be performed: unhide-bootmenu-10s repair-filesystems

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer. See you soon!
pastebin.com ko (), using paste.ubuntu Please report this message to yannubuntu@gmail.com
```

---

### Post by oldfred on 2012-12-19
Boot-Repair reports the issue for booting Windows. And you should do this even if you want to boot with grub. Windows only directly boots from partition with boot flag or only repairs the partition with boot flag. Is Active partition in Windows.
```
The boot flag would be placed on sda1.
```

You can use gparted from liveCD to add boot flag. But it looks like Boot-Repair will fix that.

> Recommended-Repair
This setting would reinstall the grub2 of sda3 into the MBR of sda.
The boot flag would be placed on sda1.
Additional repair would be performed: unhide-bootmenu-10s repair-filesystems


You also show both a wubi install inside Windows and a full install in sda3. Did you boot the full install. 
If working install you should install grub form sda3 into the MBR, so grub is booting. Which Boot-Repair will do for you.

---

### Post by YasinG on 2012-12-19
And this is the output when I choose to repair:
```
    Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info November 20th 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /wubildr

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /wubildr

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.........<....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:  Syslinux looks at sector 8919728 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   104,872,319   104,872,257   7 NTFS / exFAT / HPFS
/dev/sda2         379,877,374   976,768,064   596,890,691   f W95 Extended (LBA)
/dev/sda5         395,504,298   686,136,149   290,631,852   7 NTFS / exFAT / HPFS
/dev/sda6         686,136,213   976,768,064   290,631,852   7 NTFS / exFAT / HPFS
/dev/sda7         379,877,376   395,503,615    15,626,240  82 Linux swap / Solaris
/dev/sda3         104,873,984   379,875,327   275,001,344  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7747 MB, 7747397632 bytes
32 heads, 63 sectors/track, 7505 cylinders, total 15131636 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    15,130,079    15,130,017   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        8C3EDF533EDF34C4                       ntfs       
/dev/sda3        82028942-66d9-43b9-bd76-7e869006a89a   ext4       
/dev/sda5        01CDCEA8E37C1580                       ntfs       
/dev/sda6        01CDCEA8E414AC00                       ntfs       
/dev/sda7        5b6571a8-179a-443a-b926-da8573082478   swap       
/dev/sdb1        5CC0-CEAA                              vfat       MOYOYA

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 82028942-66d9-43b9-bd76-7e869006a89a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 82028942-66d9-43b9-bd76-7e869006a89a
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 82028942-66d9-43b9-bd76-7e869006a89a
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=82028942-66d9-43b9-bd76-7e869006a89a ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 82028942-66d9-43b9-bd76-7e869006a89a
    echo    'Loading Linux 3.2.0-29-generic ...'
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=82028942-66d9-43b9-bd76-7e869006a89a ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 82028942-66d9-43b9-bd76-7e869006a89a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root 82028942-66d9-43b9-bd76-7e869006a89a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 8C3EDF533EDF34C4
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=82028942-66d9-43b9-bd76-7e869006a89a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=5b6571a8-179a-443a-b926-da8573082478 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  86.141342163 = 92.493561856   boot/grub/grub.cfg                             1
  50.645572662 = 54.380269568   boot/initrd.img-3.2.0-29-generic               2
  86.141334534 = 92.493553664   boot/vmlinuz-3.2.0-29-generic                  1
  50.645572662 = 54.380269568   initrd.img                                     2
  86.141334534 = 92.493553664   vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz.efi.signed
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz.efi.signed
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz.efi.signed
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --

label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz.efi.signed
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda5

00000000  eb 5b 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.[.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  ab b0 52 11 00 00 00 00  |..........R.....|
00000030  04 00 00 00 00 00 00 00  0a 2b 15 01 00 00 00 00  |.........+......|
00000040  f6 00 00 00 01 00 00 00  80 15 7c e3 a8 ce cd 01  |..........|.....|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 e8 16  |.3.....|........|
00000060  00 b8 00 0d 8e c0 33 db  c6 06 0e 00 10 e8 53 00  |......3.......S.|
00000070  68 00 0d 68 6a 02 cb 8a  16 24 00 b4 08 cd 13 73  |h..hj....$.....s|
00000080  05 b9 ff ff 8a f1 66 0f  b6 c6 40 66 0f b6 d1 80  |......f...@f....|
00000090  e2 3f f7 e2 86 cd c0 ed  06 41 66 0f b7 c9 66 f7  |.?.......Af...f.|
000000a0  e1 66 a3 20 00 c3 b4 41  bb aa 55 8a 16 24 00 cd  |.f. ...A..U..$..|
000000b0  13 72 0f 81 fb 55 aa 75  09 f6 c1 01 74 04 fe 06  |.r...U.u....t...|
000000c0  14 00 c3 66 60 1e 06 66  a1 10 00 66 03 06 1c 00  |...f`..f...f....|
000000d0  66 3b 06 20 00 0f 82 3a  00 1e 66 6a 00 66 50 06  |f;. ...:..fj.fP.|
000000e0  53 66 68 10 00 01 00 80  3e 14 00 00 0f 85 0c 00  |Sfh.....>.......|
000000f0  e8 b3 ff 80 3e 14 00 00  0f 84 61 00 b4 42 8a 16  |....>.....a..B..|
00000100  24 00 16 1f 8b f4 cd 13  66 58 5b 07 66 58 66 58  |$.......fX[.fXfX|
00000110  1f eb 2d 66 33 d2 66 0f  b7 0e 18 00 66 f7 f1 fe  |..-f3.f.....f...|
00000120  c2 8a ca 66 8b d0 66 c1  ea 10 f7 36 1a 00 86 d6  |...f..f....6....|
00000130  8a 16 24 00 8a e8 c0 e4  06 0a cc b8 01 02 cd 13  |..$.............|
00000140  0f 82 19 00 8c c0 05 20  00 8e c0 66 ff 06 10 00  |....... ...f....|
00000150  ff 0e 0e 00 0f 85 6f ff  07 1f 66 61 c3 a0 f8 01  |......o...fa....|
00000160  e8 09 00 a0 fb 01 e8 03  00 fb eb fe b4 01 8b f0  |................|
00000170  ac 3c 00 74 09 b4 0e bb  07 00 cd 10 eb f2 c3 0d  |.<.t............|
00000180  0a 41 20 64 69 73 6b 20  72 65 61 64 20 65 72 72  |.A disk read err|
00000190  6f 72 20 6f 63 63 75 72  72 65 64 00 0d 0a 4e 54  |or occurred...NT|
000001a0  4c 44 52 20 69 73 20 6d  69 73 73 69 6e 67 00 0d  |LDR is missing..|
000001b0  0a 4e 54 4c 44 52 20 69  73 20 63 6f 6d 70 72 65  |.NTLDR is compre|
000001c0  73 73 65 64 00 0d 0a 50  72 65 73 73 20 43 74 72  |ssed...Press Ctr|
000001d0  6c 2b 41 6c 74 2b 44 65  6c 20 74 6f 20 72 65 73  |l+Alt+Del to res|
000001e0  74 61 72 74 0d 0a 00 00  00 00 00 00 00 00 00 00  |tart............|
000001f0  00 00 00 00 83 a0 b3 c9  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda6

00000000  eb 5b 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.[.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  ab b0 52 11 00 00 00 00  |..........R.....|
00000030  04 00 00 00 00 00 00 00  0a 2b 15 01 00 00 00 00  |.........+......|
00000040  f6 00 00 00 01 00 00 00  00 ac 14 e4 a8 ce cd 01  |................|
00000050  fa 33 c0 8e d0 bc 00 7c  fb b8 c0 07 8e d8 e8 16  |.3.....|........|
00000060  00 b8 00 0d 8e c0 33 db  c6 06 0e 00 10 e8 53 00  |......3.......S.|
00000070  68 00 0d 68 6a 02 cb 8a  16 24 00 b4 08 cd 13 73  |h..hj....$.....s|
00000080  05 b9 ff ff 8a f1 66 0f  b6 c6 40 66 0f b6 d1 80  |......f...@f....|
00000090  e2 3f f7 e2 86 cd c0 ed  06 41 66 0f b7 c9 66 f7  |.?.......Af...f.|
000000a0  e1 66 a3 20 00 c3 b4 41  bb aa 55 8a 16 24 00 cd  |.f. ...A..U..$..|
000000b0  13 72 0f 81 fb 55 aa 75  09 f6 c1 01 74 04 fe 06  |.r...U.u....t...|
000000c0  14 00 c3 66 60 1e 06 66  a1 10 00 66 03 06 1c 00  |...f`..f...f....|
000000d0  66 3b 06 20 00 0f 82 3a  00 1e 66 6a 00 66 50 06  |f;. ...:..fj.fP.|
000000e0  53 66 68 10 00 01 00 80  3e 14 00 00 0f 85 0c 00  |Sfh.....>.......|
000000f0  e8 b3 ff 80 3e 14 00 00  0f 84 61 00 b4 42 8a 16  |....>.....a..B..|
00000100  24 00 16 1f 8b f4 cd 13  66 58 5b 07 66 58 66 58  |$.......fX[.fXfX|
00000110  1f eb 2d 66 33 d2 66 0f  b7 0e 18 00 66 f7 f1 fe  |..-f3.f.....f...|
00000120  c2 8a ca 66 8b d0 66 c1  ea 10 f7 36 1a 00 86 d6  |...f..f....6....|
00000130  8a 16 24 00 8a e8 c0 e4  06 0a cc b8 01 02 cd 13  |..$.............|
00000140  0f 82 19 00 8c c0 05 20  00 8e c0 66 ff 06 10 00  |....... ...f....|
00000150  ff 0e 0e 00 0f 85 6f ff  07 1f 66 61 c3 a0 f8 01  |......o...fa....|
00000160  e8 09 00 a0 fb 01 e8 03  00 fb eb fe b4 01 8b f0  |................|
00000170  ac 3c 00 74 09 b4 0e bb  07 00 cd 10 eb f2 c3 0d  |.<.t............|
00000180  0a 41 20 64 69 73 6b 20  72 65 61 64 20 65 72 72  |.A disk read err|
00000190  6f 72 20 6f 63 63 75 72  72 65 64 00 0d 0a 4e 54  |or occurred...NT|
000001a0  4c 44 52 20 69 73 20 6d  69 73 73 69 6e 67 00 0d  |LDR is missing..|
000001b0  0a 4e 54 4c 44 52 20 69  73 20 63 6f 6d 70 72 65  |.NTLDR is compre|
000001c0  73 73 65 64 00 0d 0a 50  72 65 73 73 20 43 74 72  |ssed...Press Ctr|
000001d0  6c 2b 41 6c 74 2b 44 65  6c 20 74 6f 20 72 65 73  |l+Alt+Del to res|
000001e0  74 61 72 74 0d 0a 00 00  00 00 00 00 00 00 00 00  |tart............|
000001f0  00 00 00 00 83 a0 b3 c9  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

File descriptor 8 (/proc/11624/mounts) leaked on lvscan invocation. Parent PID 20476: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-12-20__02h36 ===================
boot-repair version : 3.195~ppa26~quantal
boot-sav version : 3.195~ppa26~quantal
glade2script version : 3.2.2~ppa45~quantal
boot-sav-extra version : 3.195~ppa26~quantal
boot-repair is executed in live-session (Ubuntu-Secure-Remix 12.10 30nov2012, quantal, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi.signed file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

=================== os-prober:
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda3:Ubuntu 12.04.1 LTS (12.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="8C3EDF533EDF34C4" TYPE="ntfs"
/dev/sda3: UUID="82028942-66d9-43b9-bd76-7e869006a89a" TYPE="ext4"
/dev/sda5: UUID="01CDCEA8E37C1580" TYPE="ntfs"
/dev/sda6: UUID="01CDCEA8E414AC00" TYPE="ntfs"
/dev/sda7: UUID="5b6571a8-179a-443a-b926-da8573082478" TYPE="swap"
/dev/sdb1: LABEL="MOYOYA" UUID="5CC0-CEAA" TYPE="vfat"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== sda3/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
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




=================== sda3/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Aug 23 16:56 grub.d
total 56
-rwxr-xr-x 1 root root 6715 May 17  2012 00_header
-rwxr-xr-x 1 root root 5522 May 17  2012 05_debian_theme
-rwxr-xr-x 1 root root 7407 May 17  2012 10_linux
-rwxr-xr-x 1 root root 6335 May 17  2012 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 May 17  2012 30_os-prober
-rwxr-xr-x 1 root root  214 May 17  2012 40_custom
-rwxr-xr-x 1 root root   95 May 17  2012 41_custom
-rw-r--r-- 1 root root  483 May 17  2012 README


=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. Please report this message to yannubuntu@gmail.com


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda3    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-efi grub-pc,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.
sda6    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda6.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA HITACHI HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  53.7GB  53.7GB  primary   ntfs
3      53.7GB  194GB   141GB   primary   ext4
2      194GB   500GB   306GB   extended                  lba
7      194GB   202GB   8001MB  logical   linux-swap(v1)
5      202GB   351GB   149GB   logical   ntfs
6      351GB   500GB   149GB   logical   ntfs


Model: Kingston DataTraveler G3 (scsi)
Disk /dev/sdb: 7747MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  7747MB  7747MB  primary  fat32        boot

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:msdos:ATA HITACHI HTS54505;
1:32.3kB:53.7GB:53.7GB:ntfs::;
3:53.7GB:194GB:141GB:ext4::;
2:194GB:500GB:306GB:::lba;
7:194GB:202GB:8001MB:linux-swap(v1)::;
5:202GB:351GB:149GB:ntfs::;
6:351GB:500GB:149GB:ntfs::;

BYT;
/dev/sdb:7747MB:scsi:512:512:msdos:Kingston DataTraveler G3;
1:32.3kB:7747MB:7747MB:fat32::boot;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/ubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
gvfsd-fuse on /root/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type ext4 (rw)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 rts51x0 sda sda1 sda2 sda3 sda5 sda6 sda7 sdb sdb1 sdc sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uinput urandom v4l vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.9G   28M  3.9G   1% /
udev           devtmpfs   3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs      1.6G  848K  1.6G   1% /run
/dev/sdb1      vfat       7.3G  4.3G  3.0G  59% /cdrom
/dev/loop0     squashfs   717M  717M     0 100% /rofs
tmpfs          tmpfs      3.9G  108K  3.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      3.9G   76K  3.9G   1% /run/shm
none           tmpfs      100M   44K  100M   1% /run/user
/dev/sda1      fuseblk     51G   30G   21G  59% /mnt/boot-sav/sda1
/dev/sda3      ext4       130G  2.3G  121G   2% /mnt/boot-sav/sda3
/dev/sda5      fuseblk    139G   31M  139G   1% /mnt/boot-sav/sda5
/dev/sda6      fuseblk    139G   31M  139G   1% /mnt/boot-sav/sda6

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc3ffc3ff

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   104872319    52436128+   7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/sda2       379877374   976768064   298445345+   f  W95 Ext'd (LBA)
Partition 2 does not start on physical sector boundary.
/dev/sda3       104873984   379875327   137500672   83  Linux
/dev/sda5       395504298   686136149   145315926    7  HPFS/NTFS/exFAT
Partition 5 does not start on physical sector boundary.
/dev/sda6       686136213   976768064   145315926    7  HPFS/NTFS/exFAT
Partition 6 does not start on physical sector boundary.
/dev/sda7       379877376   395503615     7813120   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 7747 MB, 7747397632 bytes
32 heads, 63 sectors/track, 7505 cylinders, total 15131636 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1c660c35

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    15130079     7565008+   b  W95 FAT32



=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sda3 into the MBR of sda.
The boot flag will be placed on sda1.
Additional repair will be performed: unhide-bootmenu-10s repair-filesystems


Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var

ntfsfix /dev/sda1
Refusing to operate on read-write mounted device /dev/sda1.

fsck -fyM /dev/sda3
fsck from util-linux 2.20.1

ntfsfix /dev/sda5
Refusing to operate on read-write mounted device /dev/sda5.

ntfsfix /dev/sda6
Refusing to operate on read-write mounted device /dev/sda6.
parted /dev/sda set 1 boot on

                                                                          
Information: You may need to update /etc/fstab.

grub-install (GRUB) 1.99-21ubuntu3.1,grub-install (GRUB) 1.

Reinstall the GRUB of sda3 into the MBR of sda
grub-install /dev/sda: Installation finished. No error reported.
exit code of grub-install /dev/sda:0

chroot /mnt/boot-sav/sda3 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Unhide GRUB boot menu in sda3/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.


A broken Wubi has been detected. Please fix it this way:
https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu
pastebin.com ko (), using paste.ubuntu Please report this message to yannubuntu@gmail.com
```

---

### Post by oldfred on 2012-12-19
It looks like Boot-Repair made all the fixes. Does system now boot?

But it tried to run ntfsfix which only makes minor fixes and sets chkdsk flag so Windows runs chkdsk, but it seemed to have issues mounting partitions, so it did not run. Not sure if Boot-Repair issue or partition issue.

But I would suggest running chkdsk from a Windows repair CD or from your Windows if it boots ok. You can only run chkdsk from Windows not from Linux.

---

### Post by YasinG on 2012-12-19
I was haste in posting the resluts of boot-repair, before checking if there was any effect after doing it. There was, and now I can see both OSs in the boot screen, and Windows loads nicely.
Ubuntu still has a problem which is kind of wierd. When I choose it it says:
"Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:
1. Insert your windows installation disc and restart.
2. Choose your language settings, and click next.
3. Click "repair your computer".
...
File: \Ubuntu\winboot\wubildr.mbr
Status: 0xc0000225"

How do I run chkdsk ?.

> **oldfred said:**
> 
You also show both a wubi install inside Windows and a full install in sda3. Did you boot the full install. 
I'm not sure what you mean, I booted  from the live USB.

---

### Post by oldfred on 2012-12-19
You run chkdsk from Windows. Either a Windows repairCD or the repair console in Windows. I think most Windows get you repairs when using f8 when booting. But when booting from grub they say it is really fast so you have to be quick.

---

### Post by YasinG on 2012-12-19
I ran chkdsk and it says it ran successfully. I also ran 'bootrec /fixmbr' and 'bootrec /fixboot', that I found on the gparted faq page. The aforementioned problem still presists though. I can't start my Ubuntu installation.

---

### Post by oldfred on 2012-12-19
When you ran fixMBR, you reinstalled the Windows boot loader to the MBR, so that is all that will boot.

After you ran Boot-Repair did grub load and were you able to boot? You need to have grub2 boot loader in the MBR to be able to boot Ubuntu.

---

### Post by YasinG on 2012-12-22
I'm sorry for being absent, I had two crushing exams. Yes, Grub loaded but I wasn't able to boot Ubuntu. Only Windows 7 loaded. Ubuntu shows me the message I described in my last post.

---

### Post by oldfred on 2012-12-22
Are you trying to boot wubi or the intall in sda3. 

The Windows boot loader will only give the option to boot wubi. You have to use Boot-Repair or manually install grub2's boot loader to the MBR to give the optio to boot the install in sda3.

---

### Post by YasinG on 2012-12-22
I don't know which one I'm trying to boot, there is only one choice. But I did use Boot-repair, so it should be booting the one in sda3. Also, I don't mind uninstalling either or both, if it should fix the problem. I don't have any data on either one.

---

### Post by oldfred on 2012-12-22
Then what error are you getting? A wubildr.mbr error is from wubi.

Do you get full grub menu first with Ubuntu on top, recovery, memory test or advanced options and Windows on the bottom.
Or do you get a two line entry from Windows with Windows & Ubuntu which is really wubi?
And does Windows boot ok?

---

### Post by YasinG on 2012-12-22
Yes, I get only two options, Ubuntu and Windows. Windows boots Ok. Also, when I launch the Os-Uninstaller, there are only the two systems I mentioned, Windows 7 on sda1 and Ubuntu on sda3. No mention of Wubi. I did install Ubuntu 12.10 with Wubi at first but I removed it before installing 12.04. Why is it till seeing Wubi ?!.

---

### Post by oldfred on 2012-12-22
It does not look like you unistalled wubi.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
            
Uninstall wubi:
[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)
bcdEdit - bcbc
[http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)


Boot-Repair will offer the option to restore Windows boot loader or install the grub2 boot loader. So rerun it and install grub2's boot loader.

---

### Post by YasinG on 2012-12-22
I did the following:
The folder c:/Ubuntu was already removed, so I only removed the Wubi files.
I used bcdedit from cmd to delete the Ubuntu option from the boot menu. Done successfully.
I then used Boot-repair to reinstall grub again (which it said 'reinstall grub' not 'grub2'). It kept telling me that there is a broken Wubi version on my machine, but I couldn't find it. Until I deleted some Wubildr files from all the other drives, which didn't have any systems on them.
Ubuntu still doesn't show up in the boot menu. I think the problem now is with my grub installation. How do I install it manually, without boot-repair, but also, without internet connection on that laptop ?.
The output from Boot-repair is very large so I attached it instead of posting here. It mentions that it installed Grub 1, not 2.

---

### Post by oldfred on 2012-12-22
Are text files from before running Boot-Repair. And normally Boot-Repair posts BootInfo report to pastebin and you just need to post the link.

It still shows Windows in MBR, but says it installed grub to the MBR. Grub 1.99 is grub2.

Does it boot to a grub menu and can you boot both Ubuntu and Windows?

---

### Post by YasinG on 2012-12-22
> **oldfred said:**
> Are text files from before running Boot-Repair.
I'm sorry, I don't understand what you meant here.
I know it should give me a url directly, but since I don't have a internet connection, it can't post it to pastebin.
No, it doesn't load a boot menu, it automatically loads windows as if it was the only system installed. I can't access the Ubuntu installation at any point.

---

### Post by oldfred on 2012-12-22
So this computer does not have a Ethernet connection?

You usually need the connection to get things to update correctly.

---

### Post by YasinG on 2012-12-23
The wireless device works, but I have no internet connection other than a USB modem, which doesn't work when I'm booted through the live USB.

---

### Post by oldfred on 2012-12-23
I though Boot-Repair would install grub to the MBR even without Internet. But it still is better to have a hard wired Internet connection when Installing or repairing. It often needs to download extra drivers that are not on the install ISO.

Do you have any settings in BIOS that lock MBR or are virus check from BIOS that prevent writing to MBR? IF so make sure those are off.

From liveCD run this which really only does what Boot-Repair runs.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda3 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda3 if not correct:
sudo fdisk -l
#confirm that linux is sda3
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub



       How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by YasinG on 2012-12-23
I forgot to check for the MBR settings before doing the steps for GRUB installation, but I checked afterwards and there is no information regarding the MBR in BIOS.
Anyway, the above instructions worked perfectly, with no errors, and now I have four options for Ubuntu and one for Windows 7, and all works as expected (I had to log in recovery mode, because I forgot the password I set).
I will flag this article SOLVED now, but I had one question I wanted to ask you. The USB modem still doesn't work on this installation, even though it worked perfectly on other Ubuntu versions on this and other laptops without requiring any package installations ?(The versions I mean were 12.10 and 11.04).
A monumental thank you for you. I wish I had anything to offer in return for your help.

---

### Post by oldfred on 2012-12-23
Glad you got it working. 

I do not know much about USB modems. My wifi on the laptop just works and I have not followed details on those issues. 
Best to start new thread with that issue in the title so those who know more may offer to help.

---

### Post by YasinG on 2012-12-23
Ok, thank you.

---

