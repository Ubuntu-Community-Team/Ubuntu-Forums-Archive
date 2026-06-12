---
title: "grub2 stopped detecting ubuntu"
date: 2015-10-07
forum: General Help
---

### Post by sdlinux on 2015-10-07
Hi,

Recently I restarted my PC and now I don't have the ubuntu option anymore. Just Memtest and windows. Only thing I can think of is that I had downloaded some updates and not installed them? Below is the results.txt from bootinfo script. I ran it from a usb live hdd.

I also tried boot repair app and it hung for like 30 minutes before I gave up. Any help?

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Windows is installed in the MBR of /dev/sdb.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdc and looks on the 
    same drive in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/mapper/pdc_ceddccceea 
    and looks on the same drive in partition #6 for /boot/grub/stage2 and 
    /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 276483. But according to the info from 
                       fdisk, sdc5 starts at sector 105338883.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:  Syslinux looks at sector 2024240 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

pdc_ceddccceea2: _______________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

pdc_ceddccceea5: _______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    91,496,447    91,494,400  83 Linux
/dev/sda2          91,498,494   125,044,735    33,546,242   5 Extended
/dev/sda5          91,498,496   125,044,735    33,546,240  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848   488,392,703   488,185,856   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
38 heads, 36 sectors/track, 913935 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc2         105,336,832 1,250,260,991 1,144,924,160   f W95 Extended (LBA)
/dev/sdc5         105,338,883 1,250,260,991 1,144,922,109   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 4013 MB, 4013948928 bytes
5 heads, 32 sectors/track, 48998 cylinders, total 7839744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          8,064     7,839,743     7,831,680   b W95 FAT32


Drive: pdc_ceddccceea _____________________________________________________________________

Disk /dev/mapper/pdc_ceddccceea: 640.0 GB, 640000000000 bytes
38 heads, 36 sectors/track, 913742 cylinders, total 1250000000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/pdc_ceddccceea2        105,336,832 1,250,260,991 1,144,924,160   f W95 Extended (LBA)
/dev/mapper/pdc_ceddccceea5        105,338,883 1,250,260,991 1,144,922,109   7 NTFS / exFAT / HPFS

/dev/mapper/pdc_ceddccceea2 ends after the last sector of /dev/mapper/pdc_ceddccceea
/dev/mapper/pdc_ceddccceea5 ends after the last sector of /dev/mapper/pdc_ceddccceea

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7bd68157-3d4f-401f-9ee2-33afc0d3f4ca   ext4       
/dev/sda5        ff07714b-7708-46af-b93d-aef275b9d62d   swap       
/dev/sdb1        F496329896325B76                       ntfs       System Reserved
/dev/sdb2        ECFE445EFE4422E6                       ntfs       BAD
/dev/sdc5        B426B87CA4E48287                       ntfs       Data
/dev/sdd1        869D-AB3D                              vfat       MYLINUXLIVE

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
pdc_ceddccceea
pdc_ceddccceea2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd2,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  7bd68157-3d4f-401f-9ee2-33afc0d3f4ca
else
  search --no-floppy --fs-uuid --set=root 7bd68157-3d4f-401f-9ee2-33afc0d3f4ca
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
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

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  7bd68157-3d4f-401f-9ee2-33afc0d3f4ca
    else
      search --no-floppy --fs-uuid --set=root 7bd68157-3d4f-401f-9ee2-33afc0d3f4ca
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  7bd68157-3d4f-401f-9ee2-33afc0d3f4ca
    else
      search --no-floppy --fs-uuid --set=root 7bd68157-3d4f-401f-9ee2-33afc0d3f4ca
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-F496329896325B76' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  F496329896325B76
    else
      search --no-floppy --fs-uuid --set=root F496329896325B76
    fi
    parttool ${root} hidden-
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=7bd68157-3d4f-401f-9ee2-33afc0d3f4ca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ff07714b-7708-46af-b93d-aef275b9d62d none            swap    sw              0       0

//192.168.10.116/Multimedia/pics    /media/pics    cifs    defaults,rw,credentials=/etc/nas-credential,uid=1000

//192.168.10.116/Download    /media/download    cifs    defaults,rw,credentials=/etc/nas-credential,uid=1000

//192.168.10.116/tv    /media/tv    cifs    defaults,rw,credentials=/etc/nas-credential,uid=1000

