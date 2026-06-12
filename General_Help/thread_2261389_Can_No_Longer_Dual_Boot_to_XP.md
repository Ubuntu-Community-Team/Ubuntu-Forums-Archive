---
title: "Can No Longer Dual Boot to XP"
date: 2015-01-18
forum: General Help
---

### Post by brando3103 on 2015-01-18
I've been using Unbuntu for over a year now,...and when I initially installed it, I made it a dual boot system. I've booted into XP numerous times in the past,....most recently last week. I' wanted to do so again today,........and it is no longer one of my opetions when I boot up. Any suggestions on how to get that option back again! Thanks!

Pat

---

### Post by yancek on 2015-01-18
Start by opening a terminal and running the following command, watch the output for a listing for windows:

> sudo update-grub

If that doesn't do it, run:

> sudo os-prober

then repeat the update-grub command.

---

### Post by brando3103 on 2015-01-18
Thanks Yancek,....di both, and it didn't work!

---

### Post by yancek on 2015-01-18
What happened when you ran the commands?  To get more information on partitions/boot files, etc., go to the site below and download and run the bootinfoscript and post the output here, a results.txt file.  Instructions are in a link in the Description box at the top of the page.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by monkeybrain20122 on 2015-01-18
It is time to put XP to rest anyway

---

### Post by brando3103 on 2015-01-18
I agree Monkeybrain,.......I hardly ever use XP,......and use Ubuntu almost exclusively. But there are certain times when I need to run a Windows program,.....so it's handy to have that at my disposal! I'll do the above suggestion shortly

pat

---

### Post by brando3103 on 2015-01-18
This is what it said:
"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sdb1 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/pat/Downloads/".

---

### Post by brando3103 on 2015-01-18
This might be waht you wanted:
  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   155,897,557   155,897,495   7 NTFS / exFAT / HPFS
/dev/sda2         155,897,854   312,498,175   156,600,322   5 Extended
/dev/sda5         155,897,856   308,326,399   152,428,544  83 Linux
/dev/sda6         308,328,448   312,498,175     4,169,728  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   625,140,399   625,138,352   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5A7C126D7C1243E3                       ntfs       
/dev/sda5        e96b8bba-0d21-4be8-b799-072f133cdd86   ext4       
/dev/sda6        f2791c27-bd5d-40fa-8ebf-a43c0d75b51a   swap       
/dev/sdb1        D0227AD7227AC250                       ntfs       TOSHIBA EXT

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/pat/5A7C126D7C1243E3 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/pat/TOSHIBA EXT   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
else
  search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_CA
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-e96b8bba-0d21-4be8-b799-072f133cdd86' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
    else
      search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
    fi
    linux    /boot/vmlinuz-3.13.0-44-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-44-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
    menuentry 'Ubuntu, with Linux 3.13.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-44-generic ...'
        linux    /boot/vmlinuz-3.13.0-44-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-44-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-recovery-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-44-generic ...'
        linux    /boot/vmlinuz-3.13.0-44-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro recovery nomodeset rootflags=sync
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-44-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-43-generic ...'
        linux    /boot/vmlinuz-3.13.0-43-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-recovery-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-43-generic ...'
        linux    /boot/vmlinuz-3.13.0-43-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro recovery nomodeset rootflags=sync
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-40-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-40-generic-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-40-generic ...'
        linux    /boot/vmlinuz-3.13.0-40-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-40-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-40-generic-recovery-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-40-generic ...'
        linux    /boot/vmlinuz-3.13.0-40-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro recovery nomodeset rootflags=sync
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-40-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-recovery-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro recovery nomodeset rootflags=sync
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-37-generic-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-37-generic ...'
        linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-37-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-37-generic-recovery-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-37-generic ...'
        linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro recovery nomodeset rootflags=sync
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-37-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-36-generic-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-36-generic ...'
        linux    /boot/vmlinuz-3.13.0-36-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-36-generic-recovery-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-36-generic ...'
        linux    /boot/vmlinuz-3.13.0-36-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro recovery nomodeset rootflags=sync
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-29-generic-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-29-generic ...'
        linux    /boot/vmlinuz-3.13.0-29-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-29-generic-recovery-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-29-generic ...'
        linux    /boot/vmlinuz-3.13.0-29-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro recovery nomodeset rootflags=sync
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-27-generic-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-27-generic ...'
        linux    /boot/vmlinuz-3.13.0-27-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-27-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-27-generic-recovery-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-27-generic ...'
        linux    /boot/vmlinuz-3.13.0-27-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro recovery nomodeset rootflags=sync
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-27-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
    else
      search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
    else
      search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f2791c27-bd5d-40fa-8ebf-a43c0d75b51a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-ooFACEQd/Tmp_Log: No such file or directory

