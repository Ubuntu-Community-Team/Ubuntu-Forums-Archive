---
title: "Raring fails to mount NTFS partition on boot while LM Maya doesn't"
date: 2013-12-24
forum: General Help
---

### Post by yagolf on 2013-12-24
Hi all,

I'm hoping that some of you will be like me and not let these dates get you away from your computers too much ;) 'cause I could do with some help.

I'm running Raring (Ubuntu Gnome) on an Acer Aspire V7 triple booting (EFI mode) with Windows 8 and Linux Mint Maya. 

My problem is that every time I try booting Raring after having been using Windows, it fails to mount an NTFS partition that I use to share data across all OSs and that I have set up to mount on boot in /etc/fstab.
The error that it gives me is the typical "Failed to mount such and such, press S to skip mounting or M for manual recovery", and if I try to manually mount it I get "Metadata kept in Windows cache, refused to mount. Failed to mount '/dev/sda6': Operation not permittedThe NTFS partition is in an unsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting), or mount the volume read-only with the 'ro' mount option."
The thing is, Windows was never left in hibernation and there is no fast restart enabled, and what is more, Linux Mint Maya has absolutely no problem mounting the partition (AAMOF, if I boot into it first and then restart booting Raring, the issue is gone). Maybe it's a regression, or maybe the Linux Mint team figured something out that the Ubuntu team hasn't...

I have tried playing around with my fstab but nothing changes. Here is my current fstab (the commented line at the end is the original line I used to mount the NTFS partition, the following is the one with which I booted this time around)
> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# / was on /dev/sdb9 during installation
UUID=8f843298-f4a3-4732-a292-04ffedbafc9a /               ext4    errors=remount-ro  0       1

# /boot/efi was on /dev/sdb2 during installation
UUID=E033-0FEC  /boot/efi       vfat    defaults        0       1

/dev/sdb8       none            swap    sw              0       0

# data was on /dev/sda6 during startup
#UUID=01CEE3DE243B3D30    /media/data    ntfs-3g        defaults,locale=en_UK.utf8      0    0
UUID=01CEE3DE243B3D30    /media/data    ntfs-3g        defaults,nls=utf8,umask=000,uid=1000,windows_names    0    0


I saw in another post someone asking for the output of Boot Info (from boot repair), so here it is in case you find it useful:
> 
Ubuntu Pastebin
Paste from boot-repair at Tue, 24 Dec 2013 18:27:21 +0000

Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 8Dec2013]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/linuxmint/grubx64.efi /EFI/linuxmint/shimx64.efi 
                       /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi 
                       /EFI/OEM/Boot/bootmgfw.efi /EFI/OEM/Boot/bootmgr.efi 
                       /EFI/OEM/Boot/memtest.efi

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
    Boot files:        /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 13 Maya 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.04 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

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
/dev/sda1           2,048       821,247       819,200 Windows Recovery Environment (Windows)
/dev/sda2         821,248     1,435,647       614,400 EFI System partition
/dev/sda3       1,435,648     1,697,791       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       1,697,792   208,058,367   206,360,576 Data partition (Windows/Linux)
/dev/sda5     208,058,368   240,564,223    32,505,856 Windows Recovery Environment (Windows)
/dev/sda6     240,564,224   869,871,615   629,307,392 Data partition (Windows/Linux)
/dev/sda7     869,871,616   932,371,615    62,500,000 Data partition (Windows/Linux)
/dev/sda8     972,761,088   976,766,975     4,005,888 Data partition (Windows/Linux)
/dev/sda9     932,372,480   972,761,087    40,388,608 Data partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 24.0 GB, 24015495168 bytes
256 heads, 63 sectors/track, 2908 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdb1 ends after the last sector of /dev/sdb

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048    15,644,671    15,642,624 Intel Fast Flash (iFFS) partition (for Intel Rapid Start technology)
/dev/sdb2      15,644,672    46,903,295    31,258,624 -

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5E4430A244307EB9                       ntfs       Recovery
/dev/sda2        E033-0FEC                              vfat       ESP
/dev/sda4        01CEE3DD305B9930                       ntfs       Acer
/dev/sda5        01CEE3DE239B7AC0                       ntfs       Push Button Reset
/dev/sda6        01CEE3DE243B3D30                       ntfs       data
/dev/sda7        479d91ad-9ae9-4a17-89fd-030ba74ef017   ext4       
/dev/sda8                                               swap       
/dev/sda9        8f843298-f4a3-4732-a292-04ffedbafc9a   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /boot/efi                vfat       (rw)
/dev/sda9        /                        ext4       (rw,errors=remount-ro)


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

