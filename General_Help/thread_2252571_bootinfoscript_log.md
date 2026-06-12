---
title: "bootinfoscript log"
date: 2014-11-12
forum: General Help
---

### Post by rob110 on 2014-11-12
I was wondering if you guys could help me with this. I tried upgrading buntu 13 to 14 and it errored a bunch. Then it wouldnt load grub or anything else. I have been through countless threads trying to resolve this. I reinstalled buntu 14 and have a grub menu now with only buntu. I would love to get into windows so I can do my homework!

the files are availabe in ubuntu, but I cant boot into windows7

here is boot info script results

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

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
/dev/sda1           2,048       206,847       204,800 Data partition (Windows/Linux)
/dev/sda2         206,848   683,245,357   683,038,510 Data partition (Windows/Linux)
/dev/sda3     683,245,568   960,954,367   277,708,800 Data partition (Linux)
/dev/sda4     960,954,368   961,148,927       194,560 EFI System partition
/dev/sda5     976,771,072   976,773,119         2,048 Data partition (Linux)
/dev/sda6     961,148,928   976,750,591    15,601,664 Swap partition (Linux)
/dev/sda7     976,750,592   976,771,071        20,480 BIOS Boot partition

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204885504 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        D01AA4BE1AA4A2C8                       ntfs       System Reserved
/dev/sda2        68B0A714B0A6E7B0                       ntfs       
/dev/sda3        09b5d2d0-c658-4038-9757-1ea59a4b5798   ext4       
/dev/sda4        1BE6-C201                              vfat       
/dev/sda6        c6bf2118-2703-4e26-9ddd-5f189c61713c   swap       
/dev/sdb1        FC5C98455C97F89A                       ntfs       Seagate Backup Plus Drive
/dev/sr0                                                iso9660    rEFInd_0.8.3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /media/rob/68B0A714B0A6E7B0 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/rob/Seagate Backup Plus Drive fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr0         /media/rob/rEFInd_0.8.3  iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks2)


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
set root='hd0,gpt3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  09b5d2d0-c658-4038-9757-1ea59a4b5798
else
  search --no-floppy --fs-uuid --set=root 09b5d2d0-c658-4038-9757-1ea59a4b5798
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
  set timeout=-1
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-09b5d2d0-c658-4038-9757-1ea59a4b5798' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  09b5d2d0-c658-4038-9757-1ea59a4b5798
    else
      search --no-floppy --fs-uuid --set=root 09b5d2d0-c658-4038-9757-1ea59a4b5798
    fi
    linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=09b5d2d0-c658-4038-9757-1ea59a4b5798 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-39-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-09b5d2d0-c658-4038-9757-1ea59a4b5798' {
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-advanced-09b5d2d0-c658-4038-9757-1ea59a4b5798' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  09b5d2d0-c658-4038-9757-1ea59a4b5798
        else
          search --no-floppy --fs-uuid --set=root 09b5d2d0-c658-4038-9757-1ea59a4b5798
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=09b5d2d0-c658-4038-9757-1ea59a4b5798 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-recovery-09b5d2d0-c658-4038-9757-1ea59a4b5798' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  09b5d2d0-c658-4038-9757-1ea59a4b5798
        else
          search --no-floppy --fs-uuid --set=root 09b5d2d0-c658-4038-9757-1ea59a4b5798
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=09b5d2d0-c658-4038-9757-1ea59a4b5798 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-09b5d2d0-c658-4038-9757-1ea59a4b5798' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  09b5d2d0-c658-4038-9757-1ea59a4b5798
        else
          search --no-floppy --fs-uuid --set=root 09b5d2d0-c658-4038-9757-1ea59a4b5798
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=09b5d2d0-c658-4038-9757-1ea59a4b5798 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-09b5d2d0-c658-4038-9757-1ea59a4b5798' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3 --hint-baremetal=ahci0,gpt3  09b5d2d0-c658-4038-9757-1ea59a4b5798
        else
          search --no-floppy --fs-uuid --set=root 09b5d2d0-c658-4038-9757-1ea59a4b5798
        fi
        echo    'Loading Linux 3.13.0-32-generic ...'
        linux    /boot/vmlinuz-3.13.0-32-generic root=UUID=09b5d2d0-c658-4038-9757-1ea59a4b5798 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-32-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=09b5d2d0-c658-4038-9757-1ea59a4b5798 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda4 during installation
#UUID=1BE6-C201  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda6 during installation
UUID=c6bf2118-2703-4e26-9ddd-5f189c61713c none            swap    sw              0       0
#UUID=1BE6-C201    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-DX0rg23O/Tmp_Log: No such file or directory


```

---

### Post by rob110 on 2014-11-12
I finally just booted into windows.. somehow.. it boots right into windows now though..let's see if I can get grub back and have the option for both.

suggestions?

---

### Post by yancek on 2014-11-12
In your initial post, you indicate you cannot boot windows yet the first line of the bootinfoscript indicates windows on the master boot record?  Reading further in the bootinfoscript, you seem to have windows 7 installed on the same drive as Ubuntu and xp on another drive.  The problem is that you appear to have windows 7 installed in MBR mode and Ubuntu in UEFI.  Take a look at the info for sda4 in your bootinfoscript and you will see Ubuntu efi files. If windows were installed EFI, its files would also be there.  Usually, you need to install both systems either MBR or EFI and they don't mix so you need to decide which you want.  Probably it would be easier to install Ubuntu again in MBR and not EFI mode.

---

### Post by oldfred on 2014-11-12
I am not sure how you are booting?

Windows only boots from gpt partitioned drives with UEFI.
Windows & Ubuntu only boot from MBR partitioned drives with BIOS.

But it looks like you had a BIOS boot install of Windows on sda, and now drive is converted to gpt. And it has both an efi partition for UEFI boot and a bios_grub partition for BIOS/CSM boot of Ubuntu. Ubuntu will boot in either mode from gpt partitioned drives.

Is your system actually using the Windows boot partition on the sdb drive which is MBR and it boots the Windows installed on the gpt drive? Very surprised that would work, but some have used boot repair to force Ubuntu to do something similar. Either case is very non-standard.

---

