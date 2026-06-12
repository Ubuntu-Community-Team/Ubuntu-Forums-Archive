---
title: "How to re-size my Ubuntu Partition"
date: 2016-10-22
forum: General Help
---

### Post by mulluysavage on 2016-10-22
Root ran out of file space. I have room on other partitions, thinking that I can re-size other partitions and expand the Ubuntu partition. 

Screenshot of Gparted attached.

considering: 

shrinking swap /sda6
shrinking home /sda8
shrinking or eliminating "distro play" /sda9 - this was created to test out new distros while keeping working distro on /sda7

All require moving Ubuntu partition and home partition. 

How do I do this safely? I think I need to move and resize through Gparted, then re-config my bootloaders to point to the new boot partition. However. It's not totally clear to me how my bootloaders are working.

Will post boot report from Boot Repair Disk shortly.

[https://drive.google.com/open?id=0BwG0YBrNsinPQVlQRVAzTlhFa00](https://drive.google.com/open?id=0BwG0YBrNsinPQVlQRVAzTlhFa00)

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

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
    Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/MokManager.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.5 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda11: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20140113
    Boot sector info:  Syslinux looks at sector 1824032 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /casper/vmlinuz.efi /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   488,397,167   488,397,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       821,247       819,200 Windows Recovery Environment (Windows)
/dev/sda2         821,248     1,435,647       614,400 EFI System partition
/dev/sda3       1,435,648     1,697,791       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       1,697,792   104,970,239   103,272,448 Data partition (Windows/Linux)
/dev/sda5     104,970,240   105,893,887       923,648 Windows Recovery Environment (Windows)
/dev/sda6     105,893,888   137,144,319    31,250,432 Swap partition (Linux)
/dev/sda7     137,144,320   167,143,423    29,999,104 Data partition (Windows/Linux)
/dev/sda8     167,143,424   198,600,703    31,457,280 Data partition (Windows/Linux)
/dev/sda9     198,600,704   230,057,983    31,457,280 Data partition (Windows/Linux)
/dev/sda10    230,057,984   455,262,207   225,204,224 Data partition (Windows/Linux)
/dev/sda11    455,262,208   488,396,799    33,134,592 Windows Recovery Environment (Windows)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    15,633,407    15,633,376   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        DA04973E04971D17                       ntfs       RECOVERY
/dev/sda10       19A8317B4736F421                       ntfs       storage
/dev/sda11       70D298FDD298C8AC                       ntfs       Push Button Reset
/dev/sda2        B297-4A93                              vfat       ESP
/dev/sda4        7A0E46F30E46A849                       ntfs       ACER
/dev/sda5        A64E9E6A4E9E3353                       ntfs       
/dev/sda6        e9f58f11-4966-41e1-9d20-6596ba76c7f1   swap       
/dev/sda7        6141cc59-14ca-4adf-9b31-388853dc25c9   ext4       ubuntu 12.04
/dev/sda8        4978a582-d003-4365-b312-9a6f0c032bc6   ext4       ubuntu home
/dev/sda9        1aa87994-270f-488b-901d-82388fc9700d   ext4       distro play
/dev/sdb1        C17B-6AD7                              vfat       
/dev/zram0       e5d13486-21e4-42c2-b65b-694de5de19b9   swap       
/dev/zram1       8dce9335-a379-4a31-b48b-b4a754026264   swap       
/dev/zram2       0fd887c3-66fa-487c-9e22-851358edbead   swap       
/dev/zram3       089b4169-2b7f-498c-86e3-049d08aaa8e6   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Oct 22 15:21 ata-Samsung_SSD_840_Series_S14GNEACC12929E -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 22 15:22 ata-Samsung_SSD_840_Series_S14GNEACC12929E-part1 -> ../../sda1
lrwxrwxrwx 1 root root 11 Oct 22 15:22 ata-Samsung_SSD_840_Series_S14GNEACC12929E-part10 -> ../../sda10
lrwxrwxrwx 1 root root 11 Oct 22 15:22 ata-Samsung_SSD_840_Series_S14GNEACC12929E-part11 -> ../../sda11
lrwxrwxrwx 1 root root 10 Oct 22 15:21 ata-Samsung_SSD_840_Series_S14GNEACC12929E-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 22 15:21 ata-Samsung_SSD_840_Series_S14GNEACC12929E-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Oct 22 15:22 ata-Samsung_SSD_840_Series_S14GNEACC12929E-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Oct 22 15:22 ata-Samsung_SSD_840_Series_S14GNEACC12929E-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Oct 22 15:21 ata-Samsung_SSD_840_Series_S14GNEACC12929E-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Oct 22 15:21 ata-Samsung_SSD_840_Series_S14GNEACC12929E-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Oct 22 15:21 ata-Samsung_SSD_840_Series_S14GNEACC12929E-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Oct 22 15:21 ata-Samsung_SSD_840_Series_S14GNEACC12929E-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 Oct 22 15:21 usb-SanDisk_Cruzer_Blade_20044324331DB73076F2-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct 22 15:21 usb-SanDisk_Cruzer_Blade_20044324331DB73076F2-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Oct 22 15:21 wwn-0x50025385500d4b3e -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 22 15:22 wwn-0x50025385500d4b3e-part1 -> ../../sda1
lrwxrwxrwx 1 root root 11 Oct 22 15:22 wwn-0x50025385500d4b3e-part10 -> ../../sda10
lrwxrwxrwx 1 root root 11 Oct 22 15:22 wwn-0x50025385500d4b3e-part11 -> ../../sda11
lrwxrwxrwx 1 root root 10 Oct 22 15:21 wwn-0x50025385500d4b3e-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 22 15:21 wwn-0x50025385500d4b3e-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Oct 22 15:22 wwn-0x50025385500d4b3e-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Oct 22 15:22 wwn-0x50025385500d4b3e-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Oct 22 15:21 wwn-0x50025385500d4b3e-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Oct 22 15:21 wwn-0x50025385500d4b3e-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Oct 22 15:21 wwn-0x50025385500d4b3e-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Oct 22 15:21 wwn-0x50025385500d4b3e-part9 -> ../../sda9

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
set root='hd0,gpt7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
else
  search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
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
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-6141cc59-14ca-4adf-9b31-388853dc25c9' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
    else
      search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
    fi
    linux    /boot/vmlinuz-3.13.0-100-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-100-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
    menuentry 'Ubuntu, with Linux 3.13.0-100-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-100-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-100-generic ...'
        linux    /boot/vmlinuz-3.13.0-100-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-100-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-100-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-100-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-100-generic ...'
        linux    /boot/vmlinuz-3.13.0-100-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-100-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-98-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-98-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-98-generic ...'
        linux    /boot/vmlinuz-3.13.0-98-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-98-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-98-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-98-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-98-generic ...'
        linux    /boot/vmlinuz-3.13.0-98-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-98-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-96-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-96-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-96-generic ...'
        linux    /boot/vmlinuz-3.13.0-96-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-96-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-96-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-96-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-96-generic ...'
        linux    /boot/vmlinuz-3.13.0-96-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-96-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-92-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-92-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-92-generic ...'
        linux    /boot/vmlinuz-3.13.0-92-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-92-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-92-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-92-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-92-generic ...'
        linux    /boot/vmlinuz-3.13.0-92-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-92-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-87-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-87-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-87-generic ...'
        linux    /boot/vmlinuz-3.13.0-87-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-87-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-87-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-87-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-87-generic ...'
        linux    /boot/vmlinuz-3.13.0-87-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-87-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-86-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-86-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-86-generic ...'
        linux    /boot/vmlinuz-3.13.0-86-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-86-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-86-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-86-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-86-generic ...'
        linux    /boot/vmlinuz-3.13.0-86-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-86-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-85-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-85-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-85-generic ...'
        linux    /boot/vmlinuz-3.13.0-85-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-85-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-85-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-85-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-85-generic ...'
        linux    /boot/vmlinuz-3.13.0-85-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-85-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-77-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-77-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-77-generic ...'
        linux    /boot/vmlinuz-3.13.0-77-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-77-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-77-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-77-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-77-generic ...'
        linux    /boot/vmlinuz-3.13.0-77-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-77-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-53-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-53-generic ...'
        linux    /boot/vmlinuz-3.13.0-53-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-53-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-53-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-53-generic ...'
        linux    /boot/vmlinuz-3.13.0-53-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-53-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-52-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-52-generic ...'
        linux    /boot/vmlinuz-3.13.0-52-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-52-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-52-generic ...'
        linux    /boot/vmlinuz-3.13.0-52-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-52-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-48-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-48-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-48-generic ...'
        linux    /boot/vmlinuz-3.13.0-48-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-48-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-48-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-48-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-48-generic ...'
        linux    /boot/vmlinuz-3.13.0-48-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-48-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-45-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-45-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-45-generic ...'
        linux    /boot/vmlinuz-3.13.0-45-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-45-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-45-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-45-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-45-generic ...'
        linux    /boot/vmlinuz-3.13.0-45-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-45-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-44-generic ...'
        linux    /boot/vmlinuz-3.13.0-44-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-44-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-44-generic ...'
        linux    /boot/vmlinuz-3.13.0-44-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-44-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-43-generic ...'
        linux    /boot/vmlinuz-3.13.0-43-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-43-generic ...'
        linux    /boot/vmlinuz-3.13.0-43-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-43-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-40-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-40-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-40-generic ...'
        linux    /boot/vmlinuz-3.13.0-40-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-40-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-40-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-40-generic ...'
        linux    /boot/vmlinuz-3.13.0-40-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-40-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-39-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-39-generic ...'
        linux    /boot/vmlinuz-3.13.0-39-generic.efi.signed root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-39-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-37-generic-advanced-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-37-generic ...'
        linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-37-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-37-generic-recovery-6141cc59-14ca-4adf-9b31-388853dc25c9' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt7 --hint-efi=hd0,gpt7 --hint-baremetal=ahci0,gpt7  6141cc59-14ca-4adf-9b31-388853dc25c9
        else
          search --no-floppy --fs-uuid --set=root 6141cc59-14ca-4adf-9b31-388853dc25c9
        fi
        echo    'Loading Linux 3.13.0-37-generic ...'
        linux    /boot/vmlinuz-3.13.0-37-generic root=UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-37-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-B297-4A93' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  B297-4A93
    else
      search --no-floppy --fs-uuid --set=root B297-4A93
    fi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
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
UUID=6141cc59-14ca-4adf-9b31-388853dc25c9 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=B297-4A93  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda8 during installation
UUID=4978a582-d003-4365-b312-9a6f0c032bc6 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=e9f58f11-4966-41e1-9d20-6596ba76c7f1 none            swap    sw              0       0
#storage mount
UUID=19A8317B4736F421 /media/storage ntfs-3g user,rw 0 0
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

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

menuentry "Boot-Repair-Disk session" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
ui gfxboot bootlogo
--------------------------------------------------------------------------------

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/2260/mounts) leaked on lvs invocation. Parent PID 14800: bash
File descriptor 63 (pipe:[30340]) leaked on lvs invocation. Parent PID 14800: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-10-22__15h21 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/2260/mounts) leaked on lvs invocation. Parent PID 4881: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda2@/efi/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
/dev/sda7:Ubuntu 14.04.5 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="RECOVERY" UUID="DA04973E04971D17" TYPE="ntfs"
/dev/sda2: LABEL="ESP" UUID="B297-4A93" TYPE="vfat"
/dev/sda4: LABEL="ACER" UUID="7A0E46F30E46A849" TYPE="ntfs"
/dev/sda5: UUID="A64E9E6A4E9E3353" TYPE="ntfs"
/dev/sda6: UUID="e9f58f11-4966-41e1-9d20-6596ba76c7f1" TYPE="swap"
/dev/sda7: LABEL="ubuntu 12.04" UUID="6141cc59-14ca-4adf-9b31-388853dc25c9" TYPE="ext4"
/dev/sda8: LABEL="ubuntu home" UUID="4978a582-d003-4365-b312-9a6f0c032bc6" TYPE="ext4"
/dev/sda9: LABEL="distro play" UUID="1aa87994-270f-488b-901d-82388fc9700d" TYPE="ext4"
/dev/sda10: LABEL="storage" UUID="19A8317B4736F421" TYPE="ntfs"
/dev/sda11: LABEL="Push Button Reset" UUID="70D298FDD298C8AC" TYPE="ntfs"
/dev/sdb1: UUID="C17B-6AD7" TYPE="vfat"
/dev/zram0: UUID="e5d13486-21e4-42c2-b65b-694de5de19b9" TYPE="swap"
/dev/zram1: UUID="8dce9335-a379-4a31-b48b-b4a754026264" TYPE="swap"
/dev/zram2: UUID="0fd887c3-66fa-487c-9e22-851358edbead" TYPE="swap"
/dev/zram3: UUID="089b4169-2b7f-498c-86e3-049d08aaa8e6" TYPE="swap"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda4.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda2/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda2/EFI/Boot/bootx64.efi

