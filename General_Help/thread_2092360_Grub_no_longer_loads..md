---
title: "Grub no longer loads."
date: 2012-12-07
forum: General Help
---

### Post by Sylos on 2012-12-07
Well I finally did it. Its been around 5 years of Ubuntu usage and I finally broke my Grub. I feel like I've gone through a rite of passage, a feeling that will no doubt be much more satisfying when I fix it.

So, like a good boy I have booted into an old 10.04 Live disc and run the boot info script (attached).

It seems to be saying that the core.img is missing but when I mount the partition and look in the grub folder, it appears to be there. All my folders appear to be locked when I look at them (although not so for my Tango Studio partition).

Anyway, if one of the wise men of the forum could direct me then I would be very grateful.

Cheers

EDIT: couldnt upload the file so here it is in code tags:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    21399762 of the same hard drive for core.img, but core.img can not be 
    found at this location.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 21267066 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

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

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34    39,062,534    39,062,501 Data partition (Windows/Linux)
/dev/sda2      39,062,535    70,312,535    31,250,001 Swap partition (Linux)
/dev/sda3      70,312,536 1,828,125,036 1,757,812,501 Data partition (Windows/Linux)
/dev/sda4   1,828,126,720 1,886,717,951    58,591,232 Data partition (Windows/Linux)
/dev/sda5   1,886,717,952 1,917,970,431    31,252,480 Swap partition (Linux)
/dev/sda6   1,917,970,432 3,907,028,991 1,989,058,560 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        369f384b-5d90-400e-8c13-84d820770da2   ext4       
/dev/sda2        87799a61-7688-4687-8e32-01f7360f749f   swap       
/dev/sda3        9f69ee7f-aee4-4d5d-8606-4702361bb7f8   ext4       
/dev/sda4        f2b9fcd3-aaa6-4ee7-9898-939f53756f3d   ext4       
/dev/sda5        7243295e-71c0-4844-bf2b-695773290c02   swap       
/dev/sda6        4919299d-b3f8-440e-8ad0-455647e4e2ad   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/369f384b-5d90-400e-8c13-84d820770da2 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /mnt                     ext4       (rw)
/dev/sda3        /media/9f69ee7f-aee4-4d5d-8606-4702361bb7f8 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda4        /media/f2b9fcd3-aaa6-4ee7-9898-939f53756f3d ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda6        /media/4919299d-b3f8-440e-8ad0-455647e4e2ad ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set default="2"
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

insmod part_gpt
insmod ext2
set root='(hd0,gpt1)'
search --no-floppy --fs-uuid --set=root 369f384b-5d90-400e-8c13-84d820770da2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt1)'
  search --no-floppy --fs-uuid --set=root 369f384b-5d90-400e-8c13-84d820770da2
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.3.0-030300rc6-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt1)'
	search --no-floppy --fs-uuid --set=root 369f384b-5d90-400e-8c13-84d820770da2
	linux	/boot/vmlinuz-3.3.0-030300rc6-generic root=UUID=369f384b-5d90-400e-8c13-84d820770da2 ro  splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.3.0-030300rc6-generic
}
menuentry 'Ubuntu, with Linux 3.3.0-030300rc6-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt1)'
	search --no-floppy --fs-uuid --set=root 369f384b-5d90-400e-8c13-84d820770da2
	echo	'Loading Linux 3.3.0-030300rc6-generic ...'
	linux	/boot/vmlinuz-3.3.0-030300rc6-generic root=UUID=369f384b-5d90-400e-8c13-84d820770da2 ro recovery nomodeset  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.3.0-030300rc6-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt1)'
	search --no-floppy --fs-uuid --set=root 369f384b-5d90-400e-8c13-84d820770da2
	linux	/boot/vmlinuz-3.0.0-28-generic root=UUID=369f384b-5d90-400e-8c13-84d820770da2 ro  splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-28-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt1)'
	search --no-floppy --fs-uuid --set=root 369f384b-5d90-400e-8c13-84d820770da2
	echo	'Loading Linux 3.0.0-28-generic ...'
	linux	/boot/vmlinuz-3.0.0-28-generic root=UUID=369f384b-5d90-400e-8c13-84d820770da2 ro recovery nomodeset  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-28-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt1)'
	search --no-floppy --fs-uuid --set=root 369f384b-5d90-400e-8c13-84d820770da2
	linux	/boot/vmlinuz-3.0.0-26-generic root=UUID=369f384b-5d90-400e-8c13-84d820770da2 ro  splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt1)'
	search --no-floppy --fs-uuid --set=root 369f384b-5d90-400e-8c13-84d820770da2
	echo	'Loading Linux 3.0.0-26-generic ...'
	linux	/boot/vmlinuz-3.0.0-26-generic root=UUID=369f384b-5d90-400e-8c13-84d820770da2 ro recovery nomodeset  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt1)'
	search --no-floppy --fs-uuid --set=root 369f384b-5d90-400e-8c13-84d820770da2
	linux	/boot/vmlinuz-3.0.0-17-generic root=UUID=369f384b-5d90-400e-8c13-84d820770da2 ro  splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt1)'
	search --no-floppy --fs-uuid --set=root 369f384b-5d90-400e-8c13-84d820770da2
	echo	'Loading Linux 3.0.0-17-generic ...'
	linux	/boot/vmlinuz-3.0.0-17-generic root=UUID=369f384b-5d90-400e-8c13-84d820770da2 ro recovery nomodeset  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt1)'
	search --no-floppy --fs-uuid --set=root 369f384b-5d90-400e-8c13-84d820770da2
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=369f384b-5d90-400e-8c13-84d820770da2 ro  splash  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt1)'
	search --no-floppy --fs-uuid --set=root 369f384b-5d90-400e-8c13-84d820770da2
	echo	'Loading Linux 3.0.0-16-generic ...'
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=369f384b-5d90-400e-8c13-84d820770da2 ro recovery nomodeset  splash
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu
```

EDIT2: Tried "sudo dpkg-reconfigure grub-pc" but it fails to install in the relevant drive.

---

### Post by oldfred on 2012-12-07
You are the second one today or yesterday. You need a bios_grub 1MB unformated partition. Use gparted and set bios_grub flag.

It seems the old version did allow grub2 to be installed without the bios_grub. It may have told you it was not recommended?

Installs now auto create the bios_grub if drive is partitioned with gpt, but it does not look like the update tells you anything.

       However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.

   In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

   You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot on

   Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

    
Then grub reinstall should work without issue.

---

### Post by Sylos on 2012-12-08
> **oldfred said:**
> You are the second one today or yesterday. You need a bios_grub 1MB unformated partition. Use gparted and set bios_grub flag.

It seems the old version did allow grub2 to be installed without the bios_grub. It may have told you it was not recommended?

Installs now auto create the bios_grub if drive is partitioned with gpt, but it does not look like the update tells you anything.

       However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.

   In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

   You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sda set <partition_number> boot on

   Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

    
Then grub reinstall should work without issue.

Thanks for the help. I actually failed to do it by that method.Got as far as making the partition and labelling it as boot but then still couldnt get Grub installed. In the course of trying to look for details on why I found the bootrepair prog and used that to repair it.

I remember reading about needing a fake MBR for GPT when I installed but I just let the CD do its thing and it worked. Odd that it works without.

Hey ho, thanks again for the help, very much appreciated.

Cheers

---

