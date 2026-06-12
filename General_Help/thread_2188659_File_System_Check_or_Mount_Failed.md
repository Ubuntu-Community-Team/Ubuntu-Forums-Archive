---
title: "File System Check or Mount Failed"
date: 2013-11-18
forum: General Help
---

### Post by fabrice.lambert on 2013-11-18
Hi! I'm running Ubuntu 3.8.0-31 on my Laptop's SSD (/dev/sda) with Windows on another hard-drive (/dev/sdb). When I boot up there is an error message that says "Filesystem check or mount failed. A maintainance will now be started CONTROL-D will terminate this shell and continue booting after re-trying filesystems. Any further errors will be ignored". Then I am in a console as root.

I have run the sequence of commands mentioned in other posts:
mount -o remount,rw /
dpkg --configure -a
mount -o remount,ro /
sync reboot
All it does is freeze after the reboot (any kind of shutdown command freezes the computer).

I have run fsck and fsck.ext4 from that emergency command line and from a live-USBstick. There don't appear to be any problems with the partition / is mounted on (/dev/sda3).

cat /etc/mtab:
/dev/sda3 / ext4 rw,errors=remount -ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/cgroup tmpfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0

The last 4 lines of tail /var/log/syslog (the previous lines don't record any problems):
AptDaemon: INFO: Quitting due to inactivity
AptDaemon: INFO: Quitting was requested
colord: device removed: xrandr-BOE
Profile removed: icc-f3d775d80ce1018470

Here's some bootinfo (run from a live-USBstick /dev/sdc):
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 1865504 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2         218,441,726   234,440,703    15,998,978   5 Extended
/dev/sda5         218,441,728   234,440,703    15,998,976  82 Linux swap / Solaris
/dev/sda3             206,848   218,439,679   218,232,832  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048 1,250,260,991 1,250,258,944   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 999 MB, 999817216 bytes
122 heads, 63 sectors/track, 254 cylinders, total 1952768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             32     1,952,767     1,952,736   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        EA18607118603EA7                       ntfs       System Reserved
/dev/sda3        54d067e1-67a5-409d-966a-ece622c7274b   ext4       
/dev/sda5        36deff95-b3bb-4dff-b42c-1e6ac3118a9e   swap       
/dev/sdb1        D8C0636AC0634DB6                       ntfs       
/dev/sdc1        3C51-A71C                              vfat       UBUNTU12

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
insmod part_msdos
insmod ext2
set root='hd0,msdos3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
else
  search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-54d067e1-67a5-409d-966a-ece622c7274b' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
    else
      search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
    fi
    linux    /boot/vmlinuz-3.8.0-31-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-31-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-54d067e1-67a5-409d-966a-ece622c7274b' {
    menuentry 'Ubuntu, with Linux 3.8.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-31-generic-advanced-54d067e1-67a5-409d-966a-ece622c7274b' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
        else
          search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
        fi
        echo    'Loading Linux 3.8.0-31-generic ...'
        linux    /boot/vmlinuz-3.8.0-31-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-31-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-31-generic-recovery-54d067e1-67a5-409d-966a-ece622c7274b' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
        else
          search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
        fi
        echo    'Loading Linux 3.8.0-31-generic ...'
        linux    /boot/vmlinuz-3.8.0-31-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-31-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-30-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-30-generic-advanced-54d067e1-67a5-409d-966a-ece622c7274b' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
        else
          search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
        fi
        echo    'Loading Linux 3.8.0-30-generic ...'
        linux    /boot/vmlinuz-3.8.0-30-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-30-generic-recovery-54d067e1-67a5-409d-966a-ece622c7274b' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
        else
          search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
        fi
        echo    'Loading Linux 3.8.0-30-generic ...'
        linux    /boot/vmlinuz-3.8.0-30-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-30-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-29-generic-advanced-54d067e1-67a5-409d-966a-ece622c7274b' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
        else
          search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
        fi
        echo    'Loading Linux 3.8.0-29-generic ...'
        linux    /boot/vmlinuz-3.8.0-29-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-29-generic-recovery-54d067e1-67a5-409d-966a-ece622c7274b' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
        else
          search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
        fi
        echo    'Loading Linux 3.8.0-29-generic ...'
        linux    /boot/vmlinuz-3.8.0-29-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-29-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-27-generic-advanced-54d067e1-67a5-409d-966a-ece622c7274b' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
        else
          search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
        fi
        echo    'Loading Linux 3.8.0-27-generic ...'
        linux    /boot/vmlinuz-3.8.0-27-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-27-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-27-generic-recovery-54d067e1-67a5-409d-966a-ece622c7274b' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
        else
          search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
        fi
        echo    'Loading Linux 3.8.0-27-generic ...'
        linux    /boot/vmlinuz-3.8.0-27-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-27-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-26-generic-advanced-54d067e1-67a5-409d-966a-ece622c7274b' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
        else
          search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
        fi
        echo    'Loading Linux 3.8.0-26-generic ...'
        linux    /boot/vmlinuz-3.8.0-26-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-26-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-26-generic-recovery-54d067e1-67a5-409d-966a-ece622c7274b' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
        else
          search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
        fi
        echo    'Loading Linux 3.8.0-26-generic ...'
        linux    /boot/vmlinuz-3.8.0-26-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-26-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-25-generic-advanced-54d067e1-67a5-409d-966a-ece622c7274b' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
        else
          search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
        fi
        echo    'Loading Linux 3.8.0-25-generic ...'
        linux    /boot/vmlinuz-3.8.0-25-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-25-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-25-generic-recovery-54d067e1-67a5-409d-966a-ece622c7274b' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
        else
          search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
        fi
        echo    'Loading Linux 3.8.0-25-generic ...'
        linux    /boot/vmlinuz-3.8.0-25-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.8.0-25-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-34-generic-advanced-54d067e1-67a5-409d-966a-ece622c7274b' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
        else
          search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
        fi
        echo    'Loading Linux 3.5.0-34-generic ...'
        linux    /boot/vmlinuz-3.5.0-34-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-34-generic-recovery-54d067e1-67a5-409d-966a-ece622c7274b' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
        else
          search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
        fi
        echo    'Loading Linux 3.5.0-34-generic ...'
        linux    /boot/vmlinuz-3.5.0-34-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-48-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-48-generic-advanced-54d067e1-67a5-409d-966a-ece622c7274b' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
        else
          search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
        fi
        echo    'Loading Linux 3.2.0-48-generic ...'
        linux    /boot/vmlinuz-3.2.0-48-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-48-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-48-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.2.0-48-generic-recovery-54d067e1-67a5-409d-966a-ece622c7274b' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  54d067e1-67a5-409d-966a-ece622c7274b
        else
          search --no-floppy --fs-uuid --set=root 54d067e1-67a5-409d-966a-ece622c7274b
        fi
        echo    'Loading Linux 3.2.0-48-generic ...'
        linux    /boot/vmlinuz-3.2.0-48-generic root=UUID=54d067e1-67a5-409d-966a-ece622c7274b ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.2.0-48-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-D8C0636AC0634DB6' {
    insmod part_msdos
    insmod ntfs
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  D8C0636AC0634DB6
    else
      search --no-floppy --fs-uuid --set=root D8C0636AC0634DB6
    fi
    chainloader +1
}
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
/dev/sda3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
/dev/sda5 none            swap    sw              0       0
--------------------------------------------------------------------------------