=================== sda7/etc/grub.d/ :
drwxr-xr-x  2 root root      4096 Oct  9 19:47 grub.d
total 76
-rwxr-xr-x 1 root root  9791 Dec 17  2015 00_header
-rwxr-xr-x 1 root root  6058 May  8  2014 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15  2014 10_linux
-rwxr-xr-x 1 root root 10412 May 15  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 May 15  2014 30_os-prober
-rwxr-xr-x 1 root root  1418 Aug  2 07:27 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Jan 22  2013 40_custom
-rwxr-xr-x 1 root root   216 May 15  2014 41_custom
-rw-r--r-- 1 root root   483 Jan 22  2013 README




=================== sda7/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
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



/boot/efi detected in the fstab of sda7: UUID=B297-4A93   (sda2)

efibootmgr -v
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0003,0002,0001,0006,0000,0005
Boot0000* shimx    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(2,c8800,96000,36b184a2-bbee-42aa-a786-65173427290b)File(EFIubuntushimx64.efi)A01 ..
Boot0001* HDD:     HD(2,c8800,96000,36b184a2-bbee-42aa-a786-65173427290b)File(EFIubuntugrubx64.efi)RC
Boot0002* ubuntu    HD(2,c8800,96000,36b184a2-bbee-42aa-a786-65173427290b)File(EFIubuntushimx64.efi)
Boot0003* USB HDD: SanDisk Cruzer Blade    ACPI(a0341d0,0)PCI(1d,0)USB(0,0)USB(1,0)HD(1,20,ee8be0,0005d77a)RC
Boot0004* mokmanager    ACPI(a0341d0,0)PCI(1f,2)03120a00000000000000HD(2,c8800,96000,36b184a2-bbee-42aa-a786-65173427290b)File(EFIubuntuMokManager.efi)A01 ).
Boot0005* usbgrubx64    ACPI(a0341d0,0)PCI(1d,0)USB(0,0)USB(2,0)HD(1,20,1efbe0,c3072e18)File(EFIBOOTgrubx64.efi)A01 9.
Boot0006* Windows Boot Manager    HD(2,c8800,96000,36b184a2-bbee-42aa-a786-65173427290b)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}................. ...
=================== UEFI/Legacy mode:
Unusual EFI: Please report this message to [email]boot.repair@gmail.com[/email]
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
sda4    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda4.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda5.
sda7    : sda,    not-sepboot,    grubenv-ok    grub2,    signed grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda7.
sda8    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda8.
sda9    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda9.
sda10    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda10.
sda11    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda11.

sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
1      1049kB  420MB   419MB   ntfs            Basic data partition          hidden, diag
2      420MB   735MB   315MB   fat32           EFI system partition          boot
3      735MB   869MB   134MB                   Microsoft reserved partition  msftres
4      869MB   53.7GB  52.9GB  ntfs            Basic data partition          msftdata
5      53.7GB  54.2GB  473MB   ntfs                                          hidden, diag
6      54.2GB  70.2GB  16.0GB  linux-swap(v1)
7      70.2GB  85.6GB  15.4GB  ext4                                          msftdata
8      85.6GB  102GB   16.1GB  ext4                                          msftdata
9      102GB   118GB   16.1GB  ext4                                          msftdata
10      118GB   233GB   115GB   ntfs                                          msftdata
11      233GB   250GB   17.0GB  ntfs            Basic data partition          hidden, diag


Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sdb: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  8004MB  8004MB  primary  fat32        boot


                                                                            Error: /dev/zram0: unrecognised disk label

                                                                            Error: /dev/zram1: unrecognised disk label

                                                                            Error: /dev/zram2: unrecognised disk label

                                                                            Error: /dev/zram3: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:250GB:scsi:512:512:gpt:ATA Samsung SSD 840;
1:1049kB:420MB:419MB:ntfs:Basic data partition:hidden, diag;
2:420MB:735MB:315MB:fat32:EFI system partition:boot;
3:735MB:869MB:134MB::Microsoft reserved partition:msftres;
4:869MB:53.7GB:52.9GB:ntfs:Basic data partition:msftdata;
5:53.7GB:54.2GB:473MB:ntfs::hidden, diag;
6:54.2GB:70.2GB:16.0GB:linux-swap(v1)::;
7:70.2GB:85.6GB:15.4GB:ext4::msftdata;
8:85.6GB:102GB:16.1GB:ext4::msftdata;
9:102GB:118GB:16.1GB:ext4::msftdata;
10:118GB:233GB:115GB:ntfs::msftdata;
11:233GB:250GB:17.0GB:ntfs:Basic data partition:hidden, diag;