insmod part_gpt
insmod ext2
set root='(hd0,gpt7)'
search --no-floppy --fs-uuid --set=root 479d91ad-9ae9-4a17-89fd-030ba74ef017
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt7)'
  search --no-floppy --fs-uuid --set=root 479d91ad-9ae9-4a17-89fd-030ba74ef017
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=4
else
  set timeout=4
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
menuentry 'LinuxMint, with Linux 3.2.0-57-generic' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root 479d91ad-9ae9-4a17-89fd-030ba74ef017
    linux    /boot/vmlinuz-3.2.0-57-generic root=UUID=479d91ad-9ae9-4a17-89fd-030ba74ef017 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-57-generic
}
menuentry 'LinuxMint, with Linux 3.2.0-57-generic (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root 479d91ad-9ae9-4a17-89fd-030ba74ef017
    echo    'Loading Linux 3.2.0-57-generic ...'
    linux    /boot/vmlinuz-3.2.0-57-generic root=UUID=479d91ad-9ae9-4a17-89fd-030ba74ef017 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-57-generic
}
submenu "Previous Linux versions" {
menuentry 'LinuxMint, with Linux 3.2.0-56-generic' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root 479d91ad-9ae9-4a17-89fd-030ba74ef017
    linux    /boot/vmlinuz-3.2.0-56-generic root=UUID=479d91ad-9ae9-4a17-89fd-030ba74ef017 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-56-generic
}
menuentry 'LinuxMint, with Linux 3.2.0-56-generic (recovery mode)' --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt7)'
    search --no-floppy --fs-uuid --set=root 479d91ad-9ae9-4a17-89fd-030ba74ef017
    echo    'Loading Linux 3.2.0-56-generic ...'
    linux    /boot/vmlinuz-3.2.0-56-generic root=UUID=479d91ad-9ae9-4a17-89fd-030ba74ef017 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-56-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root E033-0FEC
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root E033-0FEC
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root E033-0FEC
chainloader (${root})/EFI/ubuntu/MokManager.efi
}

menuentry "EFI/OEM/Boot/bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root E033-0FEC
chainloader (${root})/EFI/OEM/Boot/bootmgfw.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8f843298-f4a3-4732-a292-04ffedbafc9a (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt9)'
    search --no-floppy --fs-uuid --set=root 8f843298-f4a3-4732-a292-04ffedbafc9a
    linux /boot/vmlinuz-3.8.0-34-generic.efi.signed root=UUID=8f843298-f4a3-4732-a292-04ffedbafc9a ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.8.0-34-generic
}
menuentry "Ubuntu, with Linux 3.8.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-34-generic-advanced-8f843298-f4a3-4732-a292-04ffedbafc9a (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt9)'
    search --no-floppy --fs-uuid --set=root 8f843298-f4a3-4732-a292-04ffedbafc9a
    linux /boot/vmlinuz-3.8.0-34-generic.efi.signed root=UUID=8f843298-f4a3-4732-a292-04ffedbafc9a ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.8.0-34-generic
}
menuentry "Ubuntu, with Linux 3.8.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-34-generic-recovery-8f843298-f4a3-4732-a292-04ffedbafc9a (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt9)'
    search --no-floppy --fs-uuid --set=root 8f843298-f4a3-4732-a292-04ffedbafc9a
    linux /boot/vmlinuz-3.8.0-34-generic.efi.signed root=UUID=8f843298-f4a3-4732-a292-04ffedbafc9a ro recovery nomodeset
    initrd /boot/initrd.img-3.8.0-34-generic
}
menuentry "Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-8f843298-f4a3-4732-a292-04ffedbafc9a (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt9)'
    search --no-floppy --fs-uuid --set=root 8f843298-f4a3-4732-a292-04ffedbafc9a
    linux /boot/vmlinuz-3.8.0-19-generic root=UUID=8f843298-f4a3-4732-a292-04ffedbafc9a ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.8.0-19-generic
}
menuentry "Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-8f843298-f4a3-4732-a292-04ffedbafc9a (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt9)'
    search --no-floppy --fs-uuid --set=root 8f843298-f4a3-4732-a292-04ffedbafc9a
    linux /boot/vmlinuz-3.8.0-19-generic root=UUID=8f843298-f4a3-4732-a292-04ffedbafc9a ro recovery nomodeset
    initrd /boot/initrd.img-3.8.0-19-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' {
    fwsetup
}
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=479d91ad-9ae9-4a17-89fd-030ba74ef017 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
#UUID=E033-0FEC  /boot/efi       vfat    defaults        0       1
/dev/sda8       none            swap    sw              0       0
# data was on /dev/sda6 during startup
UUID=01CEE3DE243B3D30    /media/data    ntfs-3g        defaults,locale=en_UK.utf8    0    0

