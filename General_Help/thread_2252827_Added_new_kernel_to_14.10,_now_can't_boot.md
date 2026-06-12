---
title: "Added new kernel to 14.10, now can't boot"
date: 2014-11-14
forum: General Help
---

### Post by 7-webmaster on 2014-11-14
My laptop does not resume properly since going to 14.10.  I was told to install kernel 3.18  and try again to see if the problem was already fixed.  So I followed the instructions for installing kernel 3.18 and now I cannot boot ANY version of Linux.  I get the following:

Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - check rootdelay=
   - check root=
 - missing modules (cat /proc/modules; ls /dev
ALERT! /dev/disk/by-uuid/5850nfcs-8269-4a92-8fda-798e6557b0bd does not exist
Dropping to a shell

/proc/cmdline, of course, points to the device complained about by the ALERT, which is, in fact, the location where Ubuntu 14.10 is installed.
 ls /dev/s* shows no disk drives.  There is no directory /dev/disk

I ran Rescatux to rebuild the Grub files, but the problem remains the same.

I ran Rescatux to perform a complete Boot repair, but the problem remains the same.

When I boot Ubuntu from a live DVD it has no problem finding /dev/disk/by-uuid/5850nfcs-8269-4a92-8fda-798e6557b0bd.

What else can I do?

                                   
[LIST]
[*]Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]
 
 
```
============================= Boot Info Summary: ===============================
 
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 129 for .
 
sda1: __________________________________________________________________________
 
    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM
 
sda2: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD
 
sda3: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe
 
sda4: __________________________________________________________________________
 
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 
 
sda5: __________________________________________________________________________
 
    File system:       swap
    Boot sector type:  -
    Boot sector info: 
 
sda6: __________________________________________________________________________
 
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img
 
============================ Drive/Partition Info: =============================
 
Drive: sda _____________________________________________________________________
 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2    *        206,848    41,166,847    40,960,000   7 NTFS / exFAT / HPFS
/dev/sda3          41,166,848   206,819,162   165,652,315   7 NTFS / exFAT / HPFS
/dev/sda4         206,819,326   976,771,071   769,951,746   5 Extended
/dev/sda5         965,289,984   976,771,071    11,481,088  82 Linux swap / Solaris
/dev/sda6         206,819,328   965,289,983   758,470,656  83 Linux
 
 
"blkid" output: ________________________________________________________________
 
Device           UUID                                   TYPE       LABEL
 
/dev/loop0                                              iso9660    Debian wheezy 20140616-02:36
/dev/loop1                                              squashfs   
/dev/sda1        3030-3030                              vfat       DELLUTILITY
/dev/sda2        CC70378A703779F2                       ntfs       Recovery
/dev/sda3        AC7C4EC27C4E86D4                       ntfs       OS
/dev/sda5        e1d460c4-e29e-470e-a302-7891166d98f7   swap       
/dev/sda6        5850bfca-8269-4a92-8fda-798e6557b0bd   ext4       
/dev/sr0                                                iso9660    LXFDVD188
 
================================ Mount points: =================================
 
Device           Mount_Point              Type       Options
 
/dev/loop0       /lib/live/mount/medium   iso9660    (ro,noatime)
/dev/loop1       /lib/live/mount/rootfs/filesystem.squashfs squashfs   (ro,noatime)
/dev/sr0         /lib/live/mount/findiso  iso9660    (ro,noatime)
 
 
=========================== sda6/boot/grub/grub.cfg: ===========================
 
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
set root='hd0,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
else
  search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
fi
    font="/usr/share/grub/unicode.pf2"
fi
 
if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-5850bfca-8269-4a92-8fda-798e6557b0bd' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
    else
      search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
    fi
    linux    /boot/vmlinuz-3.18.0-031800rc2-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.18.0-031800rc2-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
    menuentry 'Ubuntu, with Linux 3.18.0-031800rc2-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-031800rc2-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.18.0-031800rc2-generic ...'
        linux    /boot/vmlinuz-3.18.0-031800rc2-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.18.0-031800rc2-generic
    }
    menuentry 'Ubuntu, with Linux 3.18.0-031800rc2-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.18.0-031800rc2-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.18.0-031800rc2-generic ...'
        linux    /boot/vmlinuz-3.18.0-031800rc2-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.18.0-031800rc2-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-24-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.16.0-24-generic ...'
        linux    /boot/vmlinuz-3.16.0-24-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-24-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.16.0-24-generic ...'
        linux    /boot/vmlinuz-3.16.0-24-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-19-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.11.0-19-generic ...'
        linux    /boot/vmlinuz-3.11.0-19-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-19-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.11.0-19-generic ...'
        linux    /boot/vmlinuz-3.11.0-19-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-32-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.8.0-32-generic ...'
        linux    /boot/vmlinuz-3.8.0-32-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-32-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.8.0-32-generic ...'
        linux    /boot/vmlinuz-3.8.0-32-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-28-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-28-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.5.0-28-generic ...'
        linux    /boot/vmlinuz-3.5.0-28-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-28-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-28-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.5.0-28-generic ...'
        linux    /boot/vmlinuz-3.5.0-28-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-28-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-35-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-35-generic ...'
        linux    /boot/vmlinuz-3.2.0-35-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-35-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-35-generic ...'
        linux    /boot/vmlinuz-3.2.0-35-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-35-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-34-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-34-generic ...'
        linux    /boot/vmlinuz-3.2.0-34-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-34-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-34-generic ...'
        linux    /boot/vmlinuz-3.2.0-34-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-33-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-33-generic ...'
        linux    /boot/vmlinuz-3.2.0-33-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-33-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-33-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-33-generic ...'
        linux    /boot/vmlinuz-3.2.0-33-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-33-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-32-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-32-generic ...'
        linux    /boot/vmlinuz-3.2.0-32-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-32-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-32-generic ...'
        linux    /boot/vmlinuz-3.2.0-32-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-32-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-31-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-31-generic ...'
        linux    /boot/vmlinuz-3.2.0-31-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-31-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-31-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-31-generic ...'
        linux    /boot/vmlinuz-3.2.0-31-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-31-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-30-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-30-generic ...'
        linux    /boot/vmlinuz-3.2.0-30-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-30-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-30-generic ...'
        linux    /boot/vmlinuz-3.2.0-30-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-29-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-29-generic ...'
        linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-29-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-29-generic ...'
        linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-27-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-27-generic ...'
        linux    /boot/vmlinuz-3.2.0-27-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-27-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-27-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-27-generic ...'
        linux    /boot/vmlinuz-3.2.0-27-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-27-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-26-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-26-generic ...'
        linux    /boot/vmlinuz-3.2.0-26-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-26-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-26-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-26-generic ...'
        linux    /boot/vmlinuz-3.2.0-26-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-26-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-25-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-25-generic ...'
        linux    /boot/vmlinuz-3.2.0-25-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-25-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-25-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-25-generic ...'
        linux    /boot/vmlinuz-3.2.0-25-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-25-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-24-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-24-generic ...'
        linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-24-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-24-generic ...'
        linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-23-generic-advanced-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-23-generic ...'
        linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-23-generic-recovery-5850bfca-8269-4a92-8fda-798e6557b0bd' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
        else
          search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
        fi
        echo    'Loading Linux 3.2.0-23-generic ...'
        linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=5850bfca-8269-4a92-8fda-798e6557b0bd ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-23-generic
    }
}
 
### END /etc/grub.d/10_linux ###
 
### BEGIN /etc/grub.d/20_linux_xen ###
 
### END /etc/grub.d/20_linux_xen ###
 
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
    else
      search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos6'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6 --hint='hd0,msdos6'  5850bfca-8269-4a92-8fda-798e6557b0bd
    else
      search --no-floppy --fs-uuid --set=root 5850bfca-8269-4a92-8fda-798e6557b0bd
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-CC70378A703779F2' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2 --hint='hd0,msdos2'  CC70378A703779F2
    else
      search --no-floppy --fs-uuid --set=root CC70378A703779F2
    fi
    parttool ${root} hidden-
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-AC7C4EC27C4E86D4' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3 --hint='hd0,msdos3'  AC7C4EC27C4E86D4
    else
      search --no-floppy --fs-uuid --set=root AC7C4EC27C4E86D4
    fi
    parttool ${root} hidden-
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
 
=============================== sda6/etc/fstab: ================================
 
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=5850bfca-8269-4a92-8fda-798e6557b0bd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e1d460c4-e29e-470e-a302-7891166d98f7 none            swap    sw              0       0
--------------------------------------------------------------------------------
 
=================== sda6: Location of files loaded by Grub: ====================
 
           GiB - GB             File                                 Fragment(s)
 
 182.777667999 = 196.256026624  boot/grub/grub.cfg                             1
 242.857501984 = 260.766257152  boot/grub/i386-pc/core.img                     1
 278.085327148 = 298.591846400  boot/vmlinuz-3.11.0-19-generic                 1
 165.741741180 = 177.963839488  boot/vmlinuz-3.13.0-39-generic                 1
 171.875102997 = 184.549486592  boot/vmlinuz-3.16.0-24-generic                 1
 256.539985657 = 275.457712128  boot/vmlinuz-3.18.0-031800rc2-generic          1
 182.769611359 = 196.247375872  boot/vmlinuz-3.2.0-23-generic                  1
 113.100330353 = 121.440555008  boot/vmlinuz-3.2.0-24-generic                  2
 237.291740417 = 254.790066176  boot/vmlinuz-3.2.0-25-generic                  1
 237.936260223 = 255.482114048  boot/vmlinuz-3.2.0-26-generic                  1
 243.236328125 = 261.173018624  boot/vmlinuz-3.2.0-27-generic                  2
 242.932357788 = 260.846632960  boot/vmlinuz-3.2.0-29-generic                  2
 244.061264038 = 262.058786816  boot/vmlinuz-3.2.0-30-generic                  1
 256.174545288 = 275.065323520  boot/vmlinuz-3.2.0-31-generic                  1
 100.030017853 = 107.406413824  boot/vmlinuz-3.2.0-32-generic                  1
 254.490955353 = 273.257582592  boot/vmlinuz-3.2.0-33-generic                  1
 117.405017853 = 126.062678016  boot/vmlinuz-3.2.0-34-generic                  1
 161.299549103 = 173.194072064  boot/vmlinuz-3.2.0-35-generic                  2
 117.455951691 = 126.117367808  boot/vmlinuz-3.5.0-28-generic                  2
 257.928825378 = 276.948967424  boot/vmlinuz-3.8.0-32-generic                  1
 256.539985657 = 275.457712128  vmlinuz                                        1
 171.875102997 = 184.549486592  vmlinuz.old                                    1
 271.314453125 = 291.321675776  boot/initrd.img-3.11.0-19-generic              3
 168.267578125 = 180.675936256  boot/initrd.img-3.13.0-39-generic              2
 173.008464813 = 185.766424576  boot/initrd.img-3.16.0-24-generic              3
 182.872562408 = 196.357918720  boot/initrd.img-3.18.0-031800rc2-generic       1
 113.147964478 = 121.491701760  boot/initrd.img-3.2.0-23-generic               1
 119.999526978 = 128.848510976  boot/initrd.img-3.2.0-24-generic               2
 236.384670258 = 253.816107008  boot/initrd.img-3.2.0-25-generic               2
 238.046421051 = 255.600398336  boot/initrd.img-3.2.0-26-generic               1
 243.624557495 = 261.589876736  boot/initrd.img-3.2.0-27-generic               2
 244.007369995 = 262.000918528  boot/initrd.img-3.2.0-29-generic               1
 244.390151978 = 262.411927552  boot/initrd.img-3.2.0-30-generic               2
 242.669963837 = 260.564889600  boot/initrd.img-3.2.0-31-generic               2
 236.671939850 = 254.124560384  boot/initrd.img-3.2.0-32-generic               2
 156.658882141 = 168.211193856  boot/initrd.img-3.2.0-33-generic               2
 100.663444519 = 108.086550528  boot/initrd.img-3.2.0-34-generic               2
 248.437061310 = 266.757263360  boot/initrd.img-3.2.0-35-generic               2
  98.891349792 = 106.183778304  boot/initrd.img-3.5.0-28-generic               2
 274.110973358 = 294.324416512  boot/initrd.img-3.8.0-32-generic               1
 182.872562408 = 196.357918720  initrd.img                                     1
 173.008464813 = 185.766424576  initrd.img.old                                 3
 
=============================== StdErr Messages: ===============================
 
File descriptor 6 (/proc/4097/mounts) leaked on lvscan invocation. Parent PID 18309: bash
  No volume groups found
mdadm: No arrays found in config file or automatically
 
ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-11-15__04h23 ===================
boot-repair version : 3.199~ppa40~precise
boot-sav version : 3.199~ppa40~precise
glade2script version : 3.2.2~ppa45~precise
boot-sav-extra version : 3.199~ppa40~precise
File descriptor 6 (/proc/4097/mounts) leaked on lvs invocation. Parent PID 5580: /bin/sh
No volume groups found
boot-repair is executed in live-session (Debian GNU/Linux 7.5 (wheezy), wheezy, Debian, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=(loop)/live/vmlinuz1 findiso=/Rescatux/rescatux_cdrom_usb_hybrid_i386_amd64-486_0.32b1.iso boot=live config quiet splash
 
=================== os-prober:
/dev/sda2:Windows 7 (loader):Windows:chain
/dev/sda6:Ubuntu 14.10 (14.10):Ubuntu:linux
 
=================== blkid:
/dev/sda1: SEC_TYPE="msdos" LABEL="DELLUTILITY" UUID="3030-3030" TYPE="vfat"
/dev/sda2: LABEL="Recovery" UUID="CC70378A703779F2" TYPE="ntfs"
/dev/sda3: LABEL="OS" UUID="AC7C4EC27C4E86D4" TYPE="ntfs"
/dev/sda5: UUID="e1d460c4-e29e-470e-a302-7891166d98f7" TYPE="swap"
/dev/sda6: UUID="5850bfca-8269-4a92-8fda-798e6557b0bd" TYPE="ext4"
/dev/sr0: LABEL="LXFDVD188" TYPE="iso9660"
/dev/loop0: LABEL="Debian wheezy 20140616-02:36" TYPE="iso9660"
/dev/loop1: TYPE="squashfs"
 
 
1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.
 
Windows not detected by os-prober on sda3.
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
 
=================== sda6/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Nov 12 01:17 grub.d
total 76
-rwxr-xr-x 1 root root  9424 Apr 11  2014 00_header
-rwxr-xr-x 1 root root  6058 Apr 10  2014 05_debian_theme
-rwxr-xr-x 1 root root 11611 Oct 16 09:48 10_linux
-rwxr-xr-x 1 root root 10418 Oct 16 09:48 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr 11  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr 11  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 14  2012 40_custom
-rwxr-xr-x 1 root root   216 Oct 14  2012 41_custom
-rw-r--r-- 1 root root   483 Oct 14  2012 README
 
 
 
 
=================== sda6/etc/default/grub :
 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'
 
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
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
 
 
 
 
=================== sda6recordfail=1/grub/grubenv :
recordfail=1
 
 
 
=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.
 
 
=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,     notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,     is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,     part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,     notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sda6    : sda,    not-sepboot,    grubenv-ng    grub2,    grub-pc ,    update-grub,     64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,     fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,     notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,     not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda6.
 
sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
 
 
=================== parted -l:
 
Model: ATA ST9500325AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
 
Number  Start   End     Size    Type      File system     Flags
1      1049kB  106MB   105MB   primary   fat16           diag
2      106MB   21.1GB  21.0GB  primary   ntfs            boot
3      21.1GB  106GB   84.8GB  primary   ntfs
4      106GB   500GB   394GB   extended
6      106GB   494GB   388GB   logical   ext4
5      494GB   500GB   5878MB  logical   linux-swap(v1)
 
 
 
                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
 
                                                                          
Warning: The driver descriptor says the physical block size is 512 bytes, but
Linux says it is 2048 bytes.
 
=================== parted -lm:
 
BYT;
/dev/sda:500GB:scsi:512:512:msdos:ATA ST9500325AS;
1:1049kB:106MB:105MB:fat16::diag;
2:106MB:21.1GB:21.0GB:ntfs::boot;
3:21.1GB:106GB:84.8GB:ntfs::;
4:106GB:500GB:394GB:::;
6:106GB:494GB:388GB:ext4::;
5:494GB:500GB:5878MB:linux-swap(v1)::;
 
 
                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
 
                                                                          
Warning: The driver descriptor says the physical block size is 512 bytes, but
Linux says it is 2048 bytes.
 
 
=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,relatime,size=10240k,nr_inodes=696787,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=558952k,mode=755)
/dev/sr0 on /lib/live/mount/findiso type iso9660 (ro,noatime)
/dev/loop0 on /lib/live/mount/medium type iso9660 (ro,noatime)
/dev/loop1 on /lib/live/mount/rootfs/filesystem.squashfs type squashfs (ro,noatime)
tmpfs on /lib/live/mount/overlay type tmpfs (rw,relatime)
tmpfs on /lib/live/mount/overlay type tmpfs (rw,noatime,mode=755)
aufs on / type aufs (rw,relatime,si=7a48f1d5510f2add,noxino)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /run/shm type tmpfs (rw,nosuid,nodev,noexec,relatime,size=1117900k)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=utf8,shortname=mixed,errors=remount-ro)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda6 on /mnt/boot-sav/sda6 type ext4 (rw,relatime,user_xattr,barrier=1,data=ordered)
 
 
=================== ls:
/sys/block/sda (filtered):   alignment_offset bdi capability dev device discard_alignment events  events_async events_poll_msecs ext_range holders inflight power queue  range removable ro sda1 sda2 sda3 sda4 sda5 sda6 size slaves stat  subsystem trace uevent
/sys/block/sr0 (filtered):   alignment_offset bdi capability dev device discard_alignment events  events_async events_poll_msecs ext_range holders inflight power queue  range removable ro size slaves stat subsystem trace uevent
/dev (filtered):   MAKEDEV autofs block bsg btrfs-control bus cdrom cdrw char console core  cpu cpu_dma_latency disk dvd dvdrw fd full fuse hidraw0 hpet input kmsg  log mapper mcelog md media0 mem net network_latency network_throughput  null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2  sda3 sda4 sda5 sda6 sg0 sg1 shm snapshot snd sndstat sr0 stderr stdin  stdout uinput urandom v4l vga_arbiter video0 xconsole zero
ls /dev/md:
ls /dev/mapper:  control
 
=================== hexdump -n512 -C /dev/sda1
00000000  eb 54 90 44 65 6c 6c 20  38 2e 30 00 02 04 01 00  |.T.Dell 8.0.....|
00000010  02 00 02 00 00 f8 c8 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  fd 1f 03 00 80 01 29 30  30 30 30 44 65 6c 6c 55  |......)0000DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 10 00  |tilityFAT16   ..|
00000040  01 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 33 c0  8e d0 bc 00 07 fc b9 80  |......3.........|
00000060  00 8e d8 be 00 7c b8 00  20 8e c0 33 ff f3 66 a5  |.....|.. ..3..f.|
00000070  ea 75 00 00 20 8e d8 be  cc 01 b8 01 02 b9 01 00  |.u.. ...........|
00000080  b6 00 8a 16 24 00 bb 00  02 cd 13 0f 82 0c 01 80  |....$...........|
00000090  3e c2 03 06 74 0e c6 06  c2 03 06 b8 01 03 cd 13  |>...t...........|
000000a0  0f 82 f7 00 66 0f b7 06  0e 00 66 03 06 1c 00 66  |....f.....f....f|
000000b0  0f b7 0e 16 00 66 d1 e1  66 03 c1 66 a3 46 00 66  |.....f..f..f.F.f|
000000c0  0f b7 0e 11 00 89 0e 52  00 83 c1 0f c1 e9 04 88  |.......R........|
000000d0  0e 40 00 66 03 c1 66 a3  4e 00 b8 00 30 a3 44 00  |.@.f..f.N...0.D.|
000000e0  8e c0 e8 d4 00 33 db b9  0b 00 be e1 01 8b fb f3  |.....3..........|
000000f0  a6 74 0f 83 c3 20 ff 0e  52 00 75 eb be d7 01 e9  |.t... ..R.u.....|
00000100  99 00 26 8b 47 1a a3 54  00 a1 16 00 a3 52 00 66  |..&.G..T.....R.f|
00000110  0f b7 06 0e 00 66 03 06  1c 00 66 a3 46 00 a1 52  |.....f....f.F..R|
00000120  00 3d 40 00 76 02 b0 40  a2 40 00 e8 8b 00 66 0f  |.=@.v..@.@....f.|
00000130  b6 06 40 00 66 01 06 46  00 29 06 52 00 74 09 c1  |..@.f..F.).R.t..|
00000140  e0 05 01 06 44 00 eb d6  c7 06 44 00 70 00 a0 0d  |....D.....D.p...|
00000150  00 a2 40 00 66 0f b7 06  54 00 66 83 e8 02 66 0f  |..@.f...T.f...f.|
00000160  b6 0e 0d 00 66 f7 e1 66  03 06 4e 00 66 a3 46 00  |....f..f..N.f.F.|
00000170  e8 46 00 8b 36 54 00 b8  00 30 d1 e6 73 03 05 00  |.F..6T...0..s...|
00000180  10 8e c0 26 ad 3d f8 ff  73 16 a3 54 00 0f b6 06  |...&.=..s..T....|
00000190  0d 00 c1 e0 09 01 06 42  00 eb b9 e8 0d 00 eb fe  |.......B........|
000001a0  8a 16 24 00 33 ed ea 00  00 70 00 b4 0e ac bb 07  |..$.3....p......|
000001b0  00 cd 10 80 3c 00 75 f3  c3 b4 42 8a 16 24 00 be  |....<.u...B..$..|
000001c0  3e 00 cd 13 72 01 c3 be  cc 01 eb cf 44 69 73 6b  |>...r.......Disk|
000001d0  20 65 72 72 6f 72 00 4e  6f 20 6c 6f 61 64 65 72  | error.No loader|
000001e0  00 44 45 4c 4c 42 49 4f  20 42 49 4e 00 00 00 00  |.DELLBIO BIN....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
 
=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 03 00  |........?....(..|
00000020  00 00 00 00 80 00 80 00  ff ff 70 02 00 00 00 00  |..........p.....|
00000030  00 00 0c 00 00 00 00 00  10 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  f2 79 37 70 8a 37 70 cc  |.........y7p.7p.|
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
 
=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 74 02  |........?....(t.|
00000020  00 00 00 00 80 00 80 00  50 a7 df 09 00 00 00 00  |........P.......|
00000030  00 00 0c 00 00 00 00 00  10 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  d4 86 4e 7c c2 4e 7c ac  |..........N|.N|.|
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
 
Filesystem     Type      Size  Used Avail Use% Mounted on
rootfs         rootfs    2.7G   12M  2.7G   1% /
udev           devtmpfs   10M     0   10M   0% /dev
tmpfs          tmpfs     546M  376K  546M   1% /run
/dev/sr0       iso9660   4.2G  4.2G     0 100% /lib/live/mount/findiso
/dev/loop0     iso9660   406M  406M     0 100% /lib/live/mount/medium
/dev/loop1     squashfs  374M  374M     0 100% /lib/live/mount/rootfs/filesystem.squashfs
tmpfs          tmpfs     2.7G     0  2.7G   0% /lib/live/mount/overlay
tmpfs          tmpfs     2.7G     0  2.7G   0% /lib/live/mount/overlay
aufs           aufs      2.7G   12M  2.7G   1% /
tmpfs          tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs          tmpfs     1.1G     0  1.1G   0% /run/shm
/dev/sda1      vfat      100M  120K  100M   1% /mnt/boot-sav/sda1
/dev/sda2      fuseblk    20G  6.6G   13G  34% /mnt/boot-sav/sda2
/dev/sda3      fuseblk    79G   48G   31G  61% /mnt/boot-sav/sda3
/dev/sda6      ext4      356G   84G  255G  25% /mnt/boot-sav/sda6
 
=================== fdisk -l:
 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x93e12b00
 
Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400   de  Dell Utility
/dev/sda2   *      206848    41166847    20480000    7  HPFS/NTFS/exFAT
/dev/sda3        41166848   206819162    82826157+   7  HPFS/NTFS/exFAT
/dev/sda4       206819326   976771071   384975873    5  Extended
/dev/sda5       965289984   976771071     5740544   82  Linux swap / Solaris
/dev/sda6       206819328   965289983   379235328   83  Linux
 
Partition table entries are not in disk order
 
 
 
=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sda6 into the MBR of sda.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot
 
 
Quantity of real Windows: 1
WinSE in sda3
Copied Win boot files from sda2 to sda3
 
*******lspci -nnk | grep -iA3 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6620G] [1002:9641]
Subsystem: Dell Device [1028:0513]
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series] [1002:1714]
Subsystem: Dell Device [1028:0513]
*******
 
grub-install: info: executing modprobe efivars 2>/dev/null.
grub-install: info: Looking for /sys/firmware/efi ...
grub-install: info: ... not found. Looking for /proc/device-tree ...
grub-install: info: ... not found.
Installing for i386-pc platform.
grub-install: error: install device isn't specified.
,.
 
Reinstall the GRUB of sda6 into the MBR of sda
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0
 
chroot /mnt/boot-sav/sda6 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.18.0-031800rc2-generic
Found initrd image: /boot/initrd.img-3.18.0-031800rc2-generic
Found linux image: /boot/vmlinuz-3.16.0-24-generic
Found initrd image: /boot/initrd.img-3.16.0-24-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.5.0-28-generic
Found initrd image: /boot/initrd.img-3.5.0-28-generic
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-34-generic
Found initrd image: /boot/initrd.img-3.2.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-33-generic
Found initrd image: /boot/initrd.img-3.2.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-27-generic
Found initrd image: /boot/initrd.img-3.2.0-27-generic
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda2
Found Windows 7 (loader) on /dev/sda3
Unhide GRUB boot menu in sda6/boot/grub/grub.cfg
 
Boot successfully repaired.
 
You can now reboot your computer.
 
paste.debian.net ko (), using paste2
[/LIST]
 
```
                               
                       © 2006 - 2014 Paste2.org.
             [[IMG]http://static.paste2.org/templates/paste2/img/follow_us-a.png[/IMG]]("http://twitter.com/paste2org")

---

### Post by ajgreeny on 2014-11-15
You have far too many kernels on the machine to make it easy to follow what has happened; 18 of them going right back to 3.2.0-23, so I assume this is probably an OS that you have updated, rather than clean installed, with 12.04 as the starting point.

However, that would not necessarily cause your problem.

Can you boot to earlier kernels from grub menu?
 If for some reason you don't usually see a grub menu, hold shift at power-on, then choose "Advanced" from the menu and finally choose an older kernel that you know works.  That may at least get you into the OS from where you can try to sort out any other problems you have.

Personally I would have suggested you stick with 14.04, the LTS version, but it is too late for that now, so you will have to try and get 14.10 to boot.

PS:
When attaching long code output such as the boot-repair report, please either just give us the link that it offers, or enclose your report in code tags which retains formatting and makes it much easier to read.  See my signature for how that is done.

---

### Post by 7-webmaster on 2014-11-15
Thank you.

> **ajgreeny said:**
> You have far too many kernels on the machine to make it easy to follow what has happened; 18 of them going right back to 3.2.0-23, so I assume this is probably an OS that you have updated, rather than clean installed, with 12.04 as the starting point.

However, that would not necessarily cause your problem.

Can you boot to earlier kernels from grub menu?
 If for some reason you don't usually see a grub menu, hold shift at power-on, then choose "Advanced" from the menu and finally choose an older kernel that you know works.  That may at least get you into the OS from where you can try to sort out any other problems you have.

Personally I would have suggested you stick with 14.04, the LTS version, but it is too late for that now, so you will have to try and get 14.10 to boot.

PS:
When attaching long code output such as the boot-repair report, please either just give us the link that it offers, or enclose your report in code tags which retains formatting and makes it much easier to read.  See my signature for how that is done.

I went to 14.10 because 14.04 does not work on my system.  About 25% of the time it does not shut down when the lid is closed, and if it does shutdown it does not resume when the lid is opened, and 3 crash reports are sent by Apport.  None of the volunteers are interested in fixing kernel problems on kernel 3.11 that are probably fixed in kernel 3.16, and I don't blame them.  Superficially kernel 3.16 is better in that it has never failed to "resume" when the lid opens and the support for the ATI graphics, but there is a problem with the graphics driver in kernel 3.16 that during resume it NEVER turns the backlight on.  So the system may be running but there is not a lot I can do with it except use Alt-PrtSc to shutdown and reboot.

I removed the 13 oldest kernels, rebuilt the grub config, and explicitly booted kernel 3.16.24 and it came up.

Again thank you.

---

