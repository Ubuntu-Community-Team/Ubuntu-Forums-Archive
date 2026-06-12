---
title: "'Can't have a partition outside the disk' error."
date: 2014-01-26
forum: General Help
---

### Post by Bucky Ball on 2014-01-26
Hi all,

As per the title. Working on a friend's computer and have gotten myself into a bit of a partition table pickle. Without getting into how I got here, let's get into what I now have and try and verify how I might go about fixing it.

When I open Gparted it tells me sda (the only disk in the machine) is unallocated. Odd, as Ubuntu is booting fine! There is a dodgy XP installed, a storage partition, and Ubuntu all as primary partitions, then an extended with Bodhi and swap. After running:

```
sudo sfdisk -d /dev/sda > sda-backup.txt
sudo leafpad sda-backup.txt
```

... which I got from here:

[http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk](http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk)

... I get:

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 61898369, Id= 7, bootable
/dev/sda2 : start= 61898432, size=193229833, Id= 7
/dev/sda3 : start=255133696, size= 26345472, Id=83
/dev/sda4 : start=281479212, size= 31113558, Id= f
/dev/sda5 : start=281481216, size= 27195392, Id=83
```

Is it as easy as changing the size of sda4 and continuing to follow the instructions on the link? If so, what should I change it to? A total novice at this stuff, but learning ... From 'sudo fdisk -l' I get:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00048a9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61898431    30949184+   7  HPFS/NTFS/exFAT
/dev/sda2        61898432   255128264    96614916+   7  HPFS/NTFS/exFAT
/dev/sda3       255133696   281479167    13172736   83  Linux
/dev/sda4       281479212   312592769    15556779    f  W95 Ext'd (LBA)
/dev/sda5       281481216   308676607    13597696   83  Linux

```

sda4 is beyond the 312581808 sectors of the disk. From 'sudo fdisk /dev/sda:

```
Command (m for help): v
Remaining 3912740 unallocated 512-byte sectors
```

... and boot info script:

```
/dev/sda4 ends after the last sector of /dev/sda
```

That kind of says it all. But how do I fix it? It is as simple as writing the partition table as descibed on the link I provided previously? That section of the page describes my issue, so I guess so. I have gotten that exact error as described when putting in the code to check it is that problem.

```
$ sudo parted /dev/sdb unit s print
    Error: Can't have a partition outside the disk!
```

Here is the full bootinfo output:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Bodhi 2.0.0
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    61,898,431    61,898,369   7 NTFS / exFAT / HPFS
/dev/sda2          61,898,432   255,128,264   193,229,833   7 NTFS / exFAT / HPFS
/dev/sda3         255,133,696   281,479,167    26,345,472  83 Linux
/dev/sda4         281,479,212   312,592,769    31,113,558   f W95 Extended (LBA)
/dev/sda5         281,481,216   308,676,607    27,195,392  83 Linux

/dev/sda4 ends after the last sector of /dev/sda

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        0057E4F75304F94D                       ntfs       Windows
/dev/sda2        D2AC5901AC58E191                       ntfs       Storage
/dev/sda3        00ebffa7-e6b5-42fd-bddf-75e5228552eb   ext4       Xubuntu
/dev/sda5        2a72510e-3773-4c93-9194-42329f083787   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/Windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="USB Repair NOT to Start Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

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
set default="Windows NT/2000/XP (loader) (on /dev/sda1)"
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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 00ebffa7-e6b5-42fd-bddf-75e5228552eb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 00ebffa7-e6b5-42fd-bddf-75e5228552eb
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 00ebffa7-e6b5-42fd-bddf-75e5228552eb
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
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
menuentry 'Ubuntu, with Linux 3.2.0-58-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 00ebffa7-e6b5-42fd-bddf-75e5228552eb
	linux	/boot/vmlinuz-3.2.0-58-generic-pae root=UUID=00ebffa7-e6b5-42fd-bddf-75e5228552eb ro   splash quiet $vt_handoff
	initrd	/boot/initrd.img-3.2.0-58-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-58-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 00ebffa7-e6b5-42fd-bddf-75e5228552eb
	echo	'Loading Linux 3.2.0-58-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-58-generic-pae root=UUID=00ebffa7-e6b5-42fd-bddf-75e5228552eb ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-58-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 00ebffa7-e6b5-42fd-bddf-75e5228552eb
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 00ebffa7-e6b5-42fd-bddf-75e5228552eb
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 0057E4F75304F94D
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Bodhi Linux, with Linux 3.8.0-19-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 2a72510e-3773-4c93-9194-42329f083787
	linux /boot/vmlinuz-3.8.0-19-generic root=UUID=2a72510e-3773-4c93-9194-42329f083787 ro splash quiet $vt_handoff
	initrd /boot/initrd.img-3.8.0-19-generic
}
menuentry "Bodhi Linux, with Linux 3.8.0-19-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 2a72510e-3773-4c93-9194-42329f083787
	linux /boot/vmlinuz-3.8.0-19-generic root=UUID=2a72510e-3773-4c93-9194-42329f083787 ro recovery nomodeset
	initrd /boot/initrd.img-3.8.0-19-generic
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
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda8 :
UUID=00ebffa7-e6b5-42fd-bddf-75e5228552eb	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda5 :
#UUID=92485A39485A1C73	/media/Storage	ntfs-3g	defaults,locale=en_AU.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=0057E4F75304F94D	/media/Windows	ntfs-3g	defaults,locale=en_AU.UTF-8	0	0
#Entry for /dev/sda7 :
UUID=af68d8ad-ee9b-4ace-ad10-c4e9d0e8da9a	none	swap	sw	0	0


