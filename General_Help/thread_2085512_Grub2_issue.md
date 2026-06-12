---
title: "Grub2 issue"
date: 2012-11-18
forum: General Help
---

### Post by lemmy999 on 2012-11-18
I have two harddisks on my PC. A 1TB disk ( sda) where I keep all my data and a 128Gb SDD (sdb) which has three partions on it . sdb1 is Arch, sdb2 is Puppy Linux and sdb3 is Xubuntu.

I installed Arch first and it wrote Grub to sdb. Then I installed Xubuntu which seems to have installed Grub to sda.When i boot I get one of two things happen. Either I get a black screen and have to reboot, or the PC boots to Grub and I get the following entries
```
Ubuntu, with Linux 3.5.0-17-generic
Ubuntu, with Linux 3.5.0-17-generic (recovery mode)
Previous Linux versions
Arch GNU/Linux, with Linux core repo kernel' --class arch
Arch GNU/Linux, with Linux core repo kernel (Fallback initramfs
```

My full boot info is here
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Arch Linux ()
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/syslinux/syslinux.cfg

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes, 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda3               2,048 1,953,523,711 1,953,521,664   5 Extended
/dev/sda5               4,096 1,953,523,711 1,953,519,616  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 128.0 GB, 128035676160 bytes, 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    82,524,159    82,522,112  83 Linux
/dev/sdb2          82,524,160   124,745,727    42,221,568  83 Linux
/dev/sdb3         124,745,728   239,290,367   114,544,640  83 Linux
/dev/sdb4         239,290,368   250,068,991    10,778,624  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda5        bc32ff25-9992-400c-b218-3969d3634be1   ext4       Data
/dev/sdb1        1af23750-127f-4b48-8e87-a6dd41aaac16   ext4       
/dev/sdb2        3dda5df6-f211-4b92-8878-838a470b6eb8   ext4       Puppy Linux
/dev/sdb3        b304b009-2cd4-4432-bc5e-b5a878c52bcd   ext4       Ubuntu 12.10
/dev/sdb4        deacffb6-c5de-4789-8f14-9e48a1ebdc06   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /export/Kids_Films       ext4       (rw,relatime,data=ordered)
/dev/sda5        /export/Movies           ext4       (rw,relatime,data=ordered)
/dev/sda5        /export/Video            ext4       (rw,relatime,data=ordered)
/dev/sda5        /media/run/sda5          ext4       (rw,relatime,data=ordered)
/dev/sdb1        /                        ext4       (rw,relatime,data=ordered)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
insmod part_gpt
insmod part_msdos
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"

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
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  1af23750-127f-4b48-8e87-a6dd41aaac16
else
  search --no-floppy --fs-uuid --set=root 1af23750-127f-4b48-8e87-a6dd41aaac16
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
terminal_input console
terminal_output gfxterm
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Arch GNU/Linux, with Linux core repo kernel' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-core repo kernel-true-1af23750-127f-4b48-8e87-a6dd41aaac16' {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  1af23750-127f-4b48-8e87-a6dd41aaac16
	else
	  search --no-floppy --fs-uuid --set=root 1af23750-127f-4b48-8e87-a6dd41aaac16
	fi
	echo	'Loading Linux core repo kernel ...'
	linux	/boot/vmlinuz-linux root=UUID=1af23750-127f-4b48-8e87-a6dd41aaac16 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initramfs-linux.img
}
menuentry 'Arch GNU/Linux, with Linux core repo kernel (Fallback initramfs)' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-core repo kernel-fallback-1af23750-127f-4b48-8e87-a6dd41aaac16' {
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  1af23750-127f-4b48-8e87-a6dd41aaac16
	else
	  search --no-floppy --fs-uuid --set=root 1af23750-127f-4b48-8e87-a6dd41aaac16
	fi
	echo	'Loading Linux core repo kernel ...'
	linux	/boot/vmlinuz-linux root=UUID=1af23750-127f-4b48-8e87-a6dd41aaac16 ro  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initramfs-linux-fallback.img
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" --class memtest86 --class gnu --class tool {
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  1af23750-127f-4b48-8e87-a6dd41aaac16
  else
    search --no-floppy --fs-uuid --set=root 1af23750-127f-4b48-8e87-a6dd41aaac16
  fi
  linux16 ($root)/boot/memtest86+/memtest.bin
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-b304b009-2cd4-4432-bc5e-b5a878c52bcd' {
	insmod part_msdos
	insmod ext2
	set root='hd1,msdos3'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b304b009-2cd4-4432-bc5e-b5a878c52bcd
	else
	  search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
	fi
	linux /boot/vmlinuz-3.5.0-17-generic root=UUID=b304b009-2cd4-4432-bc5e-b5a878c52bcd ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.5.0-17-generic
}
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-b304b009-2cd4-4432-bc5e-b5a878c52bcd' {
	menuentry 'Ubuntu, with Linux 3.5.0-17-generic (on /dev/sdb3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--b304b009-2cd4-4432-bc5e-b5a878c52bcd' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b304b009-2cd4-4432-bc5e-b5a878c52bcd
		else
		  search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
		fi
		linux /boot/vmlinuz-3.5.0-17-generic root=UUID=b304b009-2cd4-4432-bc5e-b5a878c52bcd ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.5.0-17-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sdb3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--b304b009-2cd4-4432-bc5e-b5a878c52bcd' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b304b009-2cd4-4432-bc5e-b5a878c52bcd
		else
		  search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
		fi
		linux /boot/vmlinuz-3.5.0-17-generic root=UUID=b304b009-2cd4-4432-bc5e-b5a878c52bcd ro recovery nomodeset
		initrd /boot/initrd.img-3.5.0-17-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-32-generic (on /dev/sdb3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic--b304b009-2cd4-4432-bc5e-b5a878c52bcd' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b304b009-2cd4-4432-bc5e-b5a878c52bcd
		else
		  search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
		fi
		linux /boot/vmlinuz-3.2.0-32-generic root=UUID=b304b009-2cd4-4432-bc5e-b5a878c52bcd ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-32-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode) (on /dev/sdb3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-32-generic--b304b009-2cd4-4432-bc5e-b5a878c52bcd' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b304b009-2cd4-4432-bc5e-b5a878c52bcd
		else
		  search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
		fi
		linux /boot/vmlinuz-3.2.0-32-generic root=UUID=b304b009-2cd4-4432-bc5e-b5a878c52bcd ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-32-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-29-generic (on /dev/sdb3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-29-generic--b304b009-2cd4-4432-bc5e-b5a878c52bcd' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b304b009-2cd4-4432-bc5e-b5a878c52bcd
		else
		  search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
		fi
		linux /boot/vmlinuz-3.2.0-29-generic root=UUID=b304b009-2cd4-4432-bc5e-b5a878c52bcd ro quiet splash $vt_handoff
		initrd /boot/initrd.img-3.2.0-29-generic
	}
	menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode) (on /dev/sdb3)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-29-generic--b304b009-2cd4-4432-bc5e-b5a878c52bcd' {
		insmod part_msdos
		insmod ext2
		set root='hd1,msdos3'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos3 --hint-efi=hd1,msdos3 --hint-baremetal=ahci1,msdos3  b304b009-2cd4-4432-bc5e-b5a878c52bcd
		else
		  search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
		fi
		linux /boot/vmlinuz-3.2.0-29-generic root=UUID=b304b009-2cd4-4432-bc5e-b5a878c52bcd ro recovery nomodeset
		initrd /boot/initrd.img-3.2.0-29-generic
	}
}

### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "RexBang Linux" {
set root=(hd0,2)
linux /puppy525/vmlinuz pmedia=atahd psubdir=puppy525
initrd /puppy525/initrd.gz
}
EOF

#then sudo update-grub
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/40_custom_old ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom_old ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# 
# /etc/fstab: static file system information
#
# <file system>	<dir>	<type>	<options>	<dump>	<pass>
tmpfs		/tmp	tmpfs	nodev,nosuid	0	0
UUID=1af23750-127f-4b48-8e87-a6dd41aaac16 / ext4 defaults 0 1
UUID=deacffb6-c5de-4789-8f14-9e48a1ebdc06 swap swap defaults 0 0
/dev/sda5 /media/run/sda5  ext4 defaults 0 0
/media/run/sda5/Films  /export/Movies none bind 0 0 
/media/run/sda5/Kids_Films /export/Kids_Films none bind 0 0 
/media/run/sda5/Video /export/Video none bind 0 0 --------------------------------------------------------------------------------

======================= sdb1/boot/syslinux/syslinux.cfg: =======================

--------------------------------------------------------------------------------
# Config file for Syslinux -
# /boot/syslinux/syslinux.cfg
#
# Comboot modules:
#   * menu.c32 - provides a text menu
#   * vesamenu.c32 - provides a graphical menu
#   * chain.c32 - chainload MBRs, partition boot sectors, Windows bootloaders
#   * hdt.c32 - hardware detection tool
#   * reboot.c32 - reboots the system
#   * poweroff.com - shutdown the system
#
# To Use: Copy the respective files from /usr/lib/syslinux to /boot/syslinux.
# If /usr and /boot are on the same file system, symlink the files instead
# of copying them.
#
# If you do not use a menu, a 'boot:' prompt will be shown and the system
# will boot automatically after 5 seconds.
#
# Please review the wiki: https://wiki.archlinux.org/index.php/Syslinux
# The wiki provides further configuration examples

