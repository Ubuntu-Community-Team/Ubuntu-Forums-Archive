---
title: "XP not booting from Grub menu"
date: 2013-07-08
forum: General Help
---

### Post by abagg1 on 2013-07-08
When I boot to my XP installation all I get is a flashing cursor ... noticed that it seems that the bootinfoscript is the first step ... i really do not know how to analyse the output so it is pasted here ...thanks for any help



                  Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 4 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM


sda2: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM


sda3: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sda4: __________________________________________________________________________


    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb2: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 


sdb5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img


sdb6: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *             63   209,990,746   209,990,684   7 NTFS / exFAT / HPFS
/dev/sda2         302,246,910   312,496,379    10,249,470   c W95 FAT32 (LBA)
/dev/sda3         312,496,380   312,576,704        80,325  82 Linux swap / Solaris
/dev/sda4         209,991,678   302,245,887    92,254,210  83 Linux




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 8010 MB, 8010072064 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15644672 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1               8,192     5,752,021     5,743,830   b W95 FAT32
/dev/sdb2           5,752,830    15,642,623     9,889,794   5 Extended
/dev/sdb5           5,752,832    15,103,999     9,351,168  83 Linux
/dev/sdb6          15,106,048    15,642,623       536,576  82 Linux swap / Solaris




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda1        6C648DAC648D7A1A                       ntfs       
/dev/sda2        CCED-990E                              vfat       PE
/dev/sda3        356a69cd-5417-4ec3-9f10-9ab513f1c032   swap       
/dev/sda4        7bc2f29f-53a7-4b86-8d78-8b805a2a70de   ext2       
/dev/sdb1        9016-4EF8                              vfat       
/dev/sdb5        287abab0-48c0-4fc6-8af6-1ab938a5540f   ext4       
/dev/sdb6        99799183-626f-48e8-9e7d-d0826971bdf4   swap       


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sdb1        /media/9016-4EF8         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb5        /                        ext4       (rw,errors=remount-ro)




================================ sda1/boot.ini: ================================


--------------------------------------------------------------------------------
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------


=========================== sda4/boot/grub/grub.cfg: ===========================


--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi


function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}


function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-41-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	linux	/boot/vmlinuz-2.6.32-41-generic root=UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-41-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-41-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	echo	'Loading Linux 2.6.32-41-generic ...'
	linux	/boot/vmlinuz-2.6.32-41-generic root=UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-41-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-39-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	linux	/boot/vmlinuz-2.6.32-39-generic root=UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-39-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	echo	'Loading Linux 2.6.32-39-generic ...'
	linux	/boot/vmlinuz-2.6.32-39-generic root=UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-39-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	linux	/boot/vmlinuz-2.6.32-38-generic root=UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	echo	'Loading Linux 2.6.32-38-generic ...'
	linux	/boot/vmlinuz-2.6.32-38-generic root=UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6C648DAC648D7A1A
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
	insmod fat
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set cced-990e
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sdb5)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 287abab0-48c0-4fc6-8af6-1ab938a5540f
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=287abab0-48c0-4fc6-8af6-1ab938a5540f ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sdb5)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 287abab0-48c0-4fc6-8af6-1ab938a5540f
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=287abab0-48c0-4fc6-8af6-1ab938a5540f ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------


=============================== sda4/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de /               ext2    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=356a69cd-5417-4ec3-9f10-9ab513f1c032 none            swap    sw              0       0
--------------------------------------------------------------------------------


=================== sda4: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


 122.663176537 = 131.708582912  boot/grub/core.img                             1
 132.737883568 = 142.526217216  boot/grub/grub.cfg                             2
 122.561106682 = 131.598986240  boot/initrd.img-2.6.32-21-generic              3
 122.529891014 = 131.565468672  boot/initrd.img-2.6.32-38-generic              3
 122.535738945 = 131.571747840  boot/initrd.img-2.6.32-39-generic              4
 122.562754631 = 131.600755712  boot/initrd.img-2.6.32-41-generic              4
 122.520861626 = 131.555773440  boot/vmlinuz-2.6.32-21-generic                 2
 122.596549034 = 131.637042176  boot/vmlinuz-2.6.32-38-generic                 2
 122.541861534 = 131.578321920  boot/vmlinuz-2.6.32-39-generic                 2
 122.545607567 = 131.582344192  boot/vmlinuz-2.6.32-41-generic                 3
 122.562754631 = 131.600755712  initrd.img                                     4
 122.535738945 = 131.571747840  initrd.img.old                                 4
 122.545607567 = 131.582344192  vmlinuz                                        3
 122.541861534 = 131.578321920  vmlinuz.old                                    2


