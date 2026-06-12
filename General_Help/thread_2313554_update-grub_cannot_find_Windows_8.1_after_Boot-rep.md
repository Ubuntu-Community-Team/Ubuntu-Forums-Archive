---
title: "update-grub cannot find Windows 8.1 after Boot-repair"
date: 2016-02-13
forum: General Help
---

### Post by Grouver on 2016-02-13
I am running Xubuntu by default.
Alright so i managed to install WIndows 8.1 on a seperate harddisk.
After the installation finished up I could not boot into Xubuntu anymore.
Even if I removed all harddisks except that Xubuntu one it would still display a Windows Boot Error message.
So I got myself a xubuntu live cd and installed and runned boot-repair tool with the recommended setting. This seemed to fix the problem and now i can luckly boot into my default Xubuntu enviorment. Hoorah. :)

But now i would like to add the Windows installation to GRUB2 so i can switch between Windows or Linux when booting.

Only if mount the Windows installation and I do sudo update-grub it says:
```
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-61-generic
Found initrd image: /boot/initrd.img-3.16.0-61-generic
Found linux image: /boot/vmlinuz-3.16.0-60-generic
Found initrd image: /boot/initrd.img-3.16.0-60-generic
Found linux image: /boot/vmlinuz-3.16.0-58-generic
Found initrd image: /boot/initrd.img-3.16.0-58-generic
Found linux image: /boot/vmlinuz-3.16.0-57-generic
Found initrd image: /boot/initrd.img-3.16.0-57-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done

```

And if i do os-probe it doesnt say anything.

I cannot figure out how to let GRUB see the Windows installation.

I hope somebody can help me out to add Windows to the GRUB2 menu.
Thank you!

The regarding Boot-repair pastebin:

```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 81783949-8869-4da8-b3c1-1d81b50f3308 root hd3,msdos7 
    set prefix=($root)'/grub'
    
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 81783949-8869-4da8-b3c1-1d81b50f3308 root hd3,msdos7 
    set prefix=($root)'/grub'
    
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 81783949-8869-4da8-b3c1-1d81b50f3308 root hd3,msdos7 
    set prefix=($root)'/grub'
    
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/grub.
 => Grub2 (v2.00) is installed in the MBR of /dev/sde and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Boot/BCD

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdd5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS 
    Boot files:        /etc/fstab

sdd6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdd7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/i386-pc/core.img

sdd8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdd9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   625,137,663   625,135,616   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd2               2,048   250,066,943   250,064,896   5 Extended
/dev/sdd5           1,001,472    40,060,927    39,059,456  83 Linux
/dev/sdd6          40,062,976   137,717,759    97,654,784  83 Linux
/dev/sdd7    *    137,719,808   138,498,047       778,240  83 Linux
/dev/sdd8         138,500,096   197,091,327    58,591,232  83 Linux
/dev/sdd9         197,093,376   206,856,191     9,762,816  83 Linux


Drive: sde _____________________________________________________________________

Disk /dev/sde: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *          2,048   625,139,711   625,137,664   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7EEA5374EA5327A3                       ntfs       
/dev/sdb1        5254719E5471858F                       ntfs       
/dev/sdc1        A85EDA9D5EDA641A                       ntfs       
/dev/sdd5        8a8de9a5-b7af-4180-9e3f-45cbf2cca97c   ext4       
/dev/sdd6        4528d284-339a-49e4-95ec-696d231ae000   ext4       
/dev/sdd7        81783949-8869-4da8-b3c1-1d81b50f3308   ext4       
/dev/sdd8        7e308906-cb7e-4f5c-99bd-5de9d19e12d1   ext4       
/dev/sdd9        d2fb5918-ebe4-4a0b-894f-7f4cfc1437ab   ext4       
/dev/sde1        4C6E670B15FD24CD                       ntfs       
/dev/sr0                                                iso9660    Xubuntu 14.04.2 LTS amd64

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Feb 13 17:09 ata-Crucial_CT128M550SSD1_14200C23A767 -> ../../sdd
lrwxrwxrwx 1 root root 10 Feb 13 09:04 ata-Crucial_CT128M550SSD1_14200C23A767-part2 -> ../../sdd2
lrwxrwxrwx 1 root root 10 Feb 13 09:04 ata-Crucial_CT128M550SSD1_14200C23A767-part5 -> ../../sdd5
lrwxrwxrwx 1 root root 10 Feb 13 09:04 ata-Crucial_CT128M550SSD1_14200C23A767-part6 -> ../../sdd6
lrwxrwxrwx 1 root root 10 Feb 13 09:04 ata-Crucial_CT128M550SSD1_14200C23A767-part7 -> ../../sdd7
lrwxrwxrwx 1 root root 10 Feb 13 09:04 ata-Crucial_CT128M550SSD1_14200C23A767-part8 -> ../../sdd8
lrwxrwxrwx 1 root root 10 Feb 13 09:04 ata-Crucial_CT128M550SSD1_14200C23A767-part9 -> ../../sdd9
lrwxrwxrwx 1 root root  9 Feb 13 17:09 ata-Hitachi_HDT725032VLA360_VFK204R810A0JH -> ../../sdc
lrwxrwxrwx 1 root root 10 Feb 13 17:09 ata-Hitachi_HDT725032VLA360_VFK204R810A0JH-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Feb 13 17:09 ata-Hitachi_HDT725032VLA360_VFK204R81RABUH -> ../../sde
lrwxrwxrwx 1 root root 10 Feb 13 17:09 ata-Hitachi_HDT725032VLA360_VFK204R81RABUH-part1 -> ../../sde1
lrwxrwxrwx 1 root root  9 Feb 13 09:04 ata-LITE-ON_DVDRW_LH-20A1S -> ../../sr0
lrwxrwxrwx 1 root root  9 Feb 13 17:09 ata-SAMSUNG_HD103UJ_S13PJ90QB39430 -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb 13 17:09 ata-SAMSUNG_HD103UJ_S13PJ90QB39430-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Feb 13 17:09 ata-ST1000DM005_HD103SJ_S246J9FC403485 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 13 17:09 ata-ST1000DM005_HD103SJ_S246J9FC403485-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 Feb 13 17:09 wwn-0x50000f000b3b4903 -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb 13 17:09 wwn-0x50000f000b3b4903-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Feb 13 17:09 wwn-0x50004cf2072d7fb8 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 13 17:09 wwn-0x50004cf2072d7fb8-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 Feb 13 17:09 wwn-0x5000cca317ce3d1b -> ../../sdc
lrwxrwxrwx 1 root root 10 Feb 13 17:09 wwn-0x5000cca317ce3d1b-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Feb 13 17:09 wwn-0x5000cca317d83ea3 -> ../../sde
lrwxrwxrwx 1 root root 10 Feb 13 17:09 wwn-0x5000cca317d83ea3-part1 -> ../../sde1
lrwxrwxrwx 1 root root  9 Feb 13 17:09 wwn-0x500a07510c23a767 -> ../../sdd
lrwxrwxrwx 1 root root 10 Feb 13 09:04 wwn-0x500a07510c23a767-part2 -> ../../sdd2
lrwxrwxrwx 1 root root 10 Feb 13 09:04 wwn-0x500a07510c23a767-part5 -> ../../sdd5
lrwxrwxrwx 1 root root 10 Feb 13 09:04 wwn-0x500a07510c23a767-part6 -> ../../sdd6
lrwxrwxrwx 1 root root 10 Feb 13 09:04 wwn-0x500a07510c23a767-part7 -> ../../sdd7
lrwxrwxrwx 1 root root 10 Feb 13 09:04 wwn-0x500a07510c23a767-part8 -> ../../sdd8
lrwxrwxrwx 1 root root 10 Feb 13 09:04 wwn-0x500a07510c23a767-part9 -> ../../sdd9

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sdd5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sde5 during installation
UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sde7 during installation
#UUID=81783949-8869-4da8-b3c1-1d81b50f3308 /boot           ext4    defaults        0       2
# /home was on /dev/sde6 during installation
UUID=4528d284-339a-49e4-95ec-696d231ae000 /home           ext4    defaults        0       2
# /tmp was on /dev/sde9 during installation
UUID=d2fb5918-ebe4-4a0b-894f-7f4cfc1437ab /tmp            ext4    defaults        0       2
# /var was on /dev/sde8 during installation
UUID=7e308906-cb7e-4f5c-99bd-5de9d19e12d1 /var            ext4    defaults        0       2
# swap was on /dev/sde1 during installation
#UUID=75f0cc46-7b82-4ddb-9878-e732bb3482ea none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
#automount of all disks
UUID=7EEA5374EA5327A3 /media/roy/U/ ntfs-3g uid=1000,gid=1000,defaults
UUID=5254719E5471858F /media/roy/B/ ntfs-3g uid=1000,gid=1000,defaults
UUID=A85EDA9D5EDA641A /media/roy/D/ ntfs-3g uid=1000,gid=1000,defaults
UUID=C44875FA4875EC14 /media/roy/C/ ntfs-3g uid=1000,gid=1000,defaults
UUID=81783949-8869-4da8-b3c1-1d81b50f3308	/boot	ext4	defaults	0	2
--------------------------------------------------------------------------------

============================= sdd7/grub/grub.cfg: ==============================

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
set root='hd3,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos5 --hint-efi=hd3,msdos5 --hint-baremetal=ahci3,msdos5  8a8de9a5-b7af-4180-9e3f-45cbf2cca97c
else
  search --no-floppy --fs-uuid --set=root 8a8de9a5-b7af-4180-9e3f-45cbf2cca97c
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd3,msdos7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
	else
	  search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
	fi
	linux	/vmlinuz-3.16.0-61-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro  quiet splash acpi=force $vt_handoff
	initrd	/initrd.img-3.16.0-61-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
	menuentry 'Ubuntu, with Linux 3.16.0-61-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-61-generic-advanced-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd3,msdos7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
		else
		  search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
		fi
		echo	'Loading Linux 3.16.0-61-generic ...'
		linux	/vmlinuz-3.16.0-61-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro  quiet splash acpi=force $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/initrd.img-3.16.0-61-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-61-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-61-generic-recovery-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd3,msdos7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
		else
		  search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
		fi
		echo	'Loading Linux 3.16.0-61-generic ...'
		linux	/vmlinuz-3.16.0-61-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/initrd.img-3.16.0-61-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-60-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-60-generic-advanced-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd3,msdos7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
		else
		  search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
		fi
		echo	'Loading Linux 3.16.0-60-generic ...'
		linux	/vmlinuz-3.16.0-60-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro  quiet splash acpi=force $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/initrd.img-3.16.0-60-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-60-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-60-generic-recovery-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd3,msdos7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
		else
		  search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
		fi
		echo	'Loading Linux 3.16.0-60-generic ...'
		linux	/vmlinuz-3.16.0-60-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/initrd.img-3.16.0-60-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-58-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-58-generic-advanced-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd3,msdos7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
		else
		  search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
		fi
		echo	'Loading Linux 3.16.0-58-generic ...'
		linux	/vmlinuz-3.16.0-58-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro  quiet splash acpi=force $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/initrd.img-3.16.0-58-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-58-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-58-generic-recovery-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd3,msdos7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
		else
		  search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
		fi
		echo	'Loading Linux 3.16.0-58-generic ...'
		linux	/vmlinuz-3.16.0-58-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/initrd.img-3.16.0-58-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-57-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-57-generic-advanced-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd3,msdos7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
		else
		  search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
		fi
		echo	'Loading Linux 3.16.0-57-generic ...'
		linux	/vmlinuz-3.16.0-57-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro  quiet splash acpi=force $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/initrd.img-3.16.0-57-generic
	}
	menuentry 'Ubuntu, with Linux 3.16.0-57-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-57-generic-recovery-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd3,msdos7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
		else
		  search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
		fi
		echo	'Loading Linux 3.16.0-57-generic ...'
		linux	/vmlinuz-3.16.0-57-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/initrd.img-3.16.0-57-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
	fwsetup
}
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

=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
cat: write error: Broken pipe
cat: write error: Broken pipe
cat: write error: Broken pipe
cat: write error: Broken pipe
File descriptor 9 (/proc/5718/mounts) leaked on lvs invocation. Parent PID 23646: bash
File descriptor 63 (pipe:[47838]) leaked on lvs invocation. Parent PID 23646: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-02-13__17h09 ===================
boot-repair version : 4ppa35
boot-sav version : 4ppa35
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa35
boot-repair is executed in live-session (Ubuntu 14.04.2 LTS, trusty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash --
ls: cannot access /home/usr/.config: No such file or directory
Windows is hibernated, refused to mount.
Failed to mount '/dev/sde1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sde1 /mnt/boot-sav/sde1

=================== os-prober:
/dev/sdd5:Ubuntu 14.04.3 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="7EEA5374EA5327A3" TYPE="ntfs"
/dev/sdb1: UUID="5254719E5471858F" TYPE="ntfs"
/dev/sdc1: UUID="A85EDA9D5EDA641A" TYPE="ntfs"
/dev/sdd5: UUID="8a8de9a5-b7af-4180-9e3f-45cbf2cca97c" TYPE="ext4"
/dev/sdd6: UUID="4528d284-339a-49e4-95ec-696d231ae000" TYPE="ext4"
/dev/sdd7: UUID="81783949-8869-4da8-b3c1-1d81b50f3308" TYPE="ext4"
/dev/sdd8: UUID="7e308906-cb7e-4f5c-99bd-5de9d19e12d1" TYPE="ext4"
/dev/sdd9: UUID="d2fb5918-ebe4-4a0b-894f-7f4cfc1437ab" TYPE="ext4"
/dev/sr0: LABEL="Xubuntu 14.04.2 LTS amd64" TYPE="iso9660"
/dev/sde1: UUID="4C6E670B15FD24CD" TYPE="ntfs"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Windows not detected by os-prober on sde1.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== sdd5/etc/grub.d/ :
drwxr-xr-x  2 root root      4096 Jan  6 17:59 grub.d
total 76
-rwxr-xr-x 1 root root  9791 Dec 17 15:00 00_header
-rwxr-xr-x 1 root root  6058 May  8  2014 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15  2014 10_linux
-rwxr-xr-x 1 root root 10412 May 15  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 May 15  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15  2014 40_custom
-rwxr-xr-x 1 root root   216 May 15  2014 41_custom
-rw-r--r-- 1 root root   483 May 15  2014 README




=================== sdd5/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
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



/boot detected in the fstab of sdd5: UUID=81783949-8869-4da8-b3c1-1d81b50f3308  (sdd7)
=================== No kernel in /mnt/boot-sav/sdd7/boot:
grub



=================== efibootmgr -v
BootCurrent: 0009
Timeout: 1 seconds
BootOrder: 0009,0002,0001,0005,0006,0007,0008
Boot0001* LITE-ON DVDRW LH-20A1S	BIOS(3,0,00)AMBO
Boot0002* Crucial_CT128M550SSD1	BIOS(2,0,00)AMBO
Boot0005* Hitachi HDT725032VLA360	BIOS(2,0,00)AMBO
Boot0006* ST1000DM005 HD103SJ	BIOS(2,0,00)AMBO
Boot0007* SAMSUNG HD103UJ	BIOS(2,0,00)AMBO
Boot0008* Hitachi HDT725032VLA360	BIOS(2,0,00)AMBO
Boot0009* UEFI: LITE-ON DVDRW LH-20A1S	ACPI(a0341d0,0)PCI(1f,2)03120a000400ffff0000CD-ROM(1,71adc,1240)AMBO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda1.
sdb1	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb1.
sdc1	: sdc,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdc1.
sdd5	: sdd,	not-sepboot,	no-grubenv	grub2,	grub-pc ,	update-grub,	64,	no-boot,	is-os,	not--efi--part,	fstab-has-goodBOOT,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdd5.
sdd6	: sdd,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdd6.
sdd7	: sdd,	is-sepboot,	grubenv-ok	nogrub,	no-docgrub,	no-update-grub,	32,	no-kernel,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdd7.
sdd8	: sdd,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdd8.
sdd9	: sdd,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdd9.
sde1	: sde,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sde1.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	no-os,	2048 sectors * 512 bytes
sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	no-os,	2048 sectors * 512 bytes
sdc	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	no-os,	2048 sectors * 512 bytes
sdd	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes
sde	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes


=================== parted -l:

Model: ATA ST1000DM005 HD10 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  1000GB  1000GB  primary  ntfs


Model: ATA SAMSUNG HD103UJ (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  1000GB  1000GB  primary  ntfs


Model: ATA Hitachi HDT72503 (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  320GB  320GB  primary  ntfs


Model: ATA Crucial_CT128M55 (scsi)
Disk /dev/sdd: 128GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
2      1049kB  128GB   128GB   extended
5      513MB   20.5GB  20.0GB  logical   ext4
6      20.5GB  70.5GB  50.0GB  logical   ext4
7      70.5GB  70.9GB  398MB   logical   ext4         boot
8      70.9GB  101GB   30.0GB  logical   ext4
9      101GB   106GB   4999MB  logical   ext4


Model: ATA Hitachi HDT72503 (scsi)
Disk /dev/sde: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  320GB  320GB  primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: Can't have a partition outside the disk!

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:512:msdos:ATA ST1000DM005 HD10;
1:1049kB:1000GB:1000GB:ntfs::;

BYT;
/dev/sdb:1000GB:scsi:512:512:msdos:ATA SAMSUNG HD103UJ;
1:1049kB:1000GB:1000GB:ntfs::;

BYT;
/dev/sdc:320GB:scsi:512:512:msdos:ATA Hitachi HDT72503;
1:1049kB:320GB:320GB:ntfs::;

BYT;
/dev/sdd:128GB:scsi:512:4096:msdos:ATA Crucial_CT128M55;
2:1049kB:128GB:128GB:::;
5:513MB:20.5GB:20.0GB:ext4::;
6:20.5GB:70.5GB:50.0GB:ext4::;
7:70.5GB:70.9GB:398MB:ext4::boot;
8:70.9GB:101GB:30.0GB:ext4::;
9:101GB:106GB:4999MB:ext4::;

BYT;
/dev/sde:320GB:scsi:512:512:msdos:ATA Hitachi HDT72503;
1:1049kB:320GB:320GB:ntfs::;

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: Can't have a partition outside the disk!

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sda   disk          931.5G
sda1  part ntfs     931.5G
sdb   disk          931.5G
sdb1  part ntfs     931.5G
sdc   disk          298.1G
sdc1  part ntfs     298.1G
sdd   disk          119.2G
sdd2  part              1K
sdd5  part ext4      18.6G
sdd6  part ext4      46.6G
sdd7  part ext4       380M
sdd8  part ext4        28G
sdd9  part ext4       4.7G
sde   disk          298.1G
sde1  part ntfs     298.1G
sr0   rom  iso9660    943M Xubuntu 14.04.2 LTS amd64
loop0 loop squashfs 902.5M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sdb      1  0  0 running
sdb1     1  0  0         /mnt/boot-sav/sdb1
sdc      1  0  0 running
sdc1     1  0  0         /mnt/boot-sav/sdc1
sdd      0  0  0 running
sdd2     0  0  0
sdd5     0  0  0         /mnt/boot-sav/sdd5
sdd6     0  0  0         /mnt/boot-sav/sdd6
sdd7     0  0  0         /mnt/boot-sav/sdd7
sdd8     0  0  0         /mnt/boot-sav/sdd8
sdd9     0  0  0         /mnt/boot-sav/sdd9
sde      1  0  0 running
sde1     1  0  0         /mnt/boot-sav/sde1
sr0      1  0  1 running /cdrom
loop0    1  1  0         /rofs


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=xubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd5 on /mnt/boot-sav/sdd5 type ext4 (rw)
/dev/sdd6 on /mnt/boot-sav/sdd6 type ext4 (rw)
/dev/sdd7 on /mnt/boot-sav/sdd7 type ext4 (rw)
/dev/sdd8 on /mnt/boot-sav/sdd8 type ext4 (rw)
/dev/sdd9 on /mnt/boot-sav/sdd9 type ext4 (rw)
/dev/sde1 on /mnt/boot-sav/sde1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdd2 sdd5 sdd6 sdd7 sdd8 sdd9 size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sde1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdc sdc1 sdd sdd2 sdd5 sdd6 sdd7 sdd8 sdd9 sde sde1 sg0 sg1 sg2 sg3 sg4 sg5 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 57 70 74 00 00 00 00  |.........Wpt....|
00000030  00 00 0c 00 00 00 00 00  7f 05 47 07 00 00 00 00  |..........G.....|
00000040  f6 00 00 00 01 00 00 00  a3 27 53 ea 74 53 ea 7e  |.........'S.tS.~|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 57 70 74 00 00 00 00  |.........Wpt....|
00000030  00 00 0c 00 00 00 00 00  7f 05 47 07 00 00 00 00  |..........G.....|
00000040  f6 00 00 00 01 00 00 00  8f 85 71 54 9e 71 54 52  |..........qT.qTR|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 53 63 68 69 6a 66  66 6f 75 74 00 0d 0a 62  |..Schijffout...b|
00000190  6f 6f 74 6d 67 72 20 6f  6e 74 62 72 65 65 6b 74  |ootmgr ontbreekt|
000001a0  00 0d 0a 62 6f 6f 74 6d  67 72 20 67 65 63 6f 6d  |...bootmgr gecom|
000001b0  70 72 69 6d 65 65 72 64  00 0d 0a 44 72 75 6b 20  |primeerd...Druk |
000001c0  43 74 72 6c 2b 41 6c 74  2b 44 65 6c 65 74 65 20  |Ctrl+Alt+Delete |
000001d0  6f 6d 20 6f 70 6e 69 65  75 77 20 74 65 20 73 74  |om opnieuw te st|
000001e0  61 72 74 65 6e 0d 0a 00  74 0d 0a 00 00 00 00 00  |arten...t.......|
000001f0  00 00 00 00 00 00 00 00  80 8d a1 b9 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdc1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff cf 42 25 00 00 00 00  |..........B%....|
00000030  00 00 0c 00 00 00 00 00  ff 2c 54 02 00 00 00 00  |.........,T.....|
00000040  f6 00 00 00 01 00 00 00  1a 64 da 5e 9d da 5e a8  |.........d.^..^.|
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

=================== hexdump -n512 -C /dev/sde1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff d7 42 25 00 00 00 00  |..........B%....|
00000030  04 00 00 00 00 00 00 00  7f 2d 54 02 00 00 00 00  |.........-T.....|
00000040  f6 00 00 00 01 00 00 00  cd 24 fd 15 0b 67 6e 4c  |.........$...gnL|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.4G  201M  3.2G   6% /
udev           devtmpfs   3.4G   12K  3.4G   1% /dev
tmpfs          tmpfs      692M  1.4M  691M   1% /run
/dev/sr0       iso9660    943M  943M     0 100% /cdrom
/dev/loop0     squashfs   903M  903M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.4G   12K  3.4G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      3.4G   80K  3.4G   1% /run/shm
none           tmpfs      100M   24K  100M   1% /run/user
/dev/sda1      fuseblk    932G  563G  369G  61% /mnt/boot-sav/sda1
/dev/sdb1      fuseblk    932G  767G  166G  83% /mnt/boot-sav/sdb1
/dev/sdc1      fuseblk    299G  261G   38G  88% /mnt/boot-sav/sdc1
/dev/sdd5      ext4        19G  7.3G   11G  42% /mnt/boot-sav/sdd5
/dev/sdd6      ext4        46G   12G   33G  26% /mnt/boot-sav/sdd6
/dev/sdd7      ext4       360M  168M  170M  50% /mnt/boot-sav/sdd7
/dev/sdd8      ext4        28G  2.1G   24G   8% /mnt/boot-sav/sdd8
/dev/sdd9      ext4       4.5G  9.4M  4.2G   1% /mnt/boot-sav/sdd9
/dev/sde1      fuseblk    299G   11G  288G   4% /mnt/boot-sav/sde1

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x060d0904

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74975362

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcacc81c6

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   625137663   312567808    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000e8f33

Device Boot      Start         End      Blocks   Id  System
/dev/sdd2            2048   250066943   125032448    5  Extended
/dev/sdd5         1001472    40060927    19529728   83  Linux
/dev/sdd6        40062976   137717759    48827392   83  Linux
/dev/sdd7   *   137719808   138498047      389120   83  Linux
/dev/sdd8       138500096   197091327    29295616   83  Linux
/dev/sdd9       197093376   206856191     4881408   83  Linux

Disk /dev/sde: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xadfbdd4f

Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048   625139711   312568832    7  HPFS/NTFS/exFAT


/boot detected. Please check the options.
Partition outside the disk detected.

=================== Recommended repair
The default repair of the Boot-Repair utility will reinstall the grub2 of sdd5 into the MBRs of all disks (except USB without OS), using the following options:        sdd7/boot,
The boot flag will be placed on sde1.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


parted /dev/sde set 1 boot on

                                                                          
Information: You may need to update /etc/fstab.

/boot added in sdd5/fstab
Quantity of real Windows: 1
WinSE in sde1
/mnt/boot-sav/sde1/ may need repair.
Mount sdd7 on /mnt/boot-sav/sdd5/boot

Reinstall the GRUB of sdd5 into all MBRs of disks with OS or not-USB

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1.7,grub-install (GRUB) 2.

Reinstall the GRUB of sdd5 into the MBR of sda
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1.7,grub-install (GRUB) 2.

Reinstall the GRUB of sdd5 into the MBR of sdb
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdb: exit code of grub-install /dev/sdb:0

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1.7,grub-install (GRUB) 2.

Reinstall the GRUB of sdd5 into the MBR of sdc
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdc: exit code of grub-install /dev/sdc:0

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1.7,grub-install (GRUB) 2.

Reinstall the GRUB of sdd5 into the MBR of sde
Installing for i386-pc platform.
grub-install: warning: Sector 32 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
grub-install: warning: Sector 33 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.
grub-install /dev/sde: exit code of grub-install /dev/sde:0

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1.7,grub-install (GRUB) 2.

Reinstall the GRUB of sdd5 into the MBR of sdd
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdd: exit code of grub-install /dev/sdd:0

chroot /mnt/boot-sav/sdd5 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-61-generic
Found initrd image: /boot/initrd.img-3.16.0-61-generic
Found linux image: /boot/vmlinuz-3.16.0-60-generic
Found initrd image: /boot/initrd.img-3.16.0-60-generic
Found linux image: /boot/vmlinuz-3.16.0-58-generic
Found initrd image: /boot/initrd.img-3.16.0-58-generic
Found linux image: /boot/vmlinuz-3.16.0-57-generic
Found initrd image: /boot/initrd.img-3.16.0-57-generic
mkdir: cannot create directory '/var/lib/os-prober/mount': No such file or directory
Adding boot menu entry for EFI firmware configuration

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdd (128GB) disk!

```