--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sdd1/boot/grub/grub.cfg: ===========================

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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdd1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdd1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  22 00 6e 00 6f 00 6e 00  53 00 78 00 53 00 22 00  |".n.o.n.S.x.S.".|
00000010  2f 00 3e 00 3c 00 61 00  73 00 73 00 65 00 6d 00  |/.>.<.a.s.s.e.m.|
00000020  62 00 6c 00 79 00 49 00  64 00 65 00 6e 00 74 00  |b.l.y.I.d.e.n.t.|
00000030  69 00 74 00 79 00 20 00  6e 00 61 00 6d 00 65 00  |i.t.y. .n.a.m.e.|
00000040  3d 00 22 00 4d 00 69 00  63 00 72 00 6f 00 73 00  |=.".M.i.c.r.o.s.|
00000050  6f 00 66 00 74 00 2d 00  57 00 69 00 6e 00 64 00  |o.f.t.-.W.i.n.d.|
00000060  6f 00 77 00 73 00 2d 00  4c 00 53 00 41 00 2e 00  |o.w.s.-.L.S.A...|
00000070  52 00 65 00 73 00 6f 00  75 00 72 00 63 00 65 00  |R.e.s.o.u.r.c.e.|
00000080  73 00 22 00 20 00 76 00  65 00 72 00 73 00 69 00  |s.". .v.e.r.s.i.|
00000090  6f 00 6e 00 3d 00 22 00  36 00 2e 00 31 00 2e 00  |o.n.=.".6...1...|
000000a0  37 00 36 00 30 00 31 00  2e 00 32 00 32 00 37 00  |7.6.0.1...2.2.7.|
000000b0  31 00 32 00 22 00 20 00  70 00 72 00 6f 00 63 00  |1.2.". .p.r.o.c.|
000000c0  65 00 73 00 73 00 6f 00  72 00 41 00 72 00 63 00  |e.s.s.o.r.A.r.c.|
000000d0  68 00 69 00 74 00 65 00  63 00 74 00 75 00 72 00  |h.i.t.e.c.t.u.r.|
000000e0  65 00 3d 00 22 00 61 00  6d 00 64 00 36 00 34 00  |e.=.".a.m.d.6.4.|
000000f0  22 00 20 00 6c 00 61 00  6e 00 67 00 75 00 61 00  |". .l.a.n.g.u.a.|
00000100  67 00 65 00 3d 00 22 00  6a 00 61 00 2d 00 4a 00  |g.e.=.".j.a.-.J.|
00000110  50 00 22 00 20 00 62 00  75 00 69 00 6c 00 64 00  |P.". .b.u.i.l.d.|
00000120  54 00 79 00 70 00 65 00  3d 00 22 00 72 00 65 00  |T.y.p.e.=.".r.e.|
00000130  6c 00 65 00 61 00 73 00  65 00 22 00 20 00 70 00  |l.e.a.s.e.". .p.|
00000140  75 00 62 00 6c 00 69 00  63 00 4b 00 65 00 79 00  |u.b.l.i.c.K.e.y.|
00000150  54 00 6f 00 6b 00 65 00  6e 00 3d 00 22 00 33 00  |T.o.k.e.n.=.".3.|
00000160  31 00 62 00 66 00 33 00  38 00 35 00 36 00 61 00  |1.b.f.3.8.5.6.a.|
00000170  64 00 33 00 36 00 34 00  65 00 33 00 35 00 22 00  |d.3.6.4.e.3.5.".|
00000180  20 00 76 00 65 00 72 00  73 00 69 00 6f 00 6e 00  | .v.e.r.s.i.o.n.|
00000190  53 00 63 00 6f 00 70 00  65 00 3d 00 22 00 6e 00  |S.c.o.p.e.=.".n.|
000001a0  6f 00 6e 00 53 00 78 00  53 00 22 00 2f 00 3e 00  |o.n.S.x.S."./.>.|
000001b0  3c 00 61 00 73 00 73 00  65 00 6d 00 62 00 00 fe  |<.a.s.s.e.m.b...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e0 ff 01 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on pdc_ceddccceea5



=============================== StdErr Messages: ===============================

ERROR: pdc: wrong # of devices in RAID set "pdc_ceddccceea" [1/2] on /dev/sdc
ERROR: pdc: wrong # of devices in RAID set "pdc_ceddccceea" [1/2] on /dev/sdc
ERROR: pdc: wrong # of devices in RAID set "pdc_ceddccceea" [1/2] on /dev/sdc
ERROR: pdc: wrong # of devices in RAID set "pdc_ceddccceea" [1/2] on /dev/sdc
ERROR: creating degraded mirror mapping for "pdc_ceddccceea"
ERROR: dos: partition address past end of RAID device
ERROR: pdc: wrong # of devices in RAID set "pdc_ceddccceea" [1/2] on /dev/sdc
ERROR: pdc: wrong # of devices in RAID set "pdc_ceddccceea" [1/2] on /dev/sdc
ERROR: pdc: wrong # of devices in RAID set "pdc_ceddccceea" [1/2] on /dev/sdc
ERROR: pdc: wrong # of devices in RAID set "pdc_ceddccceea" [1/2] on /dev/sdc
cat: /tmp/BootInfo-1Em5DFMs/Tmp_Log: No such file or directory
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-1Em5DFMs/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-1Em5DFMs/Tmp_Log: No such file or directory
hexdump: /dev/mapper/pdc_ceddccceea5: No such file or directory
hexdump: /dev/mapper/pdc_ceddccceea5: No such file or directory
ERROR: pdc: wrong # of devices in RAID set "pdc_ceddccceea" [1/2] on /dev/sdc
ERROR: pdc: wrong # of devices in RAID set "pdc_ceddccceea" [1/2] on /dev/sdc
ERROR: dos: partition address past end of RAID device
  No volume groups found