=========================== sdb5/boot/grub/grub.cfg: ===========================


--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi


function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}


function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 287abab0-48c0-4fc6-8af6-1ab938a5540f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 287abab0-48c0-4fc6-8af6-1ab938a5540f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 287abab0-48c0-4fc6-8af6-1ab938a5540f
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=287abab0-48c0-4fc6-8af6-1ab938a5540f ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 287abab0-48c0-4fc6-8af6-1ab938a5540f
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=287abab0-48c0-4fc6-8af6-1ab938a5540f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 287abab0-48c0-4fc6-8af6-1ab938a5540f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 287abab0-48c0-4fc6-8af6-1ab938a5540f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 6c648dac648d7a1a
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
	insmod fat
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set cced-990e
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-41-generic (on /dev/sda4)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	linux /boot/vmlinuz-2.6.32-41-generic root=UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de ro quiet splash
	initrd /boot/initrd.img-2.6.32-41-generic
}
menuentry "Ubuntu, with Linux 2.6.32-41-generic (recovery mode) (on /dev/sda4)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	linux /boot/vmlinuz-2.6.32-41-generic root=UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de ro single
	initrd /boot/initrd.img-2.6.32-41-generic
}
menuentry "Ubuntu, with Linux 2.6.32-39-generic (on /dev/sda4)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	linux /boot/vmlinuz-2.6.32-39-generic root=UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de ro quiet splash
	initrd /boot/initrd.img-2.6.32-39-generic
}
menuentry "Ubuntu, with Linux 2.6.32-39-generic (recovery mode) (on /dev/sda4)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	linux /boot/vmlinuz-2.6.32-39-generic root=UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de ro single
	initrd /boot/initrd.img-2.6.32-39-generic
}
menuentry "Ubuntu, with Linux 2.6.32-38-generic (on /dev/sda4)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	linux /boot/vmlinuz-2.6.32-38-generic root=UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de ro quiet splash
	initrd /boot/initrd.img-2.6.32-38-generic
}
menuentry "Ubuntu, with Linux 2.6.32-38-generic (recovery mode) (on /dev/sda4)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	linux /boot/vmlinuz-2.6.32-38-generic root=UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de ro single
	initrd /boot/initrd.img-2.6.32-38-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda4)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de ro quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda4)" {
	insmod ext2
	set root='(hd0,4)'
	search --no-floppy --fs-uuid --set 7bc2f29f-53a7-4b86-8d78-8b805a2a70de
	linux /boot/vmlinuz-2.6.32-21-generic root=UUID=7bc2f29f-53a7-4b86-8d78-8b805a2a70de ro single
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------


=============================== sdb5/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=287abab0-48c0-4fc6-8af6-1ab938a5540f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=99799183-626f-48e8-9e7d-d0826971bdf4 none            swap    sw              0       0
--------------------------------------------------------------------------------


=================== sdb5: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


   5.592357635 = 6.004748288    boot/grub/core.img                             1
   3.092803955 = 3.320872960    boot/grub/grub.cfg                             2
   5.625576019 = 6.040416256    boot/initrd.img-2.6.32-21-generic              1
   6.434417725 = 6.908903424    boot/vmlinuz-2.6.32-21-generic                 1
   5.625576019 = 6.040416256    initrd.img                                     1
   6.434417725 = 6.908903424    vmlinuz                                        1


======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sdb2