UUID=E033-0FEC    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 424.964565277 = 456.302227456  boot/grub/grub.cfg                             1
 419.264408112 = 450.181730304  boot/vmlinuz-3.2.0-56-generic                  1
 422.451908112 = 453.604282368  boot/vmlinuz-3.2.0-57-generic                  1
 422.451908112 = 453.604282368  vmlinuz                                        1
 419.264408112 = 450.181730304  vmlinuz.old                                    1
 416.833637238 = 447.571709952  boot/initrd.img-3.2.0-56-generic               2
 424.834556580 = 456.162631680  boot/initrd.img-3.2.0-57-generic               2

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set default="Ubuntu"

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
set root='hd0,gpt9'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  8f843298-f4a3-4732-a292-04ffedbafc9a
else
  search --no-floppy --fs-uuid --set=root 8f843298-f4a3-4732-a292-04ffedbafc9a
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=4
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 13,37,73; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8f843298-f4a3-4732-a292-04ffedbafc9a' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt9'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  8f843298-f4a3-4732-a292-04ffedbafc9a
    else
      search --no-floppy --fs-uuid --set=root 8f843298-f4a3-4732-a292-04ffedbafc9a
    fi
    linux    /boot/vmlinuz-3.8.0-35-generic.efi.signed root=UUID=8f843298-f4a3-4732-a292-04ffedbafc9a ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-35-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-8f843298-f4a3-4732-a292-04ffedbafc9a' {
    menuentry 'Ubuntu, with Linux 3.8.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-35-generic-advanced-8f843298-f4a3-4732-a292-04ffedbafc9a' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  8f843298-f4a3-4732-a292-04ffedbafc9a
        else
          search --no-floppy --fs-uuid --set=root 8f843298-f4a3-4732-a292-04ffedbafc9a
        fi
        echo    'Loading Linux 3.8.0-35-generic ...'
        linux    /boot/vmlinuz-3.8.0-35-generic.efi.signed root=UUID=8f843298-f4a3-4732-a292-04ffedbafc9a ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-35-generic-recovery-8f843298-f4a3-4732-a292-04ffedbafc9a' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  8f843298-f4a3-4732-a292-04ffedbafc9a
        else
          search --no-floppy --fs-uuid --set=root 8f843298-f4a3-4732-a292-04ffedbafc9a
        fi
        echo    'Loading Linux 3.8.0-35-generic ...'
        linux    /boot/vmlinuz-3.8.0-35-generic.efi.signed root=UUID=8f843298-f4a3-4732-a292-04ffedbafc9a ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-34-generic-advanced-8f843298-f4a3-4732-a292-04ffedbafc9a' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  8f843298-f4a3-4732-a292-04ffedbafc9a
        else
          search --no-floppy --fs-uuid --set=root 8f843298-f4a3-4732-a292-04ffedbafc9a
        fi
        echo    'Loading Linux 3.8.0-34-generic ...'
        linux    /boot/vmlinuz-3.8.0-34-generic.efi.signed root=UUID=8f843298-f4a3-4732-a292-04ffedbafc9a ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-34-generic-recovery-8f843298-f4a3-4732-a292-04ffedbafc9a' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  8f843298-f4a3-4732-a292-04ffedbafc9a
        else
          search --no-floppy --fs-uuid --set=root 8f843298-f4a3-4732-a292-04ffedbafc9a
        fi
        echo    'Loading Linux 3.8.0-34-generic ...'
        linux    /boot/vmlinuz-3.8.0-34-generic.efi.signed root=UUID=8f843298-f4a3-4732-a292-04ffedbafc9a ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-advanced-8f843298-f4a3-4732-a292-04ffedbafc9a' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  8f843298-f4a3-4732-a292-04ffedbafc9a
        else
          search --no-floppy --fs-uuid --set=root 8f843298-f4a3-4732-a292-04ffedbafc9a
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=8f843298-f4a3-4732-a292-04ffedbafc9a ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-19-generic-recovery-8f843298-f4a3-4732-a292-04ffedbafc9a' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  8f843298-f4a3-4732-a292-04ffedbafc9a
        else
          search --no-floppy --fs-uuid --set=root 8f843298-f4a3-4732-a292-04ffedbafc9a
        fi
        echo    'Loading Linux 3.8.0-19-generic ...'
        linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=8f843298-f4a3-4732-a292-04ffedbafc9a ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-19-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root E033-0FEC
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root E033-0FEC
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root E033-0FEC
chainloader (${root})/EFI/ubuntu/MokManager.efi
}