DEFAULT arch
PROMPT 0        # Set to 1 if you always want to display the boot: prompt 
TIMEOUT 50
# You can create syslinux keymaps with the keytab-lilo tool
#KBDMAP de.ktl

# Menu Configuration
# Either menu.c32 or vesamenu32.c32 must be copied to /boot/syslinux 
UI menu.c32
#UI vesamenu.c32

# Refer to http://syslinux.zytor.com/wiki/index.php/Doc/menu
MENU TITLE Arch Linux
#MENU BACKGROUND splash.png
MENU COLOR border       30;44   #40ffffff #a0000000 std
MENU COLOR title        1;36;44 #9033ccff #a0000000 std
MENU COLOR sel          7;37;40 #e0ffffff #20ffffff all
MENU COLOR unsel        37;44   #50ffffff #a0000000 std
MENU COLOR help         37;40   #c0ffffff #a0000000 std
MENU COLOR timeout_msg  37;40   #80ffffff #00000000 std
MENU COLOR timeout      1;37;40 #c0ffffff #00000000 std
MENU COLOR msg07        37;40   #90ffffff #a0000000 std
MENU COLOR tabmsg       31;40   #30ffffff #00000000 std

# boot sections follow
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

LABEL arch
	MENU LABEL Arch Linux
	LINUX ../vmlinuz-linux
	APPEND root=/dev/sda3 ro
	INITRD ../initramfs-linux.img

LABEL archfallback
	MENU LABEL Arch Linux Fallback
	LINUX ../vmlinuz-linux
	APPEND root=/dev/sda3 ro
	INITRD ../initramfs-linux-fallback.img

#LABEL windows
#        MENU LABEL Windows
#        COM32 chain.c32
#        APPEND hd0 1

LABEL hdt
        MENU LABEL HDT (Hardware Detection Tool)
        COM32 hdt.c32
 
LABEL reboot
        MENU LABEL Reboot
        COM32 reboot.c32
 
LABEL off
        MENU LABEL Power Off
        COMBOOT poweroff.com
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  18.677772522 = 20.055105536   boot/grub/grub.cfg                             1
  21.214584351 = 22.778986496   boot/initramfs-linux-fallback.img              1
  21.191375732 = 22.754066432   boot/initramfs-linux.img                       1
   8.746276855 = 9.391243264    boot/vmlinuz-linux                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

   8.126136780 = 8.725372928    boot/syslinux/syslinux.cfg                     1