---

### Post by oldfred on 2016-02-13
I do not like Boot-Repair's auto fix with multiple drives. You usually want to keep the Windows boot loader on the Windows drive and grub on the Ubuntu drive and boot grub. Then when Windows breaks and you need to fix it you can directly boot Windows drive from BIOS and hope f8 works. Or else you need a Windows repairCD or flash drive.
Grub only boots working Windows.

Windows boots from BIOS drive set as default, to MBR, to PBR or NTFS partition with boot flag boot sector which specifies bootmgr (or ntldr with XP) and finds /Boot/BCD.
Grub2's os-prober just looks for bootmgr & /Boot/BCD as it then knows that is the Windows boot partition.
But you have bootmgr in sde1 and BCD in sdc1. But not NTFS partition with boot flag that has both?
I would move or run Windows repairs on one or the other partitions, restore Windows boot file to which ever sdc or sde is real Windows install. Make sure from BIOS you can boot Windows directly.
Usually best to keep Windows as first drive or sda. It does not like anything else, and often then gets confused if setting other drives as boot in BIOS.

Then boot grub from drive with Ubuntu and rerun 
sudo update-grub

---

### Post by Grouver on 2016-02-14
Well the problem is that Windows have overwritten my linux GRUB. I could only boot into Windows. 
And now using Boot-repair it probably has overwritten my Windows MBR. I do not know how to fix this problem.
Also for good order, the /Boot/BCD is a old file, there is no windows on that disk. I also just removed that.