menuentry "EFI/OEM/Boot/bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root E033-0FEC
chainloader (${root})/EFI/OEM/Boot/bootmgfw.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Linux Mint 13 Maya (13)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-479d91ad-9ae9-4a17-89fd-030ba74ef017' {
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  479d91ad-9ae9-4a17-89fd-030ba74ef017
    else
      search --no-floppy --fs-uuid --set=root 479d91ad-9ae9-4a17-89fd-030ba74ef017
    fi
    linux /boot/vmlinuz-3.2.0-57-generic root=UUID=479d91ad-9ae9-4a17-89fd-030ba74ef017 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-57-generic
}
submenu 'Advanced options for Linux Mint 13 Maya (13)' $menuentry_id_option 'osprober-gnulinux-advanced-479d91ad-9ae9-4a17-89fd-030ba74ef017' {
    menuentry 'LinuxMint, with Linux 3.2.0-57-generic (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-57-generic--479d91ad-9ae9-4a17-89fd-030ba74ef017' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  479d91ad-9ae9-4a17-89fd-030ba74ef017
        else
          search --no-floppy --fs-uuid --set=root 479d91ad-9ae9-4a17-89fd-030ba74ef017
        fi
        linux /boot/vmlinuz-3.2.0-57-generic root=UUID=479d91ad-9ae9-4a17-89fd-030ba74ef017 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-57-generic
    }
    menuentry 'LinuxMint, with Linux 3.2.0-57-generic (recovery mode) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-57-generic-root=UUID=479d91ad-9ae9-4a17-89fd-030ba74ef017 ro recovery nomodeset-479d91ad-9ae9-4a17-89fd-030ba74ef017' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  479d91ad-9ae9-4a17-89fd-030ba74ef017
        else
          search --no-floppy --fs-uuid --set=root 479d91ad-9ae9-4a17-89fd-030ba74ef017
        fi
        linux /boot/vmlinuz-3.2.0-57-generic root=UUID=479d91ad-9ae9-4a17-89fd-030ba74ef017 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-57-generic
    }
    menuentry 'LinuxMint, with Linux 3.2.0-56-generic (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-56-generic--479d91ad-9ae9-4a17-89fd-030ba74ef017' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  479d91ad-9ae9-4a17-89fd-030ba74ef017
        else
          search --no-floppy --fs-uuid --set=root 479d91ad-9ae9-4a17-89fd-030ba74ef017
        fi
        linux /boot/vmlinuz-3.2.0-56-generic root=UUID=479d91ad-9ae9-4a17-89fd-030ba74ef017 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-56-generic
    }
    menuentry 'LinuxMint, with Linux 3.2.0-56-generic (recovery mode) (on /dev/sda7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-56-generic-root=UUID=479d91ad-9ae9-4a17-89fd-030ba74ef017 ro recovery nomodeset-479d91ad-9ae9-4a17-89fd-030ba74ef017' {
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  479d91ad-9ae9-4a17-89fd-030ba74ef017
        else
          search --no-floppy --fs-uuid --set=root 479d91ad-9ae9-4a17-89fd-030ba74ef017
        fi
        linux /boot/vmlinuz-3.2.0-56-generic root=UUID=479d91ad-9ae9-4a17-89fd-030ba74ef017 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-56-generic
    }
}

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

=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb9 during installation
UUID=8f843298-f4a3-4732-a292-04ffedbafc9a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb2 during installation
#UUID=E033-0FEC  /boot/efi       vfat    defaults        0       1
/dev/sdb8       none            swap    sw              0       0

