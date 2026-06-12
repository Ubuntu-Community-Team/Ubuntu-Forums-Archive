---
title: "Dual Boot lost GRUB2 menu"
date: 2019-07-13
forum: General Help
---

### Post by Olivares on 2019-07-13
I uninstalled - reinstalled Ubuntu 18.04 yesterday. This is dual boot with Windows 8.1. I have been unable to reinstate the GRUB 2 menu. When I run the Boot Repair utility, the GRUB tab is greyed out. I attach the output from running the Boot Info script.

I hope somebody can help.

---

### Post by uRock on 2019-07-13
To save people the hassle of downloading the file, here's the data from within;
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  The info in boot sector on the starting sector of the 
                       MFT is wrong. The info in the boot sector on the 
                       starting sector of the MFT Mirror is wrong.
    Operating System:  
    Boot files:        

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
    Boot files:        /bootmgr /Windows/System32/winload.exe

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdb5 
                       and looks at sector 1739221968 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 85 for .
    Operating System:  Ubuntu 18.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 1.8 TiB, 2000398929920 bytes, 488378645 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   488,378,644   488,376,597   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048       718,847       716,800   7 NTFS / exFAT / HPFS
/dev/sdb2             718,848 1,033,925,167 1,033,206,320   7 NTFS / exFAT / HPFS
/dev/sdb3       1,033,926,654 1,953,523,711   919,597,058   5 Extended
/dev/sdb5    *  1,033,926,656 1,953,523,711   919,597,056  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop10                                             squashfs   
/dev/loop11                                             squashfs   
/dev/loop12                                             squashfs   
/dev/loop13                                             squashfs   
/dev/loop14                                             squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/loop8                                              squashfs   
/dev/loop9                                              squashfs   
/dev/sda1        7A5E8C785E8C2F47                       ntfs       Seagate Backup Plus Drive
/dev/sdb1        8AB0215FB021534D                       ntfs       System Reserved
/dev/sdb2        C60423FE0423EFDB                       ntfs       
/dev/sdb5        68341cbb-f7b1-4938-a482-e0226c65af12   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/barry/Seagate Backup Plus Drive fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sdb5        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='hd1,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  68341cbb-f7b1-4938-a482-e0226c65af12
else
  search --no-floppy --fs-uuid --set=root 68341cbb-f7b1-4938-a482-e0226c65af12
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_NZ
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
		set vt_handoff=vt.handoff=1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-68341cbb-f7b1-4938-a482-e0226c65af12' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  68341cbb-f7b1-4938-a482-e0226c65af12
	else
	  search --no-floppy --fs-uuid --set=root 68341cbb-f7b1-4938-a482-e0226c65af12
	fi
        linux	/boot/vmlinuz-4.15.0-54-generic root=UUID=68341cbb-f7b1-4938-a482-e0226c65af12 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-4.15.0-54-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-68341cbb-f7b1-4938-a482-e0226c65af12' {
	menuentry 'Ubuntu, with Linux 4.15.0-54-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-54-generic-advanced-68341cbb-f7b1-4938-a482-e0226c65af12' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  68341cbb-f7b1-4938-a482-e0226c65af12
		else
		  search --no-floppy --fs-uuid --set=root 68341cbb-f7b1-4938-a482-e0226c65af12
		fi
		echo	'Loading Linux 4.15.0-54-generic ...'
	        linux	/boot/vmlinuz-4.15.0-54-generic root=UUID=68341cbb-f7b1-4938-a482-e0226c65af12 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-54-generic
	}
	menuentry 'Ubuntu, with Linux 4.15.0-54-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-54-generic-recovery-68341cbb-f7b1-4938-a482-e0226c65af12' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  68341cbb-f7b1-4938-a482-e0226c65af12
		else
		  search --no-floppy --fs-uuid --set=root 68341cbb-f7b1-4938-a482-e0226c65af12
		fi
		echo	'Loading Linux 4.15.0-54-generic ...'
	        linux	/boot/vmlinuz-4.15.0-54-generic root=UUID=68341cbb-f7b1-4938-a482-e0226c65af12 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-54-generic
	}
	menuentry 'Ubuntu, with Linux 4.15.0-20-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-20-generic-advanced-68341cbb-f7b1-4938-a482-e0226c65af12' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  68341cbb-f7b1-4938-a482-e0226c65af12
		else
		  search --no-floppy --fs-uuid --set=root 68341cbb-f7b1-4938-a482-e0226c65af12
		fi
		echo	'Loading Linux 4.15.0-20-generic ...'
	        linux	/boot/vmlinuz-4.15.0-20-generic root=UUID=68341cbb-f7b1-4938-a482-e0226c65af12 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-20-generic
	}
	menuentry 'Ubuntu, with Linux 4.15.0-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-20-generic-recovery-68341cbb-f7b1-4938-a482-e0226c65af12' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  68341cbb-f7b1-4938-a482-e0226c65af12
		else
		  search --no-floppy --fs-uuid --set=root 68341cbb-f7b1-4938-a482-e0226c65af12
		fi
		echo	'Loading Linux 4.15.0-20-generic ...'
	        linux	/boot/vmlinuz-4.15.0-20-generic root=UUID=68341cbb-f7b1-4938-a482-e0226c65af12 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-20-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  68341cbb-f7b1-4938-a482-e0226c65af12
	else
	  search --no-floppy --fs-uuid --set=root 68341cbb-f7b1-4938-a482-e0226c65af12
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  68341cbb-f7b1-4938-a482-e0226c65af12
	else
	  search --no-floppy --fs-uuid --set=root 68341cbb-f7b1-4938-a482-e0226c65af12
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 8 (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-8AB0215FB021534D' {
	insmod part_msdos
	insmod ntfs
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  8AB0215FB021534D
	else
	  search --no-floppy --fs-uuid --set=root 8AB0215FB021534D
	fi
	parttool ${root} hidden-
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
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=68341cbb-f7b1-4938-a482-e0226c65af12 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

MFT Sector of sda1

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ed ea e1 ff  |................|
00000010  9c 8c 6a ff 7e 6b 3f ff  6a 57 2d ff 59 48 20 ff  |..j.~k?.jW-.YH .|
00000020  4f 3d 16 ff 4a 39 13 ff  4a 38 12 ff 4b 39 14 ff  |O=..J9..J8..K9..|
00000030  50 3e 19 ff 58 45 1f ff  5f 4c 26 ff 63 50 2a ff  |P>..XE.._L&.cP*.|
00000040  64 51 2b ff 64 51 2b ff  61 4e 28 ff 61 4e 29 ff  |dQ+.dQ+.aN(.aN).|
00000050  60 4e 29 ff 60 4e 29 ff  77 67 46 ff a2 93 74 ff  |`N).`N).wgF...t.|
00000060  87 78 52 ff 65 54 2c ff  4d 3d 18 ff 3e 2f 10 ff  |.xR.eT,.M=..>/..|
00000070  37 2a 0f ff 31 26 0e ff  30 24 0d ff 32 26 0f ff  |7*..1&..0$..2&..|
00000080  32 2b 1c ff 20 2d 3a ff  1a 2d 40 ff 28 37 4e ff  |2+.. -:..-@.(7N.|
00000090  4e 63 84 ff 7b 94 c2 ff  8e a7 dc ff 94 ac e0 ff  |Nc..{...........|
000000a0  91 aa dc ff 8e aa de ff  82 a0 d7 ff 74 93 cf ff  |............t...|
000000b0  76 97 d2 ff 79 9b d2 ff  77 98 cd ff 76 95 ca ff  |v...y...w...v...|
000000c0  7c 99 cf ff 84 a0 d5 ff  89 a4 d9 ff 8d aa e0 ff  ||...............|
000000d0  93 b0 e7 ff a3 c1 f8 ff  a9 c6 fb ff ac c7 fc ff  |................|
000000e0  a6 c5 fb ff a5 c4 f9 ff  9f bc f4 ff 9e bb f3 ff  |................|
000000f0  97 b4 eb ff 8e ab e2 ff  8e aa e1 ff 92 af e5 ff  |................|
00000100  8d ac e3 ff 84 a4 de ff  7b 9a d6 ff 7a 98 d1 ff  |........{...z...|
00000110  87 a5 db ff 8c a8 dc ff  8b a8 e0 ff 7a 99 d0 ff  |............z...|
00000120  4b 64 8e ff 20 33 4e ff  1a 2d 43 ff 1e 25 30 ff  |Kd.. 3N..-C..%0.|
00000130  50 46 34 ff 69 58 34 ff  7a 6a 49 ff 9e 90 72 ff  |PF4.iX4.zjI...r.|
00000140  a6 99 7e ff a3 97 7e ff  b0 a4 89 ff a2 94 72 ff  |..~...~.......r.|
00000150  7c 6b 42 ff 5a 4a 22 ff  45 36 16 ff 47 3a 21 ff  ||kB.ZJ".E6..G:!.|
00000160  65 56 38 ff 72 60 40 ff  72 61 40 ff 76 65 44 ff  |eV8.r`@.ra@.veD.|
00000170  80 71 50 ff 9e 92 74 ff  ae a1 88 ff a6 98 7a ff  |.qP...t.......z.|
00000180  7f 6e 48 ff 5f 4e 24 ff  70 66 4d ff ce cf cb ff  |.nH._N$.pfM.....|
00000190  d6 da d9 ff cb cf cf ff  ba c0 c0 ff 9b a1 a2 ff  |................|
000001a0  61 63 6b ff 2d 2f 3b ff  1e 25 3b ff 26 33 51 ff  |ack.-/;..%;.&3Q.|
000001b0  27 36 59 ff 29 3d 66 ff  28 3e 70 ff 43 61 9b ff  |'6Y.)=f.(>p.Ca..|
000001c0  5c 7c b7 ff 57 70 ae ff  70 8e cd ff 71 90 d0 ff  |\|..Wp..p...q...|
000001d0  72 8f cf ff 67 83 c4 ff  68 86 c8 ff 5d 7d c1 ff  |r...g...h...]}..|
000001e0  4b 6c b2 ff 4e 71 b7 ff  50 72 b7 ff 47 64 9d ff  |Kl..Nq..Pr..Gd..|
000001f0  2e 46 74 ff 3b 4f 81 ff  2d 3e 6b ff 1a 26 44 ff  |.Ft.;O..->k..&D.|
00000200
Unknown BootLoader on sdb3

00000000  fb 60 02 eb f0 27 71 e4  40 07 64 4c 16 2f db 7b  |.`...'q.@.dL./.{|
00000010  7a 53 13 83 5d 4f a1 8d  f2 90 02 10 04 80 0c 48  |zS..]O.........H|
00000020  df 5f 7f 82 20 90 07 c0  07 e2 ba 17 d5 ce f1 36  |._.. ..........6|
00000030  d5 ca 85 37 ea 20 40 fa  b7 00 2e f6 04 3f fa af  |...7. @......?..|
00000040  fe e0 ae 39 de 9f 1c a6  81 8f 38 73 7c a4 10 3e  |...9......8s|..>|
00000050  e4 00 c3 7d b9 ef a7 0a  00 77 f4 c1 6f e2 f3 77  |...}.....w..o..w|
00000060  8e ec b9 c3 d3 47 53 b2  b7 92 47 86 37 b2 44 d3  |.....GS...G.7.D.|
00000070  71 bf e7 2f ef 4f e3 de  b8 57 b9 18 4f 5b ae ec  |q../.O...W..O[..|
00000080  43 b5 f0 6e 56 e5 77 a2  b2 01 9c d5 90 3c a1 88  |C..nV.w......<..|
00000090  df 63 04 0f cb 00 30 00  52 e0 0a c4 48 00 fb 6e  |.c....0.R...H..n|
000000a0  4e 78 ef ce cb 0a b9 6c  2e 37 ca 88 f5 fe c2 71  |Nx.....l.7.....q|
000000b0  fd 09 f8 ed d6 b9 fd 6e  2a ac 43 2b 70 f3 96 37  |.......n*.C+p..7|
000000c0  ac ed 97 0b 8d fc de fc  2a 6c a9 a1 a3 43 5b 53  |........*l...C[S|
000000d0  c5 48 ec a7 d0 b1 ad ce  e5 c2 03 ad 9b 94 f5 08  |.H..............|
000000e0  0a 6e 88 bc cc 45 92 16  5c 56 e3 a5 37 4d 6e b3  |.n...E..\V..7Mn.|
000000f0  84 d9 50 26 12 db 3f 22  8a 40 e8 1a 8d a1 fc 3b  |..P&..?".@.....;|
00000100  2c 36 61 49 0f a3 46 b5  02 dd 24 49 eb 07 b4 d6  |,6aI..F...$I....|
00000110  6d 92 53 6d 32 ec 38 b6  a6 d8 61 63 48 6d e8 08  |m.Sm2.8...acHm..|
00000120  fc cb 21 55 47 17 4e 6e  77 65 72 87 06 86 32 ac  |..!UG.Nnwer...2.|
00000130  2b 6c 3c fe 1f 7d 52 c2  87 33 98 ab 0a 1e 12 73  |+l<..}R..3.....s|
00000140  19 7f 05 58 72 9c 51 cd  65 c0 e5 9e 91 6d 52 da  |...Xr.Q.e....mR.|
00000150  99 37 ca ae f3 b3 0f 87  a2 22 c0 86 b3 89 3c ad  |.7......."....<.|
00000160  29 06 20 48 14 c8 f2 df  4c 40 11 48 50 4a b3 79  |). H....L@.HPJ.y|
00000170  6a 69 79 4e 49 61 61 a4  a6 a6 4d f6 14 a1 d1 86  |jiyNIaa...M.....|
00000180  4b b0 9a f0 8b 03 40 e6  ad c6 57 93 02 c3 51 ad  |K.....@...W...Q.|
00000190  e9 d9 b1 56 e9 56 2e c2  8a 3d 9b 53 7d b2 25 a6  |...V.V...=.S}.%.|
000001a0  4d 40 d8 7a 85 b2 3b 77  76 d5 09 0c 53 99 a4 ca  |M@.z..;wv...S...|
000001b0  a5 2d 1e 55 2d 95 d9 f9  2a 5a 4a 6c 98 6e 80 fe  |.-.U-...*ZJl.n..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 f0 cf 36 00 00  |.............6..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-z9BIn21o/Tmp_Log: No such file or directory