Its also funny, i installed Windows 8. But the Boot-repair thinks its Windows Vista. Weird. =/

I am a little afraid repairing Windows and using EasyBCD to boot into Linux if that is what you mean?
I would like to use GRUB to be sure I can always boot into Linux. 

I hope you can use the information  in this post.

---

### Post by Grouver on 2016-02-14
Also, there is a bootmgr file on the Windows partition. So running /fixboot wont fix anything i guess.
Its just a mystery why os-probe wont find the bootmgr file.

---

### Post by Grouver on 2016-02-14
I did install Windows when in FastBoot mode which i then disabled afterwards.
But i still didnt figure out what the problem is.

The regarding disk is sde1

But so sde1 is in wrong state if you read the bootinfo 

```
Windows is hibernated, refused to mount.
Failed to mount '/dev/sde1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
```

Alright i have run nftsfix /dev/sde1 but also os-probe doesnt see anything yet.

---

### Post by oldfred on 2016-02-14
If sde1 is Windows install, but when you installed it, you had another other drive set as default in BIOS, it would have installed its 100MB boot partition to that drive.

Copy /boot/BCD from sdc1 to sde1 and run Windows repairs on sde. Set BIOS to boot sde as default and run fixMBR or use Boot-Repair's advanced mode to choose an operating system and the drive to install boot loader into. Make sure fast start up is off if Windows 8 or later.