====================== sda3/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sda3: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sda3: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --

label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdd 

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-7PqcTsou/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-7PqcTsou/Tmp_Log: No such file or directory
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-7PqcTsou/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-7PqcTsou/Tmp_Log: No such file or directory
  No volume groups found


```

Any ideas?
-Fabrice

---

### Post by grier-devon on 2013-11-18
Hello there, you are actually running Ubuntu 13.04 not 3.8 did this happen recently or all of a sudden or after a upgrade? From what I could see people seem to be having this problem after the upgrade cause the system did not fully finish install, Try this....
1. Boot on Live USB
2. sudo mount /dev/sda1 /mnt
3. sudo chroot /mnt
4. sudo apt-get update
5. sudo apt-get dist-upgrade

This should yield an error once complete then you will execute...
sudo apt-get install -f

PS - Make sure you change your mount point in what I listed to the actual mount points where you tried to install Ubuntu.

---

### Post by fabrice.lambert on 2013-11-18
Hi, thanks for looking at this. My Ubunut system is actually on sda3. Steps 4. and 5. fail with "Something wicked happened resolving 'archive.ubuntu.com: http' (-11 - System error) Adding the option --fix-missing returns the same error. I'm connected to wireless as usual, but I can't ping anywhere when I've changed with chroot. How do I connect the mounted partition to internet?

---

### Post by grier-devon on 2013-11-18
> **fabrice.lambert said:**
> Hi, thanks for looking at this. My Ubunut system is actually on sda3. Steps 4. and 5. fail with "Something wicked happened resolving 'archive.ubuntu.com: http' (-11 - System error) Adding the option --fix-missing returns the same error. I'm connected to wireless as usual, but I can't ping anywhere when I've changed with chroot. How do I connect the mounted partition to internet?

Are you booting from the Live USB like I told you? You should be in a standard desktop when bootin from the live USB so you would connect to the interenet as usual.

---

### Post by fabrice.lambert on 2013-11-19
Yes, I'm booting from the live USB. I'm connected to internet, but as soon as I chroot I don't have any connection anymore (see attached screenshot).

---

### Post by nico17 on 2014-08-26
It's sad that no one has bothered to answer you for 9 months, mainly because I'm having this problem now (on 2 machines so far) while upgrading from LTS from 12 to 14

Here's what worked for me. Before the chroot I did:
[FONT=fixedsys]# mount --bind /proc /mnt/proc[/FONT]
I also didn't have anything at /mnt/etc/resolv.conf, so I did:
[FONT=fixedsys]# cp /etc/resolv.com /mnt/etc[/FONT]

After that, apt-get started working (my boxes are still far from OK, but at least this answers your question how to reach the net while chrooted).

---