--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-58-generic-pae           2
               =                boot/vmlinuz-3.2.0-58-generic-pae              1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=========================== sda5/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 2a72510e-3773-4c93-9194-42329f083787
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 2a72510e-3773-4c93-9194-42329f083787
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
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
menuentry 'Bodhi Linux, with Linux 3.8.0-19-generic' --class bodhi --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2a72510e-3773-4c93-9194-42329f083787
	linux	/boot/vmlinuz-3.8.0-19-generic root=UUID=2a72510e-3773-4c93-9194-42329f083787 ro   splash quiet $vt_handoff
	initrd	/boot/initrd.img-3.8.0-19-generic
}
menuentry 'Bodhi Linux, with Linux 3.8.0-19-generic (recovery mode)' --class bodhi --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2a72510e-3773-4c93-9194-42329f083787
	echo	'Loading Linux 3.8.0-19-generic ...'
	linux	/boot/vmlinuz-3.8.0-19-generic root=UUID=2a72510e-3773-4c93-9194-42329f083787 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.8.0-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2a72510e-3773-4c93-9194-42329f083787
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 2a72510e-3773-4c93-9194-42329f083787
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 0057E4F75304F94D
	drivemap -s (hd0) ${root}
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
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=2a72510e-3773-4c93-9194-42329f083787 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=af68d8ad-ee9b-4ace-ad10-c4e9d0e8da9a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.8.0-19-generic               1
               =                boot/vmlinuz-3.8.0-19-generic                  1
               =                initrd.img                                     1
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  5d c3 cf 6f 4c 27 15 f4  a1 ed e8 bf 75 6a da a7  |]..oL'......uj..|
00000010  ad 6f 20 89 b1 d9 30 e9  22 46 da c0 09 80 19 bf  |.o ...0."F......|
00000020  47 0f a0 13 fc 2e ff 3d  e8 75 29 d6 b7 9e 00 66  |G......=.u)....f|
00000030  00 fa 0b 71 07 82 aa 2e  58 32 c3 9b d6 80 39 fe  |...q....X2....9.|
00000040  6f 79 39 71 5c ba ae 58  18 de 78 10 00 a4 01 4e  |oy9q\..X..x....N|
00000050  00 3d f6 00 3a 12 57 2e  97 2c a7 ac a7 b6 74 0c  |.=..:.W..,....t.|
00000060  b9 61 56 37 3f 78 02 58  58 f8 db 9a 00 bb fa 08  |.aV7?x.XX.......|
00000070  3f d9 ed 7e 05 87 11 c4  29 96 9f b2 53 9a b3 6e  |?..~....)...S..n|
00000080  5b 94 a4 2a 86 56 ea 80  3b f6 17 fe f7 c2 38 82  |[..*.V..;.....8.|
00000090  b9 e0 3e c9 fb 8a dc 8d  17 c0 03 b2 26 7f c4 48  |..>.........&..H|
000000a0  38 4b a1 f9 60 d4 18 5b  7a 3f 51 06 e5 17 90 3d  |8K..`..[z?Q....=|
000000b0  c0 39 83 e0 f6 dd 3c b4  07 9b 4a 0c a4 8a da 79  |.9....<...J....y|
000000c0  b4 9a da a7 70 61 d5 92  3d bb e7 32 b4 79 56 d9  |....pa..=..2.yV.|
000000d0  d6 31 56 b6 eb 09 59 47  b3 31 b5 39 47 0f a0 14  |.1V...YG.1.9G...|
000000e0  5a 8c d6 d7 94 b6 a7 35  b0 15 cc 91 9e e3 6c e6  |Z......5......l.|
000000f0  b4 35 ae 35 81 ad 91 3e  56 a3 1b 54 6b 2c ad a2  |.5.5...>V..Tk,..|
00000100  ea 30 9c b0 4f 4a c4 73  6c d2 b2 ca d7 cd 6a f2  |.0..OJ.sl.....j.|
00000110  b4 cd 95 ab 71 b5 12 94  d5 c6 be 56 a9 d5 b3 8d  |....q......V....|
00000120  ad ca da a8 d5 e3 59 19  23 44 6b d3 9b 55 8d 4e  |......Y.#Dk..U.N|
00000130  35 d8 d4 e0 c6 50 f6 db  65 56 d6 fd c1 0c 02 39  |5....P..eV.....9|
00000140  01 55 6f aa 80 2d c5 ee  80 ae 37 ca be e0 86 01  |.Uo..-....7.....|
00000150  1c 84 56 fa 80 03 3c 5e  68 0a e3 7a 40 0b 41 0c  |..V...<^h..z@.A.|
00000160  01 78 a3 15 bc b0 05 85  57 b6 f5 c0 0d 44 b8 88  |.x......W....D..|
00000170  00 fb eb cb ea 79 c7 fc  3a 8e e4 4e 26 50 a3 2b  |.....y..:..N&P.+|
00000180  78 40 40 04 b0 07 8f 00  5c 00 c0 57 c7 ce af 77  |x@@.....\..W...w|
00000190  00 0f ec 3c c8 2c bc cf  47 0f a0 d5 d9 79 06 4b  |...<.,..G....y.K|
000001a0  da 23 51 6c 74 df 77 75  8e 46 21 98 a5 a8 de 07  |.#Qlt.wu.F!.....|
000001b0  34 f7 8e 8e ea 72 2d 77  ca 7f 85 db fb 86 00 fe  |4....r-w........|
000001c0  ff ff 83 fe ff ff d4 07  00 00 00 f8 9e 01 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

So should I just go ahead and follow the what seems like reasonably sound advice on that page? I would prefer not to screw this up any further as this has taken longer than expected already.

All responses appreciated. TIA. ;)

---

### Post by sudodus on 2014-01-26
I would 'just go ahead and follow the what seems like reasonably sound advice on that page', but if your friend prefers waiting for a backup (and you too), fine, and you'll have peace of mind :-)

---

### Post by Bucky Ball on 2014-01-26
Everything is backed up. The Windows is dead anyway but all personal stuff backed up from there, sda2 was another dead XP, also backed up then partition reformatted. Ubuntu and Bodhi are fresh installs so nothing to lose (this machine was headed to the recyclers, but mini install running xfce4 and a few apps flys on Atom 1.6gHz and 1Gb RAM, giving it new lease on life). ;)

Find attached the window I get from Gparted when I double click the unallocated sda.

If the last sector according to gparted is 312581807, then is it as simple as changing sda4 to something inside that? ... as it is currently showing:

```
/dev/sda4       281479212   **312592769**    15556779    f  W95 Ext'd (LBA)
```

Should I change it to something like 312581806? Should it be a multiple of eight? No idea. On that size it mentions 'Change the old size of the partition sda4 to the calculated new size.' How do I calculate a new size? :-k

---

### Post by sudodus on 2014-01-26
I would calculate it to be inside the drive according to fdisk -lu 
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
```

---

### Post by Bucky Ball on 2014-01-26
Thanks. That appears to make perfect sense. My next question is this. If I am changing it according to the method used on that link, sda-backup.txt shows the size of sda4 thus:

```
/dev/sda4 : start=281479212, size= **31113558**, Id= f
```

... while 'fdisk -lu' provides its end point as a different number:

```
/dev/sda4       281479212   **312592769**    15556779    f  W95 Ext'd (LBA)
```

This is where I'm getting a bit confused. If I'm working from the method in the link for a fix I'm working with the former number rather than the latter. 

(For anyone that may not notice, sda4 is an extended partition. ;))

---

### Post by sudodus on 2014-01-26
I would make the size such that the end-point is inside the drive according to fdisk (I think it matches the 160 GB correctly). I am not sure what is your problem. You should also check that the logical partition will be inside boundaries of the extended partition.

---

### Post by fantab on 2014-01-26
Have you checked this:[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/) ? 

[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

---

### Post by Bucky Ball on 2014-01-26
fantab, you legend. fixparts. Took me less than two minutes from clicking your first link to fixed. Another one for the archives. 

Thanks all. Case closed. ;)

---