You want Windows boot loader in the MBR of sde, so you can directly boot sde.
You want grub in the MBR of sdd. And set default BIOS boot drive as sdd so you can use grub.

Grub normally installs to sda.
Windows normally installs its boot loader and a 100MB boot partition to drive set as default in BIOS, often sda, but not always.

---

### Post by Grouver on 2016-02-14
Well since Windows install broke the Linux install i used Gparted in live linux and removed an unknown partition and a nfts one on sdd2. I think Windows installed its stuff your talking about on sdd2 and broke linux which I then removed and now Windows wont start. 
I dont have any other partitions on sde1. How can I get this Windows boot partition back on the sde1?
I also removed /Boot/BCD since its from ages ago. I also fixed the problem Windows was in hibernate state and just did another boot-repair from live linux.

As you can see os-prober still wont find Windows 8.



New Bootinfo summary:

```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 81783949-8869-4da8-b3c1-1d81b50f3308 root hd3,msdos7 
    set prefix=($root)'/grub'
    
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 81783949-8869-4da8-b3c1-1d81b50f3308 root hd3,msdos7 
    set prefix=($root)'/grub'
    
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 81783949-8869-4da8-b3c1-1d81b50f3308 root hd3,msdos7 
    set prefix=($root)'/grub'
    
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/grub.
 => Grub2 (v2.00) is installed in the MBR of /dev/sde and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdd5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS 
    Boot files:        /etc/fstab

sdd6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdd7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/i386-pc/core.img

sdd8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdd9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048   625,137,663   625,135,616   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd2               2,048   250,066,943   250,064,896   5 Extended
/dev/sdd5           1,001,472    40,060,927    39,059,456  83 Linux
/dev/sdd6          40,062,976   137,717,759    97,654,784  83 Linux
/dev/sdd7    *    137,719,808   138,498,047       778,240  83 Linux
/dev/sdd8         138,500,096   197,091,327    58,591,232  83 Linux
/dev/sdd9         197,093,376   206,856,191     9,762,816  83 Linux


Drive: sde _____________________________________________________________________

Disk /dev/sde: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *          2,048   625,139,711   625,137,664   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7EEA5374EA5327A3                       ntfs       
/dev/sdb1        5254719E5471858F                       ntfs       
/dev/sdc1        A85EDA9D5EDA641A                       ntfs       
/dev/sdd5        8a8de9a5-b7af-4180-9e3f-45cbf2cca97c   ext4       
/dev/sdd6        4528d284-339a-49e4-95ec-696d231ae000   ext4       
/dev/sdd7        81783949-8869-4da8-b3c1-1d81b50f3308   ext4       
/dev/sdd8        7e308906-cb7e-4f5c-99bd-5de9d19e12d1   ext4       
/dev/sdd9        d2fb5918-ebe4-4a0b-894f-7f4cfc1437ab   ext4       
/dev/sde1        4C6E670B15FD24CD                       ntfs       
/dev/sr0                                                iso9660    Xubuntu 14.04.2 LTS amd64

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Feb 14 16:23 ata-Crucial_CT128M550SSD1_14200C23A767 -> ../../sdd
lrwxrwxrwx 1 root root 10 Feb 14  2016 ata-Crucial_CT128M550SSD1_14200C23A767-part2 -> ../../sdd2
lrwxrwxrwx 1 root root 10 Feb 14  2016 ata-Crucial_CT128M550SSD1_14200C23A767-part5 -> ../../sdd5
lrwxrwxrwx 1 root root 10 Feb 14  2016 ata-Crucial_CT128M550SSD1_14200C23A767-part6 -> ../../sdd6
lrwxrwxrwx 1 root root 10 Feb 14  2016 ata-Crucial_CT128M550SSD1_14200C23A767-part7 -> ../../sdd7
lrwxrwxrwx 1 root root 10 Feb 14  2016 ata-Crucial_CT128M550SSD1_14200C23A767-part8 -> ../../sdd8
lrwxrwxrwx 1 root root 10 Feb 14  2016 ata-Crucial_CT128M550SSD1_14200C23A767-part9 -> ../../sdd9
lrwxrwxrwx 1 root root  9 Feb 14 16:22 ata-Hitachi_HDT725032VLA360_VFK204R810A0JH -> ../../sdc
lrwxrwxrwx 1 root root 10 Feb 14 16:23 ata-Hitachi_HDT725032VLA360_VFK204R810A0JH-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Feb 14 16:22 ata-Hitachi_HDT725032VLA360_VFK204R81RABUH -> ../../sde
lrwxrwxrwx 1 root root 10 Feb 14 16:23 ata-Hitachi_HDT725032VLA360_VFK204R81RABUH-part1 -> ../../sde1
lrwxrwxrwx 1 root root  9 Feb 14  2016 ata-LITE-ON_DVDRW_LH-20A1S -> ../../sr0
lrwxrwxrwx 1 root root  9 Feb 14 16:22 ata-SAMSUNG_HD103UJ_S13PJ90QB39430 -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb 14 16:23 ata-SAMSUNG_HD103UJ_S13PJ90QB39430-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Feb 14 16:22 ata-ST1000DM005_HD103SJ_S246J9FC403485 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 14 16:23 ata-ST1000DM005_HD103SJ_S246J9FC403485-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 Feb 14 16:22 wwn-0x50000f000b3b4903 -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb 14 16:23 wwn-0x50000f000b3b4903-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Feb 14 16:22 wwn-0x50004cf2072d7fb8 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 14 16:23 wwn-0x50004cf2072d7fb8-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 Feb 14 16:22 wwn-0x5000cca317ce3d1b -> ../../sdc
lrwxrwxrwx 1 root root 10 Feb 14 16:23 wwn-0x5000cca317ce3d1b-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Feb 14 16:22 wwn-0x5000cca317d83ea3 -> ../../sde
lrwxrwxrwx 1 root root 10 Feb 14 16:23 wwn-0x5000cca317d83ea3-part1 -> ../../sde1
lrwxrwxrwx 1 root root  9 Feb 14 16:23 wwn-0x500a07510c23a767 -> ../../sdd
lrwxrwxrwx 1 root root 10 Feb 14  2016 wwn-0x500a07510c23a767-part2 -> ../../sdd2
lrwxrwxrwx 1 root root 10 Feb 14  2016 wwn-0x500a07510c23a767-part5 -> ../../sdd5
lrwxrwxrwx 1 root root 10 Feb 14  2016 wwn-0x500a07510c23a767-part6 -> ../../sdd6
lrwxrwxrwx 1 root root 10 Feb 14  2016 wwn-0x500a07510c23a767-part7 -> ../../sdd7
lrwxrwxrwx 1 root root 10 Feb 14  2016 wwn-0x500a07510c23a767-part8 -> ../../sdd8
lrwxrwxrwx 1 root root 10 Feb 14  2016 wwn-0x500a07510c23a767-part9 -> ../../sdd9

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sdd5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sde5 during installation
UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sde7 during installation
#UUID=81783949-8869-4da8-b3c1-1d81b50f3308 /boot           ext4    defaults        0       2
# /home was on /dev/sde6 during installation
UUID=4528d284-339a-49e4-95ec-696d231ae000 /home           ext4    defaults        0       2
# /tmp was on /dev/sde9 during installation
UUID=d2fb5918-ebe4-4a0b-894f-7f4cfc1437ab /tmp            ext4    defaults        0       2
# /var was on /dev/sde8 during installation
UUID=7e308906-cb7e-4f5c-99bd-5de9d19e12d1 /var            ext4    defaults        0       2
# swap was on /dev/sde1 during installation
#UUID=75f0cc46-7b82-4ddb-9878-e732bb3482ea none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
#automount of all disks
UUID=7EEA5374EA5327A3 /media/roy/U/ ntfs-3g uid=1000,gid=1000,defaults
UUID=5254719E5471858F /media/roy/B/ ntfs-3g uid=1000,gid=1000,defaults
UUID=A85EDA9D5EDA641A /media/roy/D/ ntfs-3g uid=1000,gid=1000,defaults
UUID=4C6E670B15FD24CD /media/roy/C/ ntfs-3g uid=1000,gid=1000,defaults
UUID=81783949-8869-4da8-b3c1-1d81b50f3308    /boot    ext4    defaults    0    2
--------------------------------------------------------------------------------

============================= sdd7/grub/grub.cfg: ==============================

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
set root='hd3,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos5 --hint-efi=hd3,msdos5 --hint-baremetal=ahci3,msdos5  8a8de9a5-b7af-4180-9e3f-45cbf2cca97c
else
  search --no-floppy --fs-uuid --set=root 8a8de9a5-b7af-4180-9e3f-45cbf2cca97c
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd3,msdos7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
    else
      search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
    fi
    linux    /vmlinuz-3.16.0-61-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro  quiet splash acpi=force $vt_handoff
    initrd    /initrd.img-3.16.0-61-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
    menuentry 'Ubuntu, with Linux 3.16.0-61-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-61-generic-advanced-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd3,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
        else
          search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
        fi
        echo    'Loading Linux 3.16.0-61-generic ...'
        linux    /vmlinuz-3.16.0-61-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro  quiet splash acpi=force $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.16.0-61-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-61-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-61-generic-recovery-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd3,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
        else
          search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
        fi
        echo    'Loading Linux 3.16.0-61-generic ...'
        linux    /vmlinuz-3.16.0-61-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.16.0-61-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-60-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-60-generic-advanced-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd3,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
        else
          search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
        fi
        echo    'Loading Linux 3.16.0-60-generic ...'
        linux    /vmlinuz-3.16.0-60-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro  quiet splash acpi=force $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.16.0-60-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-60-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-60-generic-recovery-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd3,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
        else
          search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
        fi
        echo    'Loading Linux 3.16.0-60-generic ...'
        linux    /vmlinuz-3.16.0-60-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.16.0-60-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-58-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-58-generic-advanced-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd3,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
        else
          search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
        fi
        echo    'Loading Linux 3.16.0-58-generic ...'
        linux    /vmlinuz-3.16.0-58-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro  quiet splash acpi=force $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.16.0-58-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-58-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-58-generic-recovery-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd3,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
        else
          search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
        fi
        echo    'Loading Linux 3.16.0-58-generic ...'
        linux    /vmlinuz-3.16.0-58-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.16.0-58-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-57-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-57-generic-advanced-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd3,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
        else
          search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
        fi
        echo    'Loading Linux 3.16.0-57-generic ...'
        linux    /vmlinuz-3.16.0-57-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro  quiet splash acpi=force $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.16.0-57-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-57-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-57-generic-recovery-8a8de9a5-b7af-4180-9e3f-45cbf2cca97c' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd3,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos7 --hint-efi=hd3,msdos7 --hint-baremetal=ahci3,msdos7  81783949-8869-4da8-b3c1-1d81b50f3308
        else
          search --no-floppy --fs-uuid --set=root 81783949-8869-4da8-b3c1-1d81b50f3308
        fi
        echo    'Loading Linux 3.16.0-57-generic ...'
        linux    /vmlinuz-3.16.0-57-generic root=UUID=8a8de9a5-b7af-4180-9e3f-45cbf2cca97c ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.16.0-57-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
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

=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
cat: write error: Broken pipe
cat: write error: Broken pipe
cat: write error: Broken pipe
cat: write error: Broken pipe
File descriptor 9 (/proc/24546/mounts) leaked on lvs invocation. Parent PID 11528: bash
File descriptor 63 (pipe:[58741]) leaked on lvs invocation. Parent PID 11528: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-02-14__16h21 ===================
boot-repair version : 4ppa35
boot-sav version : 4ppa35
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa35
boot-repair is executed in live-session (Ubuntu 14.04.2 LTS, trusty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash --
ls: cannot access /home/usr/.config: No such file or directory

=================== os-prober:
/dev/sdd5:Ubuntu 14.04.3 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="7EEA5374EA5327A3" TYPE="ntfs"
/dev/sdb1: UUID="5254719E5471858F" TYPE="ntfs"
/dev/sdc1: UUID="A85EDA9D5EDA641A" TYPE="ntfs"
/dev/sdd5: UUID="8a8de9a5-b7af-4180-9e3f-45cbf2cca97c" TYPE="ext4"
/dev/sdd6: UUID="4528d284-339a-49e4-95ec-696d231ae000" TYPE="ext4"
/dev/sdd7: UUID="81783949-8869-4da8-b3c1-1d81b50f3308" TYPE="ext4"
/dev/sdd8: UUID="7e308906-cb7e-4f5c-99bd-5de9d19e12d1" TYPE="ext4"
/dev/sdd9: UUID="d2fb5918-ebe4-4a0b-894f-7f4cfc1437ab" TYPE="ext4"
/dev/sr0: LABEL="Xubuntu 14.04.2 LTS amd64" TYPE="iso9660"
/dev/sde1: UUID="4C6E670B15FD24CD" TYPE="ntfs"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Windows not detected by os-prober on sde1.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== sdd5/etc/grub.d/ :
drwxr-xr-x  2 root root      4096 Jan  6 17:59 grub.d
total 76
-rwxr-xr-x 1 root root  9791 Dec 17 15:00 00_header
-rwxr-xr-x 1 root root  6058 May  8  2014 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15  2014 10_linux
-rwxr-xr-x 1 root root 10412 May 15  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 May 15  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15  2014 40_custom
-rwxr-xr-x 1 root root   216 May 15  2014 41_custom
-rw-r--r-- 1 root root   483 May 15  2014 README




=================== sdd5/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
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



/boot detected in the fstab of sdd5: UUID=81783949-8869-4da8-b3c1-1d81b50f3308     (sdd7)

=================== efibootmgr -v
BootCurrent: 0009
Timeout: 1 seconds
BootOrder: 0009,0005,0002,0001,0006,0007,0008
Boot0001* LITE-ON DVDRW LH-20A1S    BIOS(3,0,00)AMBO
Boot0002* Crucial_CT128M550SSD1    BIOS(2,0,00)AMBO
Boot0005* Hitachi HDT725032VLA360    BIOS(2,0,00)AMBO
Boot0006* ST1000DM005 HD103SJ    BIOS(2,0,00)AMBO
Boot0007* SAMSUNG HD103UJ    BIOS(2,0,00)AMBO
Boot0008* Hitachi HDT725032VLA360    BIOS(2,0,00)AMBO
Boot0009* UEFI: LITE-ON DVDRW LH-20A1S    ACPI(a0341d0,0)PCI(1f,2)03120a000400ffff0000CD-ROM(1,71adc,1240)AMBO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb1.
sdc1    : sdc,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdc1.
sdd5    : sdd,    not-sepboot,    no-grubenv    grub2,    grub-pc ,    update-grub,    64,    no-boot,    is-os,    not--efi--part,    fstab-has-goodBOOT,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdd5.
sdd6    : sdd,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdd6.
sdd7    : sdd,    is-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdd7.
sdd8    : sdd,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdd8.
sdd9    : sdd,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdd9.
sde1    : sde,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sde1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes
sdc    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes
sdd    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sde    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA ST1000DM005 HD10 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  1000GB  1000GB  primary  ntfs


Model: ATA SAMSUNG HD103UJ (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  1000GB  1000GB  primary  ntfs


Model: ATA Hitachi HDT72503 (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  320GB  320GB  primary  ntfs


Model: ATA Crucial_CT128M55 (scsi)
Disk /dev/sdd: 128GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
2      1049kB  128GB   128GB   extended
5      513MB   20.5GB  20.0GB  logical   ext4
6      20.5GB  70.5GB  50.0GB  logical   ext4
7      70.5GB  70.9GB  398MB   logical   ext4         boot
8      70.9GB  101GB   30.0GB  logical   ext4
9      101GB   106GB   4999MB  logical   ext4


Model: ATA Hitachi HDT72503 (scsi)
Disk /dev/sde: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  320GB  320GB  primary  ntfs         boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: Can't have a partition outside the disk!

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:512:msdos:ATA ST1000DM005 HD10;
1:1049kB:1000GB:1000GB:ntfs::;

BYT;
/dev/sdb:1000GB:scsi:512:512:msdos:ATA SAMSUNG HD103UJ;
1:1049kB:1000GB:1000GB:ntfs::;

BYT;
/dev/sdc:320GB:scsi:512:512:msdos:ATA Hitachi HDT72503;
1:1049kB:320GB:320GB:ntfs::;

BYT;
/dev/sdd:128GB:scsi:512:4096:msdos:ATA Crucial_CT128M55;
2:1049kB:128GB:128GB:::;
5:513MB:20.5GB:20.0GB:ext4::;
6:20.5GB:70.5GB:50.0GB:ext4::;
7:70.5GB:70.9GB:398MB:ext4::boot;
8:70.9GB:101GB:30.0GB:ext4::;
9:101GB:106GB:4999MB:ext4::;

BYT;
/dev/sde:320GB:scsi:512:512:msdos:ATA Hitachi HDT72503;
1:1049kB:320GB:320GB:ntfs::boot;

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: Can't have a partition outside the disk!

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sda   disk          931.5G
sda1  part ntfs     931.5G
sdb   disk          931.5G
sdb1  part ntfs     931.5G
sdc   disk          298.1G
sdc1  part ntfs     298.1G
sdd   disk          119.2G
sdd2  part              1K
sdd5  part ext4      18.6G
sdd6  part ext4      46.6G
sdd7  part ext4       380M
sdd8  part ext4        28G
sdd9  part ext4       4.7G
sde   disk          298.1G
sde1  part ntfs     298.1G
sr0   rom  iso9660    943M Xubuntu 14.04.2 LTS amd64
loop0 loop squashfs 902.5M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sdb      1  0  0 running
sdb1     1  0  0         /mnt/boot-sav/sdb1
sdc      1  0  0 running
sdc1     1  0  0         /mnt/boot-sav/sdc1
sdd      0  0  0 running
sdd2     0  0  0
sdd5     0  0  0         /mnt/boot-sav/sdd5
sdd6     0  0  0         /mnt/boot-sav/sdd6
sdd7     0  0  0         /mnt/boot-sav/sdd7
sdd8     0  0  0         /mnt/boot-sav/sdd8
sdd9     0  0  0         /mnt/boot-sav/sdd9
sde      1  0  0 running
sde1     1  0  0         /mnt/boot-sav/sde1
sr0      1  0  1 running /cdrom
loop0    1  1  0         /rofs


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=xubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdd5 on /mnt/boot-sav/sdd5 type ext4 (rw)
/dev/sdd6 on /mnt/boot-sav/sdd6 type ext4 (rw)
/dev/sdd7 on /mnt/boot-sav/sdd7 type ext4 (rw)
/dev/sdd8 on /mnt/boot-sav/sdd8 type ext4 (rw)
/dev/sdd9 on /mnt/boot-sav/sdd9 type ext4 (rw)
/dev/sde1 on /mnt/boot-sav/sde1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdd2 sdd5 sdd6 sdd7 sdd8 sdd9 size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sde1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hidraw3 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdc sdc1 sdd sdd2 sdd5 sdd6 sdd7 sdd8 sdd9 sde sde1 sg0 sg1 sg2 sg3 sg4 sg5 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 57 70 74 00 00 00 00  |.........Wpt....|
00000030  00 00 0c 00 00 00 00 00  7f 05 47 07 00 00 00 00  |..........G.....|
00000040  f6 00 00 00 01 00 00 00  a3 27 53 ea 74 53 ea 7e  |.........'S.tS.~|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 57 70 74 00 00 00 00  |.........Wpt....|
00000030  00 00 0c 00 00 00 00 00  7f 05 47 07 00 00 00 00  |..........G.....|
00000040  f6 00 00 00 01 00 00 00  8f 85 71 54 9e 71 54 52  |..........qT.qTR|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 53 63 68 69 6a 66  66 6f 75 74 00 0d 0a 62  |..Schijffout...b|
00000190  6f 6f 74 6d 67 72 20 6f  6e 74 62 72 65 65 6b 74  |ootmgr ontbreekt|
000001a0  00 0d 0a 62 6f 6f 74 6d  67 72 20 67 65 63 6f 6d  |...bootmgr gecom|
000001b0  70 72 69 6d 65 65 72 64  00 0d 0a 44 72 75 6b 20  |primeerd...Druk |
000001c0  43 74 72 6c 2b 41 6c 74  2b 44 65 6c 65 74 65 20  |Ctrl+Alt+Delete |
000001d0  6f 6d 20 6f 70 6e 69 65  75 77 20 74 65 20 73 74  |om opnieuw te st|
000001e0  61 72 74 65 6e 0d 0a 00  74 0d 0a 00 00 00 00 00  |arten...t.......|
000001f0  00 00 00 00 00 00 00 00  80 8d a1 b9 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdc1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff cf 42 25 00 00 00 00  |..........B%....|
00000030  00 00 0c 00 00 00 00 00  ff 2c 54 02 00 00 00 00  |.........,T.....|
00000040  f6 00 00 00 01 00 00 00  1a 64 da 5e 9d da 5e a8  |.........d.^..^.|
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

=================== hexdump -n512 -C /dev/sde1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff d7 42 25 00 00 00 00  |..........B%....|
00000030  04 00 00 00 00 00 00 00  7f 2d 54 02 00 00 00 00  |.........-T.....|
00000040  f6 00 00 00 01 00 00 00  cd 24 fd 15 0b 67 6e 4c  |.........$...gnL|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.4G  214M  3.2G   7% /
udev           devtmpfs   3.4G   12K  3.4G   1% /dev
tmpfs          tmpfs      692M  1.4M  691M   1% /run
/dev/sr0       iso9660    943M  943M     0 100% /cdrom
/dev/loop0     squashfs   903M  903M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.4G  648K  3.4G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      3.4G   80K  3.4G   1% /run/shm
none           tmpfs      100M   24K  100M   1% /run/user
/dev/sda1      fuseblk    932G  572G  360G  62% /mnt/boot-sav/sda1
/dev/sdb1      fuseblk    932G  767G  166G  83% /mnt/boot-sav/sdb1
/dev/sdc1      fuseblk    299G  261G   38G  88% /mnt/boot-sav/sdc1
/dev/sdd5      ext4        19G  7.3G   10G  43% /mnt/boot-sav/sdd5
/dev/sdd6      ext4        46G   12G   32G  27% /mnt/boot-sav/sdd6
/dev/sdd7      ext4       360M  167M  171M  50% /mnt/boot-sav/sdd7
/dev/sdd8      ext4        28G  2.2G   24G   9% /mnt/boot-sav/sdd8
/dev/sdd9      ext4       4.5G  9.4M  4.2G   1% /mnt/boot-sav/sdd9
/dev/sde1      fuseblk    299G   11G  288G   4% /mnt/boot-sav/sde1

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x060d0904

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74975362

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcacc81c6

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   625137663   312567808    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000e8f33

Device Boot      Start         End      Blocks   Id  System
/dev/sdd2            2048   250066943   125032448    5  Extended
/dev/sdd5         1001472    40060927    19529728   83  Linux
/dev/sdd6        40062976   137717759    48827392   83  Linux
/dev/sdd7   *   137719808   138498047      389120   83  Linux
/dev/sdd8       138500096   197091327    29295616   83  Linux
/dev/sdd9       197093376   206856191     4881408   83  Linux

Disk /dev/sde: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xadfbdd4f

Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048   625139711   312568832    7  HPFS/NTFS/exFAT


/boot detected. Please check the options.
Partition outside the disk detected.
Partition outside the disk detected.

=================== Recommended repair
The default repair of the Boot-Repair utility will reinstall the grub2 of sdd5 into the MBRs of all disks (except USB without OS), using the following options:        sdd7/boot,
The boot flag will be placed on sde1.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 1
WinSE in sde1
/mnt/boot-sav/sde1/ may need repair.
Mount sdd7 on /mnt/boot-sav/sdd5/boot

Reinstall the GRUB of sdd5 into all MBRs of disks with OS or not-USB

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1.7,grub-install (GRUB) 2.

Reinstall the GRUB of sdd5 into the MBR of sda
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1.7,grub-install (GRUB) 2.

Reinstall the GRUB of sdd5 into the MBR of sdb
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdb: exit code of grub-install /dev/sdb:0

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1.7,grub-install (GRUB) 2.

Reinstall the GRUB of sdd5 into the MBR of sdc
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdc: exit code of grub-install /dev/sdc:0

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1.7,grub-install (GRUB) 2.

Reinstall the GRUB of sdd5 into the MBR of sde
Installing for i386-pc platform.
grub-install: warning: Sector 32 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
grub-install: warning: Sector 33 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.
grub-install /dev/sde: exit code of grub-install /dev/sde:0

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1.7,grub-install (GRUB) 2.

Reinstall the GRUB of sdd5 into the MBR of sdd
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdd: exit code of grub-install /dev/sdd:0

chroot /mnt/boot-sav/sdd5 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-61-generic
Found initrd image: /boot/initrd.img-3.16.0-61-generic
Found linux image: /boot/vmlinuz-3.16.0-60-generic
Found initrd image: /boot/initrd.img-3.16.0-60-generic
Found linux image: /boot/vmlinuz-3.16.0-58-generic
Found initrd image: /boot/initrd.img-3.16.0-58-generic
Found linux image: /boot/vmlinuz-3.16.0-57-generic
Found initrd image: /boot/initrd.img-3.16.0-57-generic
mkdir: cannot create directory '/var/lib/os-prober/mount': No such file or directory
Adding boot menu entry for EFI firmware configuration

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdd (128GB) disk!

```