```

---

### Post by yancek on 2015-10-07
I don't know what happened but your Ubuntu /boot/grub/grub.cfg file does not have an entry for Ubuntu but does have for memtest and windows.  That's the problem.  You can go to the site below using an Ubuntu Live CD/flash drive and follow the instructions to get boot repair and reinstall grub.

[http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)

Or use some of the other options suggested at the site below, start at Section 2.2

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by oldfred on 2015-10-07
Did you have sdc as RAID and now a drive is missing. 

Or was it RAID before and not used as RAID now? You need to remove RAID meta-data on drive.

The RAID is confusing or complicating the Boot-Repair summary. 

You should in advanced mode be able to select the Ubuntu install in sda1 and uninstall/reinstall grub to sda. It looks like you may have a grub version difference and a total reinstall will hopefully fix that.

---

### Post by sdlinux on 2015-10-08
> **yancek said:**
> I don't know what happened but your Ubuntu /boot/grub/grub.cfg file does not have an entry for Ubuntu but does have for memtest and windows.  That's the problem.  You can go to the site below using an Ubuntu Live CD/flash drive and follow the instructions to get boot repair and reinstall grub.

[http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)

Or use some of the other options suggested at the site below, start at Section 2.2

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

I tried boot repair again on ubuntu live usb and it hung again. Then I made a boot repair live usb and it still hung. I left it overnight (10+ hours) and its still on the step of trying to reinstall kernel. I'll have to try your sugestion to manually reinstall grub.


> **oldfred said:**
> Did you have sdc as RAID and now a drive is missing. 

Or was it RAID before and not used as RAID now? You need to remove RAID meta-data on drive.

The RAID is confusing or complicating the Boot-Repair summary. 

You should in advanced mode be able to select the Ubuntu install in sda1 and uninstall/reinstall grub to sda. It looks like you may have a grub version difference and a total reinstall will hopefully fix that.

I've never had raid setup on this PC. How do I get into advance mode? I don't see that option in grub. I do have the option to press "e" or "c". I don't know why there are older versions of grub. sda is a new drive, but the others are veyr old so maybe I had linux on them at one point but I am sure I would of formatted that out. Could it be boot repair installed it there? I did see it had an option checked to install grub on all hard drives.

---

### Post by oldfred on 2015-10-08
Sorry, advanced mode of Boot-Repair.

       Even if raid not used BIOS may have set parameters, Also check BIOS settings
sudo dmraid -E -r /dev/sdd

I think it is your sdd drive, but do not thing running the dmraid command on other drives harms anything.

---

### Post by sdlinux on 2015-10-08
I did the dmraid command and still same problem. 

I changed advanced options on boot repair but it still gets stuck on reinstalling kernel. It won't let me unchecked that.

I manually mounted Linux drive and installed grub. Still same problem. Do I need to update grub cfg to tell it where Linux is? How? Could it be that my kernel is gone? Where is kernel kept.

---

### Post by sdlinux on 2015-10-08
I realized my kernel was missing so I reinstalled from instructions on stackexchange. Then I rebooted and everything looked back to normal.

However, my Firefox is slow to render when I move the window and VMware complained it was missing kernel modules. So now I'm wondering if I installed the wrong kernel? It installed 3.13.0-65

---

### Post by oldfred on 2015-10-08
It depends on which 14.04 you are running. 

That is the kernel I have, but I have not updated kernel with the HWE - Hardware Enablement Stack which with the newer point releases of 14.04 like 14.04.3 you get. Mine still says 14.04.3 but is still based on the original install.

It used to be that the LTS did not have a new kernel or most software updated. Now with the point releases they update kernel & support software as so much new hardware is released and needs the newer kernel.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

If you use Boot-Repair to run the total uninstall/reinstall of grub you can also include an update to newest kernel. But again depends on version of Ubuntu.

---