```

---

### Post by oldfred on 2019-07-13
It looks like you had an unusual configuration.

Windows uses a Windows boot loader in MBR to find partition with boot flag & has more boot code to boot from partition with boot flag.

Grub2 has code in MBR (and sectors just after MBR - core.img) to find partition with rest of grub.
Grub2 does not recommend installing to a partition PBR or BS - boot sector as it does not really fit, and has to use unreliable blocklists.

It looks like you installed grub to PBR of Linux partition and then used an open source Windows type boot loader (syslinux) to use boot flag to know which partition to boot from. And you have boot flag on Linux partition. 

Boot flag should be on sdb1 for Windows boot. Windows boot loader needs to be on same drive as Windows.
Only because you have two drives you can install grub to MBR of sda & set sda as default boot. Then grub will offer to boot Windows. Grub only boots working Windows or Windows that is not hibernated/fast start up on.

But Windows 8 or 10 turns on fast start up with updates & then grub will not boot it. But then you also can change boot order in BIOS from sda to sdb to directly boot Windows & turn off fast start up or make other Windows repairs. And then change boot back to sda to dual boot.

So move boot flag from sdb5 to sdb2, Windows boot partition with gparted or Windows repair flash drive. Windows should then boot ok, and check fast start up is off.

Install grub to MBR of sda to boot install on sdb5 and then set BIOS to boot sda. Probably easier to use Boot-Repair and its advanced mode to select install (sdb5) & drive(sda) to install grub. Do not run auto fix as that will want to install grub to both drives, and you need to keep the Windows boot loader on the sdb drive.

        [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[URL="https://sourceforge.net/p/boot-repair/home/Home/"]https://sourceforge.net/p/boot-repair/home/Home/

      [/URL] Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 
    [URL="https://sourceforge.net/p/boot-repair/home/Home/"]
[/URL]

---

### Post by Olivares on 2019-07-13
I have followed steps you have outlined, but not sure I understand setting boot order in BIOS.
My ASRock UEFI setup shows the following: 
Boot option 1: SATA HL - DT - ST DVDRAM
Boot option 2: UEFI: Built-in EFI Shell
Boot option 3: AHCI PO: ST1000 DM003-1CH162
Boot option 4: Disabled.

Is this correct?

Updated boot info summary is here: [http://paste.ubuntu.com/p/bZ9Gk3NbhV/](http://paste.ubuntu.com/p/bZ9Gk3NbhV/)

---

### Post by oldfred on 2019-07-13
With UEFI hardware better to use UEFI, but you have installed in the older BIOS/MBR configuration. 
Do not know details of Asrock settings, but with most systems you need to have UEFI off, CSM/Legacy/BIOS mode on, and allow USB boot on.

Is sda an external drive that go promoted to sda? You only seem to show the ST1000 drive as boot option.
Do you have grub installed to sda, it would not show in BIOS boot options unless it can see a boot loader?

---

### Post by Olivares on 2019-07-14
The problem is now fixed, and the solution was quite simple. Using GRUB Customizer, check the line 'GRUB GFX Mode'.  The menu is now visible. 
Thank you for your interest and the effort you put into responding.

---

### Post by oldfred on 2019-07-14
Grub tries to run the video resolution of your system. But sometimes needs help, setting gfxmode fixes an issue with grub finding correct default X by Y resolution to display.

Boot-Repair also has that as an option in its advanced options & grub options tab. Or you can manually edit /etc/default/grub file, but need to change to an available ratio & best to use default for monitor if available.
> # The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

Grub-Customizer also adds its own proxy files to replace standard grub2 files in /etc/grub.d.

---