---

### Post by oldfred on 2016-02-14
You have to create a /Boot/BCD on your Windows partition.

Windows normally installs to two partitions, the 100MB boot and main install. But can be installed to just one. Or the one main partition can be repaired to include both bootmgr & BCD, so it can be booted without separate boot partition. Since boot partition is separate it often lets you use f8 to get into repair functions on main partition. So make a Windows repair CD or flash drive as soon as you get it working.

If you have a Windows repair disk or installer disk, go into repair console and run the full set of repairs. If using auto fix you have to run it 3 times. Be sure to have BIOS set to sde as default boot before running any repairs. Otherwise it may corrupt other drives.

If you do not have a repair disk,  you can down load third party tools to create a new BCD.
 BCDboot Command-Line Options Windows Vista/7/8 recreates boot files.
[http://technet.microsoft.com/en-GB/library/hh824874.aspx](http://technet.microsoft.com/en-GB/library/hh824874.aspx)

 Repair BCD - not recommended for dual booting, just Windows repairs
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

---

### Post by Grouver on 2016-02-14
Alright I have set sde as first boot device after my optic drive and runned the Startup Repair from my installation disk 3 times. After I removed the Windows installation disk it still booted into GRUB and not in to the primary drive which contains Windows.
Also os-prober doesnt find Windows.

Do you reccomend to use the BCDboot otherwise now?

---

### Post by oldfred on 2016-02-14
I do not know details of Windows repairs anymore.

But you have to have bootmgr, BCD, boot flag, NTFS primary partition and BIOS set to boot from that drive for Windows to work. May also need chkdsk as well as fixMBR and fixBoot.

---

### Post by Grouver on 2016-02-14
What about if I just unhook all harddisks except sde1  and reinstall Windows on that one? Than the installer is forced to put its boot stuff onto that one disk.
After that I just plug all drives in again and os-prober should detect it.

---

### Post by oldfred on 2016-02-14
That should work.
Or you could just have Windows drive plugged in and run repairs on Windows.

Best to then keep Windows plugged into SATA port 0 or first SATA port. And have DVD last.
Ubuntu is not as concerned about drive order, as it uses UUID for most things. But if a command in grub or Ubuntu uses hd? or sd? then you need to pay attention to which drive is which.

---