# data was on /dev/sda6 during startup
UUID=01CEE3DE243B3D30    /media/data    ntfs-3g        defaults,locale=en_UK.utf8    0    0
UUID=E033-0FEC    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 459.031108856 = 492.880900096  boot/grub/grub.cfg                             1
 447.063583374 = 480.030867456  boot/vmlinuz-3.8.0-19-generic                  1
 446.407341003 = 479.326232576  boot/vmlinuz-3.8.0-34-generic                  2
 453.911251068 = 487.383494656  boot/vmlinuz-3.8.0-34-generic.efi.signed       2
 457.559711456 = 491.300999168  boot/vmlinuz-3.8.0-35-generic                  1
 456.415180206 = 490.072068096  boot/vmlinuz-3.8.0-35-generic.efi.signed       2
 457.559711456 = 491.300999168  vmlinuz                                        1
 457.559711456 = 491.300999168  vmlinuz.old                                    1
 446.112705231 = 479.009869824  boot/initrd.img-3.8.0-19-generic               1
 447.354953766 = 480.343724032  boot/initrd.img-3.8.0-34-generic               1
 456.440952301 = 490.099740672  boot/initrd.img-3.8.0-35-generic               1
 456.440952301 = 490.099740672  initrd.img                                     1
 456.440952301 = 490.099740672  initrd.img.old                                 1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
