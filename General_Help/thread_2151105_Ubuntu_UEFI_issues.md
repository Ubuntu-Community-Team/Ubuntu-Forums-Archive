---
title: "Ubuntu UEFI issues"
date: 2013-06-03
forum: General Help
---

### Post by dbzkid on 2013-06-03
To start off, I have bought a new Asus K55N laptop with windows 8 pre-installed. I am trying to install dual-boot Ubuntu 13.04 x64 and windows 8. Also secureboot and fastboot are disabled I followed this guide: [https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI") and here is what happened

Booting from USB - UEFI

I tried to boot from the USB in uefi and am greeted with the black and white grub menu, I select "try ubuntu" and it goes to the blank black screen. After doing some research and trying several different flags such as nomodeset and others it will not go past that boot screen. 

Booting from USB - CSM/Legacy/BIOS

I was able to successfully boot off of the usb in CSM mode and was able to install ubuntu. Once I did everything worked and was able to reboot with no problems. Until I tried to boot windows where it did not boot windows (I cant remember the exact error because it was several days ago). So I switched the computer to UEFI mode to load windows, it loaded and then after a day I wanted to run ubuntu and Grub would no longer work (again I cannot remember exactly what it said).

From here I continued to follow the guide and run the boot-repair to fix any issues. it stated it completed and I rebooted the machine in uefi and was greeted with the purple grub menu with both windows and ubuntu entries. I tried booting in to windows and it worked, when I tried to boot in to ubuntu it simply hangs and I get stuck at the purple screen (similar to the black screen)

I now tried booting from live usb (bios mode) and doing another boot repair (and purge the grub) and got to the point where it wanted to chroot and install grub-efi. When It tried to do this it continuously failed. it will give me a dependency error and dpkg will leave the package unconfigured. I also tried to force the configuration and still nothing.

As of right now I am stuck with a grub menu that will boot windows but will not boot ubuntu.

Another note to mention I tried rEFInd via usb and it booted up and showed that I had ubuntu and windows and allowed me to boot windows but when I tried to boot ubuntu it gave me that blank screen again. I have also tried to re-install ubuntu (manually deleting the partitions and re-installing) and I get the error: file '/boot/grub/x86_64-efi/normal.mod' not found

here is my boot info:
[http://paste.ubuntu.com/5729057/](http://paste.ubuntu.com/5729057/)

```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 31Jan2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    580614144 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 94 for .
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/grubx64.efi 
                       /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.04 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:  Syslinux looks at sector 1056568 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       616,447       614,400 EFI System partition
/dev/sda2         616,448     2,459,647     1,843,200 Windows Recovery Environment (Windows)
/dev/sda3       2,459,648     2,721,791       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       2,721,792   580,614,143   577,892,352 Data partition (Windows/Linux)
/dev/sda5     580,614,144   580,616,191         2,048 BIOS Boot partition
/dev/sda6     934,809,600   976,773,119    41,963,520 Windows Recovery Environment (Windows)
/dev/sda7     580,616,192   927,559,679   346,943,488 Data partition (Windows/Linux)
/dev/sda8     927,559,680   934,809,599     7,249,920 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
228 heads, 59 sectors/track, 584 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     7,854,079     7,852,032   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        FCEA-00B0                              vfat       SYSTEM
/dev/sda2        A252B86B52B84637                       ntfs       Recovery
/dev/sda4        58C2BBEEC2BBCE8E                       ntfs       OS
/dev/sda6        A6A6BF89A6BF590F                       ntfs       Restore
/dev/sda7        b7bc66a9-8b85-46fd-8072-046da818af25   ext4       
/dev/sda8        d9df69c7-da2e-40c2-82a5-aa53473e2264   swap       
/dev/sdb1        5A63-1584                              vfat       MYLINUXLIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='hd0,gpt7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  b7bc66a9-8b85-46fd-8072-046da818af25
else
  search --no-floppy --fs-uuid --set=root b7bc66a9-8b85-46fd-8072-046da818af25
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-b7bc66a9-8b85-46fd-8072-046da818af25' {
recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt7'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  b7bc66a9-8b85-46fd-8072-046da818af25
	else
	  search --no-floppy --fs-uuid --set=root b7bc66a9-8b85-46fd-8072-046da818af25
	fi
	linux	/boot/vmlinuz-3.8.0-23-generic root=UUID=b7bc66a9-8b85-46fd-8072-046da818af25 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.8.0-23-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-b7bc66a9-8b85-46fd-8072-046da818af25' {
	menuentry 'Ubuntu, with Linux 3.8.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-23-generic-advanced-b7bc66a9-8b85-46fd-8072-046da818af25' {
	recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  b7bc66a9-8b85-46fd-8072-046da818af25
		else
		  search --no-floppy --fs-uuid --set=root b7bc66a9-8b85-46fd-8072-046da818af25
		fi
		echo	'Loading Linux 3.8.0-23-generic ...'
		linux	/boot/vmlinuz-3.8.0-23-generic root=UUID=b7bc66a9-8b85-46fd-8072-046da818af25 ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-23-generic
	}
	menuentry 'Ubuntu, with Linux 3.8.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-23-generic-recovery-b7bc66a9-8b85-46fd-8072-046da818af25' {
	recordfail
		load_video
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  b7bc66a9-8b85-46fd-8072-046da818af25
		else
		  search --no-floppy --fs-uuid --set=root b7bc66a9-8b85-46fd-8072-046da818af25
		fi
		echo	'Loading Linux 3.8.0-23-generic ...'
		linux	/boot/vmlinuz-3.8.0-23-generic root=UUID=b7bc66a9-8b85-46fd-8072-046da818af25 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-23-generic
	}
	menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-b7bc66a9-8b85-46fd-8072-046da818af25' {
	recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  b7bc66a9-8b85-46fd-8072-046da818af25
		else
		  search --no-floppy --fs-uuid --set=root b7bc66a9-8b85-46fd-8072-046da818af25
		fi
		echo	'Loading Linux 3.8.0-19-generic ...'
		linux	/boot/vmlinuz-3.8.0-19-generic root=UUID=b7bc66a9-8b85-46fd-8072-046da818af25 ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-19-generic
	}
	menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-b7bc66a9-8b85-46fd-8072-046da818af25' {
	recordfail
		load_video
		insmod gzio
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt7'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  b7bc66a9-8b85-46fd-8072-046da818af25
		else
		  search --no-floppy --fs-uuid --set=root b7bc66a9-8b85-46fd-8072-046da818af25
		fi
		echo	'Loading Linux 3.8.0-19-generic ...'
		linux	/boot/vmlinuz-3.8.0-19-generic root=UUID=b7bc66a9-8b85-46fd-8072-046da818af25 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.8.0-19-generic
	}
}

```

If anyone can point me in the right direction I would really appreciate it! I must have tried getting this working for several days.

Thanks,

Kevin

---

### Post by howefield on 2013-06-03
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?t=2151100](http://ubuntuforums.org/showthread.php?t=2151100)

---

