---
title: "Windows OS not detected by grub after I udated to 18.04"
date: 2018-10-20
forum: General Help
---

### Post by necb on 2018-10-20
I updated from Xubuntu 16.04 to 18.04 and I no longer get a grub menu.  My Windows HDD is /dev/sdc and my Xubuntu 18.04 HDD is /dev/sda.  I searched around this forum and many users were able to fix this by running os-prober and update-grub.  I tried running sudo os-prober but it does not print any output at all and update-grub does not work either.  If I go into my BIOS and force my computer to boot into Windows it boots up Window OS just fine.  So my Windows HDD is working, it just isn't detect in 18.04 (even though 16.04 detected it without any problem).  How do I fix this so that when I boot I get a grub menu with my Xubuntu and Windows OS as choices?

---

### Post by oldfred on 2018-10-20
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

With multiple drives, do not run any autofix, only use advanced mode. But best to wait until someone reviews report.

---

### Post by necb on 2018-10-20
Okay, I made some progress.  It appears that when I installed 18.04 I reformatted my disk.  It made two partitions...

Linux HDD  Samsung Evo 500GB
/dev/sda1  contains a 512 MB EFI System
/dev/sda2  contains a 499.5 GB Linux Filesystem

I remembered reading somewhere that GRUB was installed on a separate partition so I went into my BIOS and saw two EFI partitions in my BIOS boot menu for my Samsung Evo hard drive.  My BIOS was set to boot from one of these, but I didn't know which one was the EFI and which one was the Linux Filesystem.  I switched the default boot order to boot to the one I wasn't currently booting from and when I rebooted I got a GRUB menu.  Yay!!!  So it seems that GRUB was probably installed on the 512 MB parition, but that my BIOS was booting from the 499.5 GB partition so it was booting directly into Linux, right?



Now my next problem is why Windows isn't detected.  My windows HDD is....

Window HDD  Crucial 250G
/dev/sdc1  100 MB  HPFS/NTFS/exFAT
/dev/sdc2  223.5GB  HPFS/NTFS/exFAT

But there is no Windows OS option in the GRUB menu.  I was messing around with boot-repair and saw this in the log...

> 1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Windows not detected by os-prober on sdc2.

and...

>  => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Windows 7/8/2012 is installed in the MBR of /dev/sdc.

So I can boot into Windows from the BIOS but no matter what I do I can't seem to get a windows option on the GRUB menu.  Any ideas?

---

### Post by necb on 2018-10-20
The [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) link is broken.  Gives a 500 error.  I installed boot-repair from the ppa and it does not give me the Windows option back in the grub menu yet.

---

### Post by necb on 2018-10-20
Here is the full boot-repair output