5850cbb887c11947baf0379ca2d4c97e


ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-12-24__18h26 ===================
boot-repair version : 3.199~ppa39~raring
boot-sav version : 3.199~ppa39~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.199~ppa39~raring
boot-repair is executed in installed-session (Ubuntu 13.04, raring, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.8.0-35-generic.efi.signed root=UUID=8f843298-f4a3-4732-a292-04ffedbafc9a ro quiet splash vt.handoff=7
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda1 : Error code 14
mount -r /dev/sda1 /mnt/boot-sav/sda1
Windows is hibernated, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda4 /mnt/boot-sav/sda4
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda4 : Error code 14
mount -r /dev/sda4 /mnt/boot-sav/sda4
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda5 /mnt/boot-sav/sda5
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda5': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda5 : Error code 14
mount -r /dev/sda5 /mnt/boot-sav/sda5
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda6': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda6 /mnt/boot-sav/sda6
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda6': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount /dev/sda6 : Error code 14
mount -r /dev/sda6 /mnt/boot-sav/sda6

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda9:The OS now in use - Ubuntu 13.04 CurrentSession:linux
/dev/sda7:Linux Mint 13 Maya (13):LinuxMint:linux

=================== blkid:
/dev/sda1: LABEL="Recovery" UUID="5E4430A244307EB9" TYPE="ntfs"
/dev/sda2: LABEL="ESP" UUID="E033-0FEC" TYPE="vfat"
/dev/sda4: LABEL="Acer" UUID="01CEE3DD305B9930" TYPE="ntfs"
/dev/sda5: LABEL="Push Button Reset" UUID="01CEE3DE239B7AC0" TYPE="ntfs"
/dev/sda6: LABEL="data" UUID="01CEE3DE243B3D30" TYPE="ntfs"
/dev/sda7: UUID="479d91ad-9ae9-4a17-89fd-030ba74ef017" TYPE="ext4"
/dev/sda8: TYPE="swap"
/dev/sda9: UUID="8f843298-f4a3-4732-a292-04ffedbafc9a" TYPE="ext4"


1 disks with OS, 2 OS : 2 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda4.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== /etc/grub.d/ :
drwxr-xr-x 2 root root     4096 Dec 12 11:37 grub.d
drwxr-xr-x 2 root root     4096 Dec 11 23:47 grub.d.bak
total 72
-rwxr-xr-x 1 root root  7541 Apr  9  2013 00_header
-rwxr-xr-x 1 root root  5974 Apr  9  2013 05_debian_theme
-rwxr-xr-x 1 root root 11381 Apr  9  2013 10_linux
-rwxr-xr-x 1 root root 10258 Apr  9  2013 20_linux_xen
-rwxr-xr-x 1 root root   602 Dec 12 11:37 25_custom
-rwxr-xr-x 1 root root 10976 Apr  9  2013 30_os-prober
-rwxr-xr-x 1 root root  1426 Apr  9  2013 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  9  2013 40_custom
-rwxr-xr-x 1 root root   216 Apr  9  2013 41_custom
-rw-r--r-- 1 root root   483 Apr  9  2013 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="Ubuntu"
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=4
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



/boot/efi detected in the fstab of sda9: UUID=E033-0FEC     (sda2)

=================== sda9saved_entry=Ubuntu/grub/grubenv :
saved_entry=Ubuntu



Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bootx64.efi
Presence of .bkp file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of .bkp file detected: /boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi

=================== sda7/etc/grub.d/ :
drwxr-xr-x 2 root root     4096 Dec 12 11:18 grub.d
drwxr-xr-x 2 root root     4096 Dec  7 12:46 grub.d.bak
total 60
-rwxr-xr-x 1 root root 6743 Jul 20 00:29 00_header
-rwxr-xr-x 1 root root 5522 Jul 20 00:15 05_debian_theme
-rwxr-xr-x 1 root root 7500 Dec 20 18:05 10_linux
-rwxr-xr-x 1 root root 6335 Jul 20 00:29 20_linux_xen
-rwxr-xr-x 1 root root  602 Dec 12 11:18 25_custom
-rwxr-xr-x 1 root root 7603 Jul 20 00:29 30_os-prober
-rwxr-xr-x 1 root root 1388 Jul 20 00:29 30_uefi-firmware
-rwxr-xr-x 1 root root  214 Jul 20 00:29 40_custom
-rwxr-xr-x 1 root root   95 Jul 20 00:29 41_custom
-rw-r--r-- 1 root root  483 Jul 20 00:29 README




=================== sda7/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=4
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



/boot/efi detected in the fstab of sda7: UUID=E033-0FEC     (sda2)

efibootmgr -v
BootCurrent: 0002
BootOrder: 0002,0001,0004,0000
Boot0000* Windows Boot Manager    HD(2,c8800,96000,4bf537cc-15d7-4e1b-a0c8-e57b75b9ebe6)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...-................
Boot0001* linuxmint    HD(2,c8800,96000,4bf537cc-15d7-4e1b-a0c8-e57b75b9ebe6)File(EFIlinuxmintshimx64.efi)
Boot0002* ubuntu    HD(2,c8800,96000,4bf537cc-15d7-4e1b-a0c8-e57b75b9ebe6)File(EFIubuntushimx64.efi)
Boot0004* HDD:     HD(2,c8800,96000,4bf537cc-15d7-4e1b-a0c8-e57b75b9ebe6)File(EFIubuntugrubx64.efi)RC
=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda9    : sda,    not-sepboot,    grubenv-ng    grub2,    signed grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /boot/efi.
sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda4.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda5.
sda6    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda6.
sda7    : sda,    not-sepboot,    grubenv-ok    grub2,    signed grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda7.

sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA ST500LT012-9WS14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size    File system     Name                          Flags
1      1049kB  420MB  419MB   ntfs            Basic data partition          hidden, diag
2      420MB   735MB  315MB   fat32           EFI system partition          boot
3      735MB   869MB  134MB                   Microsoft reserved partition  msftres
4      869MB   107GB  106GB   ntfs            Basic data partition
5      107GB   123GB  16.6GB  ntfs            Basic data partition          hidden, diag
6      123GB   445GB  322GB   ntfs            Basic data partition
7      445GB   477GB  32.0GB  ext4            Basic data partition
9      477GB   498GB  20.7GB  ext4
8      498GB   500GB  2051MB  linux-swap(v1)  Basic data partition


Model: ATA KINGSTON SMS151S (scsi)
Disk /dev/sdb: 24.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
1      1049kB  8010MB  8009MB               Basic data partition
2      8010MB  24.0GB  16.0GB               Basic data partition

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:gpt:ATA ST500LT012-9WS14;
1:1049kB:420MB:419MB:ntfs:Basic data partition:hidden, diag;
2:420MB:735MB:315MB:fat32:EFI system partition:boot;
3:735MB:869MB:134MB::Microsoft reserved partition:msftres;
4:869MB:107GB:106GB:ntfs:Basic data partition:;
5:107GB:123GB:16.6GB:ntfs:Basic data partition:hidden, diag;
6:123GB:445GB:322GB:ntfs:Basic data partition:;
7:445GB:477GB:32.0GB:ext4:Basic data partition:;
9:477GB:498GB:20.7GB:ext4::;
8:498GB:500GB:2051MB:linux-swap(v1):Basic data partition:;

BYT;
/dev/sdb:24.0GB:scsi:512:512:gpt:ATA KINGSTON SMS151S;
1:1049kB:8010MB:8009MB::Basic data partition:;
2:8010MB:24.0GB:16.0GB::Basic data partition:;


=================== mount:
/dev/sda9 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sda2 on /boot/efi type vfat (rw)
gvfsd-fuse on /run/user/yago/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=yago)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type fuseblk (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd full fuse hidraw0 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 sdb sdb1 sdb2 sg0 sg1 shm snapshot snd stderr stdin stdout uinput urandom usb v4l vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 7f 0c 00 00 00 00 00  |................|
00000030  55 85 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U...............|
00000040  f6 00 00 00 01 00 00 00  b9 7e 30 44 a2 30 44 5e  |.........~0D.0D^|
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
ls /boot/efi/1:

=================== hexdump -n512 -C /dev/sda2
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 5e 1b  |.X.MSDOS5.0...^.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 88 0c 00  |........?.......|
00000020  00 60 09 00 51 02 00 00  00 00 00 00 02 00 00 00  |.`..Q...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 ec 0f 33 e0 4e  4f 20 4e 41 4d 45 20 20  |..)..3.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 e8 19 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  f8 cf 4c 0c 00 00 00 00  |..........L.....|
00000030  3c 1a b5 00 00 00 00 00  2e 2b 01 00 00 00 00 00  |<........+......|
00000040  f6 00 00 00 01 00 00 00  30 99 5b 30 dd e3 ce 01  |........0.[0....|
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

=================== hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 b8 66 0c  |........?.....f.|
00000020  00 00 00 00 80 00 80 00  f8 ff ef 01 00 00 00 00  |................|
00000030  f1 22 00 00 00 00 00 00  f7 01 00 00 00 00 00 00  |."..............|
00000040  f6 00 00 00 01 00 00 00  c0 7a 9b 23 de e3 ce 01  |.........z.#....|
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

=================== hexdump -n512 -C /dev/sda6
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 b8 56 0e  |........?.....V.|
00000020  00 00 00 00 80 00 80 00  f8 77 82 25 00 00 00 00  |.........w.%....|
00000030  0c 00 00 00 00 00 00 00  0b 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  30 3d 3b 24 de e3 ce 01  |........0=;$....|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda9      ext4       19G  9.7G  8.2G  55% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  5.8G   12K  5.8G   1% /dev
tmpfs          tmpfs     1.2G  976K  1.2G   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     5.9G  248K  5.9G   1% /run/shm
none           tmpfs     100M   16K  100M   1% /run/user
/dev/sda2      vfat      296M   57M  240M  20% /boot/efi
/dev/sda1      fuseblk   400M  256M  145M  64% /mnt/boot-sav/sda1
/dev/sda4      fuseblk    99G   53G   47G  53% /mnt/boot-sav/sda4
/dev/sda5      fuseblk    16G   14G  2.4G  86% /mnt/boot-sav/sda5
/dev/sda6      fuseblk   301G  121G  180G  41% /mnt/boot-sav/sda6
/dev/sda7      ext4       30G  9.4G   19G  34% /mnt/boot-sav/sda7

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x655e9ed9

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 24.0 GB, 24015495168 bytes
256 heads, 63 sectors/track, 2908 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2a1f61b0

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT


EFI detected. Please check the options.
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sda2/efi/.../grub*.efi file!

The boot files of [The OS now in use - Ubuntu 13.04] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

You may want to retry after activating the [Backup and rename Windows EFI files] option.

=================== Default settings
Recommended-Repair
This setting would reinstall the grub-efi-amd64-signed of sda9, using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.[/code]
Anyway, I hope this is something someone can help me with. I'd reaaally appreciate it because I want to remove the installation of Maya and stay with Raring as soon as possible.

Thanks in advance!! :D

---

### Post by QIII on 2013-12-24
Do you have fast boot enabled?

If you do, then Windows is not actually shut down, but hibernating.  You will encounter this if Windows had that drive mounted when it was "shut down" under fast boot.

---

### Post by oldfred on 2013-12-24
Boot-Repair says this on several of your partitions.

> The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.


---

### Post by yagolf on 2013-12-30
Thanks guys, at the end it was the 'fast restart' setting that was still on (I must have ticked it back on by mistake... :-# )

---