=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos3)'
search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1366x768
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos3)'
  search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
	linux	/boot/vmlinuz-3.5.0-17-generic root=UUID=b304b009-2cd4-4432-bc5e-b5a878c52bcd ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.5.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
	echo	'Loading Linux 3.5.0-17-generic ...'
	linux	/boot/vmlinuz-3.5.0-17-generic root=UUID=b304b009-2cd4-4432-bc5e-b5a878c52bcd ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.5.0-17-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
	linux	/boot/vmlinuz-3.2.0-32-generic root=UUID=b304b009-2cd4-4432-bc5e-b5a878c52bcd ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
	echo	'Loading Linux 3.2.0-32-generic ...'
	linux	/boot/vmlinuz-3.2.0-32-generic root=UUID=b304b009-2cd4-4432-bc5e-b5a878c52bcd ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=b304b009-2cd4-4432-bc5e-b5a878c52bcd ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
	echo	'Loading Linux 3.2.0-29-generic ...'
	linux	/boot/vmlinuz-3.2.0-29-generic root=UUID=b304b009-2cd4-4432-bc5e-b5a878c52bcd ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-29-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos3)'
	search --no-floppy --fs-uuid --set=root b304b009-2cd4-4432-bc5e-b5a878c52bcd
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Arch GNU/Linux, with Linux core repo kernel' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-core repo kernel-true-1af23750-127f-4b48-8e87-a6dd41aaac16 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 1af23750-127f-4b48-8e87-a6dd41aaac16
	linux /boot/vmlinuz-linux root=UUID=1af23750-127f-4b48-8e87-a6dd41aaac16 ro quiet
	initrd /boot/initramfs-linux.img
}
menuentry "Arch GNU/Linux, with Linux core repo kernel (Fallback initramfs)' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-core repo kernel-fallback-1af23750-127f-4b48-8e87-a6dd41aaac16 (on /dev/sdb1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 1af23750-127f-4b48-8e87-a6dd41aaac16
	linux /boot/vmlinuz-linux root=UUID=1af23750-127f-4b48-8e87-a6dd41aaac16 ro quiet
	initrd /boot/initramfs-linux-fallback.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "RexBang Linux" {
set root=(hd0,2)
linux /puppy525/vmlinuz pmedia=atahd psubdir=puppy525
initrd /puppy525/initrd.gz
}
EOF

#then sudo update-grub
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=b304b009-2cd4-4432-bc5e-b5a878c52bcd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb4 during installation
UUID=deacffb6-c5de-4789-8f14-9e48a1ebdc06 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  93.777248383 = 100.692553728  boot/grub/core.img                             1
  93.817581177 = 100.735860736  boot/grub/grub.cfg                             1
  60.902778625 = 65.393860608   boot/initrd.img-3.2.0-29-generic               2
  62.160690308 = 66.744532992   boot/initrd.img-3.2.0-32-generic               1
  93.723983765 = 100.635361280  boot/initrd.img-3.5.0-17-generic               1
 107.675128937 = 115.615289344  boot/vmlinuz-3.2.0-29-generic                  1
  60.753650665 = 65.233735680   boot/vmlinuz-3.2.0-32-generic                  1
 107.701030731 = 115.643101184  boot/vmlinuz-3.5.0-17-generic                  1
  60.902778625 = 65.393860608   initrd.img.old                                 2
  60.753650665 = 65.233735680   vmlinuz                                        1
 107.675128937 = 115.615289344  vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
  No volume groups found
mdadm: No arrays found in config file or automatically


```

My question is, I don't need both Grubs so can I just delete one? If so how do I go about it?

---

### Post by efflandt on 2012-11-18
At this point do you have BIOS set to boot sda or sdb.  It looks like it is the Ubuntu grub that is currently working.  Do you get the black screen when you switch BIOS boot order to the opposite, or randomly while booting the same drive?

You would remove grub from within whichever OS you want to remove it from.  But I don't know if that removes grub from the mbr or restores the previous mbr.  But if that OS does a kernel update or anything else that runs initramfs, to access those changes in that OS you will need to boot the primary OS and do: **sudo update-grub**

---

### Post by lemmy999 on 2012-11-18
The BIOS is set to boot from sdb. Generally, from cold, I have to boot twice. There are, in fact, two separate issues here

1. The reboot issue ( as described previously)
2. The "Ubuntu, with Linux 3.5.0-17-generic" issue ie- xubuntu is currently using 3.2.33 (IIRC) If I could just remove those entries from Grub then I'd probably be happy to leave both instances of Grub. I can only imagine that entry is a remnant from a previous 12.10 install ( the one where I decided that I just couldn't get along with Unity:()

---

### Post by oldfred on 2012-11-18
I prefer just to use synaptic to houseclean old kernels. Others may suggest grub customizer to hide entries or Ubuntu tweak, but I do not know if they work well with the newest versions.

       Check current kernel, I also keep one older just in case:
#Current kernel:
uname -a
#current install:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by lemmy999 on 2012-11-18
> I prefer just to use synaptic to houseclean old kernels. 

Unfortunately I think Grub is detecting remnants of a previous Ubuntu install and I'm not too sure that synaptic will deal with that issue.

I'm away from my PC for a couple of days but I'll have another look at the options when I get back.

---