```
 Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Windows 7/8/2012 is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/BOOT/bkpbootx64.efi 
                       /EFI/BOOT/bootx64.efi /EFI/BOOT/fbx64.efi 
                       /EFI/ubuntu/fwupx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/mmx64.efi /EFI/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 18.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1                 2,048     1,050,623     1,048,576 EFI System partition
/dev/sda2             1,050,624   976,771,071   975,720,448 Data partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sdb1                 2,048 7,814,035,455 7,814,033,408 Data partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdc2             206,848   468,858,879   468,652,032   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition  Attrs   Start Sector    End Sector  # of Sectors System

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        9437-4BAA                              vfat       
/dev/sda2        e08dd676-77bc-4342-9a99-da710e10247f   ext4       
/dev/sdb1        6a28c8da-5045-4654-a21d-fab6ceeb0a51   ext4       4TB
/dev/sdc1        ECEED809EED7C9CA                       ntfs       System Reserved
/dev/sdc2        72B6DDC6B6DD8B4D                       ntfs       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Oct 20 09:30 ata-Crucial_CT240M500SSD3_1347095AF0FE -> ../../sdc
lrwxrwxrwx 1 root root 10 Oct 20 09:32 ata-Crucial_CT240M500SSD3_1347095AF0FE-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Oct 20 09:32 ata-Crucial_CT240M500SSD3_1347095AF0FE-part2 -> ../../sdc2
lrwxrwxrwx 1 root root  9 Oct 20 09:11 ata-PIONEER_BD-RW_BDR-205 -> ../../sr0
lrwxrwxrwx 1 root root  9 Oct 20 09:30 ata-Samsung_SSD_850_EVO_500GB_S2RANX0H727336V -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 20 09:30 ata-Samsung_SSD_850_EVO_500GB_S2RANX0H727336V-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 20 09:30 ata-Samsung_SSD_850_EVO_500GB_S2RANX0H727336V-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Oct 20 09:30 ata-WDC_WD40EFRX-68WT0N0_WD-WCC4E5UFKT9K -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct 20 09:30 ata-WDC_WD40EFRX-68WT0N0_WD-WCC4E5UFKT9K-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Oct 20 09:30 wwn-0x50014ee20d626d67 -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct 20 09:30 wwn-0x50014ee20d626d67-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Oct 20 09:30 wwn-0x5002538d410bc855 -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 20 09:30 wwn-0x5002538d410bc855-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 20 09:30 wwn-0x5002538d410bc855-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Oct 20 09:30 wwn-0x500a0751095af0fe -> ../../sdc
lrwxrwxrwx 1 root root 10 Oct 20 09:32 wwn-0x500a0751095af0fe-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Oct 20 09:32 wwn-0x500a0751095af0fe-part2 -> ../../sdc2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda2        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdb1        /media/4TB               ext4       (rw,relatime,errors=remount-ro,data=ordered)


========================== sda1/EFI/ubuntu/grub.cfg: ===========================

--------------------------------------------------------------------------------
search.fs_uuid e08dd676-77bc-4342-9a99-da710e10247f root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
--------------------------------------------------------------------------------

=========================== sda2/boot/grub/grub.cfg: ===========================

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
insmod part_gpt
insmod ext2
set root='hd0,gpt2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e08dd676-77bc-4342-9a99-da710e10247f
else
  search --no-floppy --fs-uuid --set=root e08dd676-77bc-4342-9a99-da710e10247f
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
  set timeout=10
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=10
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 10 ; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-e08dd676-77bc-4342-9a99-da710e10247f' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e08dd676-77bc-4342-9a99-da710e10247f
	else
	  search --no-floppy --fs-uuid --set=root e08dd676-77bc-4342-9a99-da710e10247f
	fi
        linux	/boot/vmlinuz-4.15.0-36-generic root=UUID=e08dd676-77bc-4342-9a99-da710e10247f ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-4.15.0-36-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-e08dd676-77bc-4342-9a99-da710e10247f' {
	menuentry 'Ubuntu, with Linux 4.15.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-36-generic-advanced-e08dd676-77bc-4342-9a99-da710e10247f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e08dd676-77bc-4342-9a99-da710e10247f
		else
		  search --no-floppy --fs-uuid --set=root e08dd676-77bc-4342-9a99-da710e10247f
		fi
		echo	'Loading Linux 4.15.0-36-generic ...'
	        linux	/boot/vmlinuz-4.15.0-36-generic root=UUID=e08dd676-77bc-4342-9a99-da710e10247f ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-36-generic
	}
	menuentry 'Ubuntu, with Linux 4.15.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-36-generic-recovery-e08dd676-77bc-4342-9a99-da710e10247f' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e08dd676-77bc-4342-9a99-da710e10247f
		else
		  search --no-floppy --fs-uuid --set=root e08dd676-77bc-4342-9a99-da710e10247f
		fi
		echo	'Loading Linux 4.15.0-36-generic ...'
	        linux	/boot/vmlinuz-4.15.0-36-generic root=UUID=e08dd676-77bc-4342-9a99-da710e10247f ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-36-generic
	}
	menuentry 'Ubuntu, with Linux 4.15.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-29-generic-advanced-e08dd676-77bc-4342-9a99-da710e10247f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e08dd676-77bc-4342-9a99-da710e10247f
		else
		  search --no-floppy --fs-uuid --set=root e08dd676-77bc-4342-9a99-da710e10247f
		fi
		echo	'Loading Linux 4.15.0-29-generic ...'
	        linux	/boot/vmlinuz-4.15.0-29-generic root=UUID=e08dd676-77bc-4342-9a99-da710e10247f ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-29-generic
	}
	menuentry 'Ubuntu, with Linux 4.15.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-29-generic-recovery-e08dd676-77bc-4342-9a99-da710e10247f' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt2'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  e08dd676-77bc-4342-9a99-da710e10247f
		else
		  search --no-floppy --fs-uuid --set=root e08dd676-77bc-4342-9a99-da710e10247f
		fi
		echo	'Loading Linux 4.15.0-29-generic ...'
	        linux	/boot/vmlinuz-4.15.0-29-generic root=UUID=e08dd676-77bc-4342-9a99-da710e10247f ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-29-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "EFI/BOOT/bkpbootx64.efi" {
search --fs-uuid --no-floppy --set=root 9437-4BAA
chainloader (${root})/EFI/BOOT/bkpbootx64.efi
}

menuentry "EFI/BOOT/fbx64.efi" {
search --fs-uuid --no-floppy --set=root 9437-4BAA
chainloader (${root})/EFI/BOOT/fbx64.efi
}

menuentry "EFI/ubuntu/fwupx64.efi" {
search --fs-uuid --no-floppy --set=root 9437-4BAA
chainloader (${root})/EFI/ubuntu/fwupx64.efi
}

menuentry "EFI/ubuntu/mmx64.efi" {
search --fs-uuid --no-floppy --set=root 9437-4BAA
chainloader (${root})/EFI/ubuntu/mmx64.efi
}
### END /etc/grub.d/25_custom ###

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

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=e08dd676-77bc-4342-9a99-da710e10247f /               ext4    errors=remount-ro 0       1
UUID=6a28c8da-5045-4654-a21d-fab6ceeb0a51 /media/4TB               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=9437-4BAA  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
UUID=9437-4BAA	/boot/efi	vfat	defaults	0	1
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 172.635334015 = 185.365778432  boot/grub/grub.cfg                             1
 174.641826630 = 187.520233472  boot/vmlinuz-4.15.0-29-generic                 1
   6.836807251 = 7.340965888    boot/vmlinuz-4.15.0-36-generic                 1
   6.836807251 = 7.340965888    vmlinuz                                        1
 174.641826630 = 187.520233472  vmlinuz.old                                    1
   7.184604645 = 7.714410496    boot/initrd.img-4.15.0-29-generic              2
   7.246662140 = 7.781044224    boot/initrd.img-4.15.0-36-generic              1
   7.246662140 = 7.781044224    initrd.img                                     1
   7.184604645 = 7.714410496    initrd.img.old                                 2


ADDITIONAL INFORMATION :
=================== log of boot-repair 20181020_0930 ===================
boot-repair version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
boot-repair is executed in installed-session (Ubuntu 18.04.1 LTS, bionic, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-4.15.0-36-generic root=UUID=e08dd676-77bc-4342-9a99-da710e10247f ro quiet splash vt.handoff=1

=================== os-prober:
/dev/sda2:The OS now in use - Ubuntu 18.04.1 LTS CurrentSession:linux

=================== blkid:
/dev/sda1: UUID="9437-4BAA" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="daa92cb8-9d3b-4998-b61a-d455eaef3ea4"
/dev/sda2: UUID="e08dd676-77bc-4342-9a99-da710e10247f" TYPE="ext4" PARTUUID="44646296-d8a3-44d5-946b-419716e76d83"
/dev/sdb1: LABEL="4TB" UUID="6a28c8da-5045-4654-a21d-fab6ceeb0a51" TYPE="ext4" PARTUUID="3d20f5bf-d5e0-4359-bc89-9e0702a0f2a2"
/dev/sdc1: LABEL="System Reserved" UUID="ECEED809EED7C9CA" TYPE="ntfs" PARTUUID="6981befa-01"
/dev/sdc2: UUID="72B6DDC6B6DD8B4D" TYPE="ntfs" PARTUUID="6981befa-02"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Windows not detected by os-prober on sdc2.

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Oct 15 19:24 grub.d
total 80
-rwxr-xr-x 1 root root  9783 Jul 17 14:13 00_header
-rwxr-xr-x 1 root root  6258 Jul 16 11:15 05_debian_theme
-rwxr-xr-x 1 root root 12693 Jul 17 14:13 10_linux
-rwxr-xr-x 1 root root 11298 Jul 17 14:13 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 12059 Jul 17 14:13 30_os-prober
-rwxr-xr-x 1 root root  1418 Jul 17 14:13 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jul 17 14:13 40_custom
-rwxr-xr-x 1 root root   216 Jul 17 14:13 41_custom
-rw-r--r-- 1 root root   483 Jul 17 14:13 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
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



/boot/efi detected in the fstab of sda2: UUID=9437-4BAA   (sda1)
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/fbx64.efi
/usr/share/boot-sav/bs-cmd_terminal.sh: line 179: warning: command substitution: ignored null byte in input

=================== efibootmgr -v
BootCurrent: 0001
Timeout: 2 seconds
BootOrder: 0001,000D,000C,000B,000E,000F,0000
Boot0000* Windows Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* ubuntu	HD(1,GPT,daa92cb8-9d3b-4998-b61a-d455eaef3ea4,0x800,0x100000)/File(EFIubuntushimx64.efi)
Boot000B* SATA : PORT 4 : Crucial_CT240M500SSD3 : PART 0 : Boot Drive	BBS(HD,,0x0)AMBO
Boot000C* SATA : PORT 6G 1 : PIONEER BD-RW   BDR-205	BBS(CDROM,,0x0)AMBO
Boot000D* SATA : PORT 6G 0 : Samsung SSD 850 EVO 500GB : PART 0 : Boot Drive	BBS(HD,,0x0)AMBO
Boot000E* SATA : PORT 2 : WDC WD40EFRX-68WT0N0 : PART 0 : Boot Drive	BBS(HD,,0x0)AMBO
Boot000F* UEFI : SATA : PORT 6G 0 : Samsung SSD 850 EVO 500GB : PART 0 : OS Bootloader	PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,65535,0)/HD(1,GPT,daa92cb8-9d3b-4998-b61a-d455eaef3ea4,0x800,0x100000)AMBO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [email]boot.repair@gmail.com[/email])


=================== PARTITIONS & DISKS:
sda2	: sda,	not-sepboot,	grubenv-ok	grub2,	signed grub-pc grub-efi ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	notbiosboot, .
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	notbiosboot, /boot/efi.
sdb1	: sdb,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /media/4TB.
sdc1	: sdc,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	notbiosboot, /mnt/boot-sav/sdc1.
sdc2	: sdc,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /media/necbot/72B6DDC6B6DD8B4D.

sda	: GPT,	no-BIOS_boot,	has-correctEFI, 	not-usb,	not-mmc, has-os,	2048 sectors * 512 bytes
sdb	: GPT,	no-BIOS_boot,	has-no-EFIpart, 	not-usb,	not-mmc, no-os,	2048 sectors * 512 bytes
sdc	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	not-mmc, has-os,	2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:512:gpt:ATA Samsung SSD 850:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:500GB:500GB:ext4::;

BYT;
/dev/sdb:4001GB:scsi:512:4096:gpt:ATA WDC WD40EFRX-68W:;
1:1049kB:4001GB:4001GB:ext4::;

BYT;
/dev/sdc:240GB:scsi:512:4096:msdos:ATA Crucial_CT240M50:;
1:1049kB:106MB:105MB:ntfs::boot;
2:106MB:240GB:240GB:ntfs::;

=================== lsblk:
KNAME TYPE FSTYPE   SIZE LABEL
sda   disk        465.8G
sda1  part vfat     512M
sda2  part ext4   465.3G
sdb   disk          3.7T
sdb1  part ext4     3.7T 4TB
sdc   disk        223.6G
sdc1  part ntfs     100M System Reserved
sdc2  part ntfs   223.5G
sr0   rom          1024M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      0  0  0 running
sda1     0  0  0         /boot/efi
sda2     0  0  0         /
sdb      1  0  0 running
sdb1     1  0  0         /media/4TB
sdc      0  0  0 running
sdc1     0  0  0         /mnt/boot-sav/sdc1
sdc2     0  0  0         /media/necbot/72B6DDC6B6DD8B4D
sr0      1  0  1 running


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8158148k,nr_inodes=2039537,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1638568k,mode=755)
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=26,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=15020)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdb1 on /media/4TB type ext4 (rw,relatime,errors=remount-ro,data=ordered)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1638564k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sdc2 on /media/necbot/72B6DDC6B6DD8B4D type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sdc1 sdc2 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 initctl input kmsg kvm lightnvm log mapper mcelog mei0 mem memory_bandwidth mqueue net network_latency network_throughput null nvidia0 nvidiactl nvidia-modeset nvidia-uvm nvidia-uvm-tools port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdb1 sdc sdc1 sdc2 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom userio vboxdrv vboxdrvu vboxnetctl vboxusb vfio vga_arbiter vhci vhost-net vhost-vsock zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 10 00 00 04 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 aa 4b 37 94 4e  4f 20 4e 41 4d 45 20 20  |..).K7.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdc1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 1f 03 00 00 00 00 00  |................|
00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|
00000040  f6 00 00 00 01 00 00 00  ca c9 d7 ee 09 d8 ee ec  |................|
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
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sdc2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 03 00  |........?....(..|
00000020  00 00 00 00 80 00 80 00  ff 0f ef 1b 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  4d 8b dd b6 c6 dd b6 72  |........M......r|
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
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.8G     0  7.8G   0% /dev
tmpfs          tmpfs     1.6G  2.8M  1.6G   1% /run
/dev/sda2      ext4      457G   12G  422G   3% /
tmpfs          tmpfs     7.9G  6.5M  7.9G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sda1      vfat      511M  6.1M  505M   2% /boot/efi
/dev/sdb1      ext4      3.6T  1.7T  1.8T  48% /media/4TB
tmpfs          tmpfs     1.6G   20K  1.6G   1% /run/user/1000
/dev/sdc2      fuseblk   224G  119G  106G  53% /media/necbot/72B6DDC6B6DD8B4D
/dev/sdc1      fuseblk   100M   25M   76M  25% /mnt/boot-sav/sdc1

=================== fdisk -l:
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 67434C35-D232-4883-927B-3F82211D53D9

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624 976771071 975720448 465.3G Linux filesystem




Disk /dev/sdb: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: BD1C2F67-F18A-4223-BF4E-F77211F60676

Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 7814035455 7814033408  3.7T Linux filesystem


Disk /dev/sdc: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x6981befa

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sdc1  *      2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sdc2       206848 468858879 468652032 223.5G  7 HPFS/NTFS/exFAT


(debug) reinstall grub2 place-in-all-MBRs no-BIOS_boot (sda2)
(debug) reinstall grub2 place-in-all-MBRs no-BIOS_boot (sda2)
=================== Repair blocked
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.
Gtk-Message: 09:31:13.685: GtkDialog mapped without a transient parent. This is discouraged.
(debug) reinstall grub2 place-in-all-MBRs no-BIOS_boot (sda2)
=================== Repair blocked
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.
Gtk-Message: 09:31:49.783: GtkDialog mapped without a transient parent. This is discouraged.


=================== Default settings of Boot Repair
The default repair of the Boot-Repair utility would purge (in order to unsign) and reinstall the grub2 of sda2 into the MBRs of all disks (except live-disks and removable disks without OS).
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot


=================== Blockers in case of suggested repair
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.


=================== Advice in case of suggested repair
EFI detected. You may want to retry after activating the [Separate /boot/efi partition:] option.
Do you want to continue?


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda (ATA Samsung SSD 850) disk!


=================== User settings
The settings chosen by the user will reinstall the grub-efi-amd64-signed of sda2, using the following options:        sda1/boot/efi,
Grub-efi will not be selected by default because: no-win-efi
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file


/boot/efi added in sda2/fstab
Quantity of real Windows: 1
sda2/boot/efi not empty

*******lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP107 [GeForce GTX 1050 Ti] [10de:1c82] (rev a1)
Subsystem: ASUSTeK Computer Inc. GP107 [GeForce GTX 1050 Ti] [1043:85c3]
Kernel driver in use: nvidia
Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
*******

grub-install --version
grub-install (GRUB) 2.02-2ubuntu8.6,grub-install (GRUB) 2.

efibootmgr -v
BootCurrent: 0001
Timeout: 2 seconds
BootOrder: 0001,000D,000C,000B,000E,000F,0000
Boot0000* Windows Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* ubuntu	HD(1,GPT,daa92cb8-9d3b-4998-b61a-d455eaef3ea4,0x800,0x100000)/File(EFIubuntushimx64.efi)
Boot000B* SATA : PORT 4 : Crucial_CT240M500SSD3 : PART 0 : Boot Drive	BBS(HD,,0x0)AMBO
Boot000C* SATA : PORT 6G 1 : PIONEER BD-RW   BDR-205	BBS(CDROM,,0x0)AMBO
Boot000D* SATA : PORT 6G 0 : Samsung SSD 850 EVO 500GB : PART 0 : Boot Drive	BBS(HD,,0x0)AMBO
Boot000E* SATA : PORT 2 : WDC WD40EFRX-68WT0N0 : PART 0 : Boot Drive	BBS(HD,,0x0)AMBO
Boot000F* UEFI : SATA : PORT 6G 0 : Samsung SSD 850 EVO 500GB : PART 0 : OS Bootloader	PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,65535,0)/HD(1,GPT,daa92cb8-9d3b-4998-b61a-d455eaef3ea4,0x800,0x100000)AMBO

uname -r
Kernel: 4.15.0-36-generic

Reinstall the grub-efi-amd64-signed of sda2
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : exit code of grub-install :0
efi files in sda1/efi: /ubuntu/shimx64.efi /ubuntu/mmx64.efi /ubuntu/grubx64.efi /ubuntu/fwupx64.efi /BOOT/fbx64.efi
ls: cannot access '/media/necbot/72B6DDC6B6DD8B4D/': No such file or directory
ls: cannot access '/media/necbot/72B6DDC6B6DD8B4D/': No such file or directory
df /dev/sda1
Save and rename /boot/efi/EFI/Boot/bootx64.efi (/boot/efi/EFI/Boot/bkpbootx64.efi)
cp /boot/efi/EFI/ubuntu/shimx64.efi /boot/efi/EFI/Boot/bootx64.efi
efi files in sda1/efi: /ubuntu/shimx64.efi /ubuntu/mmx64.efi /ubuntu/grubx64.efi /ubuntu/fwupx64.efi /BOOT/fbx64.efi /BOOT/bootx64.efi /BOOT/bkpbootx64.efi
Add /boot/efi efi entries in /etc/grub.d/25_custom
Adding custom /boot/efi/EFI/BOOT/bkpbootx64.efi
Adding custom /boot/efi/EFI/BOOT/fbx64.efi
Adding custom /boot/efi/EFI/ubuntu/fwupx64.efi
Adding custom /boot/efi/EFI/ubuntu/mmx64.efi
ls: cannot access '/media/necbot/72B6DDC6B6DD8B4D/': No such file or directory
ls: cannot access '/media/necbot/72B6DDC6B6DD8B4D/': No such file or directory
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : exit code of grub-install :0

efibootmgr -v
BootCurrent: 0001
Timeout: 2 seconds
BootOrder: 0001,000D,000C,000B,000E,000F,0000
Boot0000* Windows Boot Manager	VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0001* ubuntu	HD(1,GPT,daa92cb8-9d3b-4998-b61a-d455eaef3ea4,0x800,0x100000)/File(EFIubuntushimx64.efi)
Boot000B* SATA : PORT 4 : Crucial_CT240M500SSD3 : PART 0 : Boot Drive	BBS(HD,,0x0)AMBO
Boot000C* SATA : PORT 6G 1 : PIONEER BD-RW   BDR-205	BBS(CDROM,,0x0)AMBO
Boot000D* SATA : PORT 6G 0 : Samsung SSD 850 EVO 500GB : PART 0 : Boot Drive	BBS(HD,,0x0)AMBO
Boot000E* SATA : PORT 2 : WDC WD40EFRX-68WT0N0 : PART 0 : Boot Drive	BBS(HD,,0x0)AMBO
Boot000F* UEFI : SATA : PORT 6G 0 : Samsung SSD 850 EVO 500GB : PART 0 : OS Bootloader	PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,65535,0)/HD(1,GPT,daa92cb8-9d3b-4998-b61a-d455eaef3ea4,0x800,0x100000)AMBO

update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-36-generic
Found initrd image: /boot/initrd.img-4.15.0-36-generic
Found linux image: /boot/vmlinuz-4.15.0-29-generic
Found initrd image: /boot/initrd.img-4.15.0-29-generic
Adding boot menu entry for EFI firmware configuration
Unhide GRUB boot menu in sda2/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!
```