---

### Post by yancek on 2015-01-18
Your output shows a 160GB drive with the first partition a windows partition indicating xp.  Unfortunately, no boot files are shown on that partition.  You do have some wubi files there so apparently you had done a wubi install in the past.  

It also shows a 320GB drive with a windows partition showing vista or windows 7.  I don't see any boot files there.  Do you have an install on the 320GB drive?  Does it boot?
I expect the reason you can't boot xp is because you don't have the required boot files and that is why no entry is shown in Grub, they can't be detected if they are not there.  Generally you need a windows installation medium to repair the windows bootloader although there may be other solutions.  I haven't used windows in many years so maybe someone else who does will have a suggestion.

---

### Post by brando3103 on 2015-01-18
This might be waht you wanted:
  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   155,897,557   155,897,495   7 NTFS / exFAT / HPFS
/dev/sda2         155,897,854   312,498,175   156,600,322   5 Extended
/dev/sda5         155,897,856   308,326,399   152,428,544  83 Linux
/dev/sda6         308,328,448   312,498,175     4,169,728  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   625,140,399   625,138,352   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5A7C126D7C1243E3                       ntfs       
/dev/sda5        e96b8bba-0d21-4be8-b799-072f133cdd86   ext4       
/dev/sda6        f2791c27-bd5d-40fa-8ebf-a43c0d75b51a   swap       
/dev/sdb1        D0227AD7227AC250                       ntfs       TOSHIBA EXT

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/pat/5A7C126D7C1243E3 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/pat/TOSHIBA EXT   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
else
  search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_CA
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-e96b8bba-0d21-4be8-b799-072f133cdd86' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
    else
      search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
    fi
    linux    /boot/vmlinuz-3.13.0-44-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-44-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
    menuentry 'Ubuntu, with Linux 3.13.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-44-generic ...'
        linux    /boot/vmlinuz-3.13.0-44-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-44-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-recovery-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-44-generic ...'
        linux    /boot/vmlinuz-3.13.0-44-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro recovery nomodeset rootflags=sync
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-44-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-43-generic ...'
        linux    /boot/vmlinuz-3.13.0-43-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-recovery-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-43-generic ...'
        linux    /boot/vmlinuz-3.13.0-43-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro recovery nomodeset rootflags=sync
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-40-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-40-generic-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-40-generic ...'
        linux    /boot/vmlinuz-3.13.0-40-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-40-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-40-generic-recovery-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-40-generic ...'
        linux    /boot/vmlinuz-3.13.0-40-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro recovery nomodeset rootflags=sync
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-40-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-recovery-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro recovery nomodeset rootflags=sync
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-37-generic-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-37-generic ...'
        linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-37-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-37-generic-recovery-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-37-generic ...'
        linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro recovery nomodeset rootflags=sync
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-37-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-36-generic-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-36-generic ...'
        linux    /boot/vmlinuz-3.13.0-36-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-36-generic-recovery-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-36-generic ...'
        linux    /boot/vmlinuz-3.13.0-36-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro recovery nomodeset rootflags=sync
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-36-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-29-generic-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-29-generic ...'
        linux    /boot/vmlinuz-3.13.0-29-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-29-generic-recovery-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-29-generic ...'
        linux    /boot/vmlinuz-3.13.0-29-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro recovery nomodeset rootflags=sync
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-27-generic-advanced-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-27-generic ...'
        linux    /boot/vmlinuz-3.13.0-27-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro rootflags=sync quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-27-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-27-generic-recovery-e96b8bba-0d21-4be8-b799-072f133cdd86' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
        else
          search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
        fi
        echo    'Loading Linux 3.13.0-27-generic ...'
        linux    /boot/vmlinuz-3.13.0-27-generic root=UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 ro recovery nomodeset rootflags=sync
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-27-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
    else
      search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5  e96b8bba-0d21-4be8-b799-072f133cdd86
    else
      search --no-floppy --fs-uuid --set=root e96b8bba-0d21-4be8-b799-072f133cdd86
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=e96b8bba-0d21-4be8-b799-072f133cdd86 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f2791c27-bd5d-40fa-8ebf-a43c0d75b51a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-ooFACEQd/Tmp_Log: No such file or directory

---

### Post by brando3103 on 2015-01-18
Thanks! The weird thing is,.....that up until yesterday I could boot into XP. But now I can't. So I'm not sure what may have happened in the interim. I have done no "fooling around" with installs or anything. The dual boot option just vanished at start-up!

---