BYT;
/dev/sdb:8004MB:scsi:512:512:msdos:SanDisk Cruzer Blade;
1:16.4kB:8004MB:8004MB:fat32::boot;

                                                                            Error: /dev/zram0: unrecognised disk label

                                                                            Error: /dev/zram1: unrecognised disk label

                                                                            Error: /dev/zram2: unrecognised disk label

                                                                            Error: /dev/zram3: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type vfat (rw)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw)
/dev/sda8 on /mnt/boot-sav/sda8 type ext4 (rw)
/dev/sda9 on /mnt/boot-sav/sda9 type ext4 (rw)
/dev/sda10 on /mnt/boot-sav/sda10 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda11 on /mnt/boot-sav/sda11 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda10 sda11 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda10 sda11 sda2 sda3 sda4 sda5 sda6 sda7 sda8 sda9 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 7f 0c 00 00 00 00 00  |................|
00000030  55 85 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U...............|
00000040  f6 00 00 00 01 00 00 00  17 1d 97 04 3e 97 04 da  |............>...|
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

=================== hexdump -n512 -C /dev/sda2
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 5e 1b  |.X.MSDOS5.0...^.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 88 0c 00  |........?.......|
00000020  00 60 09 00 51 02 00 00  00 00 00 00 02 00 00 00  |.`..Q...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 93 4a 97 b2 4e  4f 20 4e 41 4d 45 20 20  |..).J..NO NAME  |
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
00000020  00 00 00 00 80 00 80 00  ff cf 27 06 00 00 00 00  |..........'.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  49 a8 46 0e f3 46 0e 7a  |........I.F..F.z|
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
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 b8 41 06  |........?.....A.|
00000020  00 00 00 00 80 00 80 00  ff 17 0e 00 00 00 00 00  |................|
00000030  55 96 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U...............|
00000040  f6 00 00 00 01 00 00 00  53 33 9e 4e 6a 9e 4e a6  |........S3.Nj.N.|
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

=================== hexdump -n512 -C /dev/sda10
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 b6 0d  |........?....h..|
00000020  00 00 00 00 80 00 80 00  ff 57 6c 0d 00 00 00 00  |.........Wl.....|
00000030  04 00 00 00 00 00 00 00  7f c5 d6 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  21 f4 36 47 7b 31 a8 19  |........!.6G{1..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r

---

### Post by oldfred on 2016-10-22
You will have to swap off, as little key says swap still mounted.

I would make swap as 2 or 3GB, if you have 4GB or more of RAM and do not hibernate, you may not even need any swap, but some is still suggested.

I do not like moving start of partitions. Any interruption totally corrupts partition as it then is half copied/moved. So really good backups are required.

I typically make / (root) 25GB and have a large data partition, but not /home. If not allocating larger space for /home often then better to keep it inside / so unused space is shared or whatever you do most in either / or /home can use available space.

You do not have a lot of room.
NTFS really likes 30% free. Otherwise it starts to slow as it fragments. And at 10% free defrag can take forever as there is no working room. Linux also need space and even hides 5% to try to prevent crash from full partition.

---