---

### Post by oldfred on 2018-10-20
Windows is installed on sdc which is MBR(msdos) partitioned. Windows only boots in BIOS boot mode from MBR partitioned drives.

Ubuntu is installed in UEFI boot mode from sda which is gpt partitioned.

UEFI and BIOS boot are not compatible. They record hardware info onto drive differently for operating system use. 
You can dual boot only from UEFI boot menu.

If you want to dual boot from grub, you either have to reinstall Windows in UEFI boot mode onto gpt partitioned drive, or convert Ubuntu to BIOS boot.
You can add a tiny 1 or 2MB unformatted partition on sda and sdb (anywhere within first 2TiB). But do not use auto fix in Boot-Repair as will also install a BIOS boot grub to sdc, you want to keep the Windows boot loader in sdc.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[URL="https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations"]https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations

[/URL]
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 

[URL="https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations"]
[/URL]

---

### Post by necb on 2018-10-20
Thank you for the explanation.  I fixed everything doing the following....


- I disabled UEFI boot in my BIOS and selected legacy boot.  
- I still had my 18.04 installation USB so I booted back into that and select "Try Ubuntu" and installed boot-repair via the PPA.    
- Then I used Gparted to ....
   1)  add a 1MB unformated partition as the beginning of /dev/sda, set the flag to bios_grub.  
   2) delete the efi partition.  
- I ran boot-repair again to install grub and rebooted and everything worked!  Thanks!

---

### Post by oldfred on 2018-10-20
Glad that worked.
I like to keep an ESP on every gpt drive for future UEFI boot configuration. 
I used bios_grub from my older system that was BIOS only and  most newer drives have both bios_grub and ESP. 
But now I only use ESP for UEFI boot.

---