00000000  52 94 20 00 5b 42 09 12  61 a6 e2 4c 80 88 0c 2a  |R. .[B..a..L...*|
00000010  4d 5a 84 90 67 aa b1 87  b0 eb 4a 4b 49 3a 49 30  |MZ..g.....JKI:I0|
00000020  89 24 22 48 20 88 12 6f  04 84 44 9a 88 45 13 50  |.$"H ..o..D..E.P|
00000030  92 2a 98 14 10 84 2c 4c  9a a0 90 4a 10 29 24 55  |.*....,L...J.)$U|
00000040  41 35 03 e0 44 54 42 01  58 42 43 1d 4d 90 01 4c  |A5..DTB.XBC.M..L|
00000050  22 a0 4a 58 88 32 44 9d  a4 13 00 aa 52 45 5c 32  |".JX.2D.....RE\2|
00000060  6a 4c 74 25 2c 27 46 b4  a3 3e d7 11 a5 e5 e1 b1  |jLt%,'F..>......|
00000070  ae ef 4a 89 bc b5 5e b5  77 0c 0a 2b 80 05 b4 21  |..J...^.w..+...!|
00000080  14 7e d6 90 b6 03 e4 1e  32 13 49 76 12 fc 55 3c  |.~......2.Iv..U<|
00000090  44 9a 89 46 1a 1f 0c 8c  8a 69 4d 5a 4c d3 c6 fc  |D..F.....iMZL...|
000000a0  03 4d 34 a4 9a 69 08 35  16 28 00 24 d0 69 22 a2  |.M4..i.5.(.$.i".|
000000b0  1d 05 14 25 06 94 24 26  b2 a1 01 08 48 98 90 fd  |...%..$&....H...|
000000c0  61 21 62 9a ab 54 34 a7  89 f3 ea 56 a8 20 26 8a  |a!b..T4....V. &.|
000000d0  16 28 a1 50 67 08 d0 68  4c 84 30 20 50 80 10 f8  |.(.Pg..hL.0 P...|
000000e0  50 87 c8 08 58 41 a9 1c  6b 18 a4 e5 14 85 83 fe  |P...XA..k.......|
000000f0  27 d9 53 b7 21 69 fc ac  12 f8 9e 32 92 b1 4c 55  |'.S.!i.....2..LU|
00000100  92 0d 32 25 fa 52 84 a0  10 94 bf 34 84 82 84 26  |..2%.R.....4...&|
00000110  a2 c5 6c 84 55 86 55 6d  20 94 94 94 07 52 68 18  |..l.U.Um ....Rh.|
00000120  41 08 51 0f 90 8a 80 21  14 04 42 00 84 11 24 4c  |A.Q....!..B...$L|
00000130  96 10 55 49 92 00 93 52  14 e7 d9 81 08 00 c2 10  |..UI...R........|
00000140  03 01 08 42 10 c4 00 00  60 ed ba 3d 00 e8 ca 4e  |...B....`..=...N|
00000150  80 0c 60 04 22 04 21 02  1a 02 ce 68 03 08 01 10  |..`.".!....h....|
00000160  24 e1 11 01 01 7c 00 58  00 ea 1b 12 a0 40 92 30  |$....|.X.....@.0|
00000170  82 04 55 24 08 02 74 01  49 24 01 25 2d 4c 06 43  |..U$..t.I$.%-L.C|
00000180  a2 a0 00 a2 30 84 54 0c  c4 03 04 c8 11 97 b3 08  |....0.T.........|
00000190  4c 04 04 00 62 42 30 90  21 a6 05 e7 70 93 02 69  |L...bB0.!...p..i|
000001a0  a5 29 26 b3 e8 94 99 92  40 93 24 92 90 15 29 08  |.)&.....@.$...).|
000001b0  02 24 98 92 49 bd 29 49  6d 23 0c 90 80 4a 00 18  |.$..I.)Im#...J..|
000001c0  73 66 83 2e c2 ac 02 00  00 00 00 b0 8e 00 00 2e  |sf..............|
000001d0  c3 ac 05 b4 e7 cd 02 b0  8e 00 00 38 08 00 00 00  |...........8....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by oldfred on 2013-07-08
Bootscript does not show anything wrong that we can see. You have correct NTFS partition configuration and the three Windows XP boot files shown. Boot.ini also looks correct as it is trying to boot first partition.

Often chkdsk solves Windows boot issues. You can use your XP install disk to run chkdsk. You cannot run it from Linux.
       Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

   Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

   FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

---

### Post by abagg1 on 2013-07-09
thanks for the info ... seems I have really gotten myself in a larger  pickle ... in the meantime I ran TestDisk did something and now am  getting the grub rescue prompt ... tried to follow the instructions  around Boot-Repair-Disk .... could not get it to work from the ubuntu cd  so downloaded the iso but neither versions are working ... any  thoughts?

---

### Post by oldfred on 2013-07-09
If you created bootable CD or flash drive you should be able to boot either whether hard drive works or not.
Does Ubuntu live version boot? You can manually reinstall grub2's boot loader if you have not deleted the Linux partitions with testdisk.
But Boot-Repair is easier.

 RestoreUbuntu/XP/Vista/7Bootloader & Windows 8
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) from LiveCD

---

### Post by abagg1 on 2013-07-09
i wish i could get boot repair to run ... but it seems to hang on the splash screen ...  i can choose the language then hit enter to start the session but it never comes off the splash screen .... i can boot to the ubuntu cd so let me see if i can reinstall grub

---

### Post by abagg1 on 2013-07-09
Ok so i was able to use a USB boot repair ... XP is booting but not seeing the grub menu ... so cannot get into ubuntu...

---

### Post by abagg1 on 2013-07-09
looks like i was able to get things almost back to normal ... the install of ubuntu i wanted to run is not showing in the grub menu but at least i have one .... thanks for all your advice

---

### Post by oldfred on 2013-07-09
You can try this for grub2's os-prober to search for other installs.

sudo update-grub

---

