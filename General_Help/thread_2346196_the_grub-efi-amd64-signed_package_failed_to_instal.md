---
title: "the grub-efi-amd64-signed package failed to install into target"
date: 2016-12-12
forum: General Help
---

### Post by fullon on 2016-12-12
Dear Ubuntu drinkers,

I'm trying to install Ubunto 16 in a notebook with several hard drivers, but it fails to install grub2 and halt with the following message:

the 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot. I have windows installed in some partition of sda.

I tested several flash drivers with rufus. I'm trying to install Ubuntu in sdc2 and Grub2 in sda. Any ideas? Any help will be appreciated.

This is my Boot-Info:

---

### Post by fullon on 2016-12-12
```
Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid 7d58b737-3802-4705-ab41-6fe989ee63ba root hd2,msdos2 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => No boot loader is installed in the MBR of /dev/sdb.
 => libparted MBR boot code is installed in the MBR of /dev/sdc.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdc3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdc6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32784 of /dev/sdd1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     1,026,047     1,024,000   7 NTFS / exFAT / HPFS
/dev/sda2           1,026,048   409,602,047   408,576,000   7 NTFS / exFAT / HPFS
/dev/sda3         409,602,048   819,202,047   409,600,000   7 NTFS / exFAT / HPFS
/dev/sda4         819,202,048 1,953,521,663 1,134,319,616   f W95 Extended (LBA)
/dev/sda5         819,204,096 1,024,004,095   204,800,000   7 NTFS / exFAT / HPFS
/dev/sda6       1,024,006,144 1,543,921,663   519,915,520   7 NTFS / exFAT / HPFS
/dev/sda7       1,543,923,712 1,953,521,663   409,597,952   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 22.4 GiB, 24015495168 bytes, 46905264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63    11,711,384    11,711,322  82 Linux swap / Solaris
/dev/sdc2          11,711,385   304,672,322   292,960,938  83 Linux
/dev/sdc3         304,672,725   597,634,064   292,961,340   7 NTFS / exFAT / HPFS
/dev/sdc4         597,634,126   976,768,064   379,133,939   5 Extended
/dev/sdc5         597,634,128   792,952,334   195,318,207   7 NTFS / exFAT / HPFS
/dev/sdc6         792,952,398   976,768,064   183,815,667  83 Linux


Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 14.4 GiB, 15472047104 bytes, 30218842 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048    30,218,841    30,216,794   c W95 FAT32 (LBA)
```

---

### Post by fullon on 2016-12-12
```
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        C622674622673A97                       ntfs       System Reserved
/dev/sda2        86425FCB425FBE9D                       ntfs       
/dev/sda3        FA4AAF3A4AAEF315                       ntfs       Work
/dev/sda5        A0346AAE346A86DE                       ntfs       Utils
/dev/sda6        7E308EE5308EA3AD                       ntfs       Music
/dev/sda7        244E9E6E4E9E388E                       ntfs       Video
/dev/sdc1        04e3b14d-d53a-4f6a-994c-56e230d5b857   swap       
/dev/sdc2        acc748d0-58fd-43ee-bc85-27139a175572   ext4       
/dev/sdc3        F05C7CC35C7C865E                       ntfs       Music_140GB
/dev/sdc5        1E4C464C4C461EC1                       ntfs       Videos_90GB
/dev/sdc6        f9149e13-9e46-41f1-9897-ddd2f2b8a0b3   ext4       
/dev/sdd1        B85E-21AA                              vfat       UBUNTU16

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Dec 12 15:07 ata-HGST_HTS541010A9E680_JD1000CH2VH6AJ -> ../../sda
lrwxrwxrwx 1 root root 10 Dec 12 15:07 ata-HGST_HTS541010A9E680_JD1000CH2VH6AJ-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Dec 12 15:07 ata-HGST_HTS541010A9E680_JD1000CH2VH6AJ-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Dec 12 15:07 ata-HGST_HTS541010A9E680_JD1000CH2VH6AJ-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Dec 12 15:07 ata-HGST_HTS541010A9E680_JD1000CH2VH6AJ-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Dec 12 15:07 ata-HGST_HTS541010A9E680_JD1000CH2VH6AJ-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Dec 12 15:07 ata-HGST_HTS541010A9E680_JD1000CH2VH6AJ-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Dec 12 15:07 ata-HGST_HTS541010A9E680_JD1000CH2VH6AJ-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 Dec 12 15:07 ata-LITEONIT_LMS-24L6M-HP_002320101563 -> ../../sdb
lrwxrwxrwx 1 root root  9 Dec 12 15:07 ata-SAMSUNG_HM500JI_S1WFJDSSB22325 -> ../../sdc
lrwxrwxrwx 1 root root 10 Dec 12 15:07 ata-SAMSUNG_HM500JI_S1WFJDSSB22325-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Dec 12 15:07 ata-SAMSUNG_HM500JI_S1WFJDSSB22325-part2 -> ../../sdc2
lrwxrwxrwx 1 root root 10 Dec 12 15:07 ata-SAMSUNG_HM500JI_S1WFJDSSB22325-part3 -> ../../sdc3
lrwxrwxrwx 1 root root 10 Dec 12 15:07 ata-SAMSUNG_HM500JI_S1WFJDSSB22325-part4 -> ../../sdc4
lrwxrwxrwx 1 root root 10 Dec 12 15:07 ata-SAMSUNG_HM500JI_S1WFJDSSB22325-part5 -> ../../sdc5
lrwxrwxrwx 1 root root 10 Dec 12 15:07 ata-SAMSUNG_HM500JI_S1WFJDSSB22325-part6 -> ../../sdc6
lrwxrwxrwx 1 root root  9 Dec 12 15:03 ata-hp_BD_CMB_UJ162_WP94_013866 -> ../../sr0
lrwxrwxrwx 1 root root  9 Dec 12 15:07 usb-Kingston_DataTraveler_3.0_60A44C3FAFD5F030397B0113-0:0 -> ../../sdd
lrwxrwxrwx 1 root root 10 Dec 12 15:07 usb-Kingston_DataTraveler_3.0_60A44C3FAFD5F030397B0113-0:0-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 Dec 12 15:07 wwn-0x5000cca79ae839bb -> ../../sda
lrwxrwxrwx 1 root root 10 Dec 12 15:07 wwn-0x5000cca79ae839bb-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Dec 12 15:07 wwn-0x5000cca79ae839bb-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Dec 12 15:07 wwn-0x5000cca79ae839bb-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Dec 12 15:07 wwn-0x5000cca79ae839bb-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Dec 12 15:07 wwn-0x5000cca79ae839bb-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Dec 12 15:07 wwn-0x5000cca79ae839bb-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Dec 12 15:07 wwn-0x5000cca79ae839bb-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 Dec 12 15:07 wwn-0x50024e900265e40b -> ../../sdc
lrwxrwxrwx 1 root root 10 Dec 12 15:07 wwn-0x50024e900265e40b-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Dec 12 15:07 wwn-0x50024e900265e40b-part2 -> ../../sdc2
lrwxrwxrwx 1 root root 10 Dec 12 15:07 wwn-0x50024e900265e40b-part3 -> ../../sdc3
lrwxrwxrwx 1 root root 10 Dec 12 15:07 wwn-0x50024e900265e40b-part4 -> ../../sdc4
lrwxrwxrwx 1 root root 10 Dec 12 15:07 wwn-0x50024e900265e40b-part5 -> ../../sdc5
lrwxrwxrwx 1 root root 10 Dec 12 15:07 wwn-0x50024e900265e40b-part6 -> ../../sdc6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdc2/boot/grub/grub.cfg: ===========================

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
set root='hd2,msdos2'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos2 --hint-efi=hd2,msdos2 --hint-baremetal=ahci2,msdos2  acc748d0-58fd-43ee-bc85-27139a175572
else
  search --no-floppy --fs-uuid --set=root acc748d0-58fd-43ee-bc85-27139a175572
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-acc748d0-58fd-43ee-bc85-27139a175572' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos2 --hint-efi=hd2,msdos2 --hint-baremetal=ahci2,msdos2  acc748d0-58fd-43ee-bc85-27139a175572
    else
      search --no-floppy --fs-uuid --set=root acc748d0-58fd-43ee-bc85-27139a175572
    fi
    linux    /boot/vmlinuz-4.4.0-53-generic.efi.signed root=UUID=acc748d0-58fd-43ee-bc85-27139a175572 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.4.0-53-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-acc748d0-58fd-43ee-bc85-27139a175572' {
    menuentry 'Ubuntu, with Linux 4.4.0-53-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-53-generic-advanced-acc748d0-58fd-43ee-bc85-27139a175572' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos2 --hint-efi=hd2,msdos2 --hint-baremetal=ahci2,msdos2  acc748d0-58fd-43ee-bc85-27139a175572
        else
          search --no-floppy --fs-uuid --set=root acc748d0-58fd-43ee-bc85-27139a175572
        fi
        echo    'Loading Linux 4.4.0-53-generic ...'
        linux    /boot/vmlinuz-4.4.0-53-generic.efi.signed root=UUID=acc748d0-58fd-43ee-bc85-27139a175572 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-53-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-53-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-53-generic-init-upstart-acc748d0-58fd-43ee-bc85-27139a175572' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos2 --hint-efi=hd2,msdos2 --hint-baremetal=ahci2,msdos2  acc748d0-58fd-43ee-bc85-27139a175572
        else
          search --no-floppy --fs-uuid --set=root acc748d0-58fd-43ee-bc85-27139a175572
        fi
        echo    'Loading Linux 4.4.0-53-generic ...'
        linux    /boot/vmlinuz-4.4.0-53-generic.efi.signed root=UUID=acc748d0-58fd-43ee-bc85-27139a175572 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-53-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-53-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-53-generic-recovery-acc748d0-58fd-43ee-bc85-27139a175572' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos2 --hint-efi=hd2,msdos2 --hint-baremetal=ahci2,msdos2  acc748d0-58fd-43ee-bc85-27139a175572
        else
          search --no-floppy --fs-uuid --set=root acc748d0-58fd-43ee-bc85-27139a175572
        fi
        echo    'Loading Linux 4.4.0-53-generic ...'
        linux    /boot/vmlinuz-4.4.0-53-generic.efi.signed root=UUID=acc748d0-58fd-43ee-bc85-27139a175572 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-53-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-31-generic-advanced-acc748d0-58fd-43ee-bc85-27139a175572' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos2 --hint-efi=hd2,msdos2 --hint-baremetal=ahci2,msdos2  acc748d0-58fd-43ee-bc85-27139a175572
        else
          search --no-floppy --fs-uuid --set=root acc748d0-58fd-43ee-bc85-27139a175572
        fi
        echo    'Loading Linux 4.4.0-31-generic ...'
        linux    /boot/vmlinuz-4.4.0-31-generic.efi.signed root=UUID=acc748d0-58fd-43ee-bc85-27139a175572 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-31-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-31-generic (upstart)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-31-generic-init-upstart-acc748d0-58fd-43ee-bc85-27139a175572' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos2 --hint-efi=hd2,msdos2 --hint-baremetal=ahci2,msdos2  acc748d0-58fd-43ee-bc85-27139a175572
        else
          search --no-floppy --fs-uuid --set=root acc748d0-58fd-43ee-bc85-27139a175572
        fi
        echo    'Loading Linux 4.4.0-31-generic ...'
        linux    /boot/vmlinuz-4.4.0-31-generic.efi.signed root=UUID=acc748d0-58fd-43ee-bc85-27139a175572 ro  quiet splash $vt_handoff init=/sbin/upstart
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-31-generic
    }
    menuentry 'Ubuntu, with Linux 4.4.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-31-generic-recovery-acc748d0-58fd-43ee-bc85-27139a175572' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos2 --hint-efi=hd2,msdos2 --hint-baremetal=ahci2,msdos2  acc748d0-58fd-43ee-bc85-27139a175572
        else
          search --no-floppy --fs-uuid --set=root acc748d0-58fd-43ee-bc85-27139a175572
        fi
        echo    'Loading Linux 4.4.0-31-generic ...'
        linux    /boot/vmlinuz-4.4.0-31-generic.efi.signed root=UUID=acc748d0-58fd-43ee-bc85-27139a175572 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.4.0-31-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sdc2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc2 during installation
UUID=acc748d0-58fd-43ee-bc85-27139a175572 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc1 during installation
UUID=04e3b14d-d53a-4f6a-994c-56e230d5b857 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdc2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  17.715095997 = 19.021439488   boot/grub/grub.cfg                             1
   6.723797321 = 7.219622400    boot/vmlinuz-4.4.0-31-generic                  2
  49.723686695 = 53.390402048   boot/vmlinuz-4.4.0-31-generic.efi.signed       1
  10.219791889 = 10.973417984   boot/vmlinuz-4.4.0-53-generic                  1
  10.380066395 = 11.145511424   boot/vmlinuz-4.4.0-53-generic.efi.signed       1
   6.723797321 = 7.219622400    vmlinuz                                        2
  10.509636402 = 11.284636160   boot/initrd.img-4.4.0-31-generic               2
  25.969215870 = 27.884233216   boot/initrd.img-4.4.0-53-generic               4
  10.509636402 = 11.284636160   initrd.img                                     2
  10.509636402 = 11.284636160   initrd.img.old                                 2

=========================== sdd1/boot/grub/grub.cfg: ===========================

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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdd1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/8513/mounts) leaked on lvs invocation. Parent PID 21624: bash
File descriptor 63 (pipe:[64098]) leaked on lvs invocation. Parent PID 21624: bash
```

---

### Post by oldfred on 2016-12-12
Please use code tags on longer text or teminal output.
But with Boot-Repair's summary report better still just to post the link it gives.

You show Windows installed in BIOS/MBR mode on sda.
And even sdc is shown as MBR(msdos).

The install of grub-efi-amd64 if for UEFI boot which must have an ESP - efi system partition on drive seen as sda. And that drive then should be gpt partitioned as well as drive you install Ubuntu into.

So you must have a newer UEFI system, but have all installs in the 35 year old BIOS/MBR configuration.

Reboot Boot-Repair/live installer in BIOS mode and then install grub to sdc, using advanced mode. Do not run auto fix as that installs grub to the MBR of all drives.
 Best to keep Windows boot loader in sda. Only if your system would not let you boot from sdc, should you then install grub to sda.
Windows will normally boot from grub menu. But if hibernation gets turned on in Windows or Windows needs chkdsk then grub will not boot it. Best to have Windows repair/recovery disk, but sometimes you can directly boot sda and get into Windows repair console to fix things when grub cannot boot it.

---

### Post by fullon on 2016-12-12
Thank you! I'll navigate through all this info, and come back with feedback.
PS: Sorry for the bad manners, will keep your advice in mind.

---

### Post by fullon on 2016-12-13
OK, I think I totaled my MBR, GPT, uefi, whatever on both HDs and on the M.2 SSD. Nothing works. Grub2 wont install in any HD.

I'm assuming I lost all data in all HDs, but that's ok. I tried a lot of things, Gparted, boot disks, etc, I think I just made it worse.

Is there a way to restore the HDs to factory default, so that I can at least install Ubuntu on it? I don't care about loosing data, I just want to be able to install Ubuntu in an easy way.
Thank you.

---

### Post by oldfred on 2016-12-13
Since you were able to boot installer in UEFI mode, then your system must be UEFI.

But how you boot install media, is then how it installs, so if you want UEFI you must boot installer, both Windows & Ubuntu in UEFI mode. Windows 7 on DVD defaults to BIOS only. You can convert a Windows 7 installer to UEFI, by copying to flash drive and moving files around.

Do you want UEFI or BIOS? And dual boot or just Ubuntu?
If installing Ubuntu on its own drive, you can use the newer gpt partitioning but configure it for either UEFI or BIOS. I do that by adding both an ESP - efi system partition and a bios_grub partition. But Ubuntu only installs grub to ESP on sda in UEFI mode. 

Windows only installs in UEFI mode to gpt drives and only in BIOS mode to MBR drives. I did have an old XP install on my old BIOS only system, but Ubuntu in BIOS mode on gpt drive. But when Windows 8 came out using UEFI only, I started adding both ESP & bios_grub to all new drives. Old system booted BIOS, but could then move drive to newer UEFI system and reinstall grub to boot in UEFI mode.

You can just use gparted to create/delete/repartition as desired. If you convert from MBR to gpt or vice versa it should erase drive. You can use gdisk to convert without losing data (usually).

Do you want UEFI or BIOS. MBR or gpt?
Best to install Windows first, it requires extra partitions especially in UEFI mode.

Lots of info on UEFI in link in my signature. And links to many more helpful instructions.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

---

### Post by fullon on 2016-12-13
I want UEFI and/or GPT. I used Gparted and gdisk to convert MBR to GPT, but this did not solve the problem. I think I have done something that messed up the part of the HD where MBR or GPT is located. I spend like 4 hours trying several approaches, but ubuntu install always halt with the message:

the 'grub-efi-amd64-signed' package failed to install into /target/.  Without the GRUB boot loader, the installed system will not boot. I have  windows installed in some partition of sda.

Is there a way to restore the HD to factory default. Particularly the partition table/MBR/GPT? I just want to install Ubuntu.
Thank you.

---

### Post by oldfred on 2016-12-13
Systems installed in BIOS mode, will not work on gpt partitioned drive.
You should be able to convert back to MBR, if desired using the reverse of whatever you did.

You may have to repair WIndows with chkdsk, fixMBR and fixBoot. 
And then repair Linux partitions and reinstall grub.

---

### Post by fullon on 2016-12-14
Thank you.
Tried to follow your instructions, it did not work.

Using Gparted I deleted all partitions on the sda 1TB HD, created a new GPT partition table and then created a swap partition and two ext4 partitions. Tried to install ubuntu, but it did not work, again with the same error.

Why is this not working? Makes no sense to me. Checked the hard drive with different tools and it presents no errors.
Any help is appreciated.
Thanks.

---

### Post by oldfred on 2016-12-14
If you have a drive with gpt and create partitions in advance you must also create the ESP - efi system partition which is a FAT32 formatted partition 300 to 500MB with the boot flag for UEFI install. And/or create a bios_grub partition which is 1 or 2MB unformatted with bios_grub flag.

It is recommended that ESP be first or near beginning of drive, particularlly the new very large Multiple TB drives. The bios_grub can be anywhere on drive, but I normally make it my second partition. And I have both on most drives and large flash drives.

But how you boot installer UEFI or BIOS/CSM/Legacy will determine which of the two partitions is used. And then how you must have UEFI set to boot. How you boot installer, is not necessarily the same as default boot settings in UEFI. If you want UEFI make sure to always boot in UEFI mode.

       One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL]
 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
      
 suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534) 
    
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
     [URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by fullon on 2016-12-14
Thank you, oldfred! the information on the first three paragraphs of your post above just solved my issue!
Now I managed to install Ubuntu, and will install Win7 (probably will have to reinstall Ubuntu after that, but it is ok).

You just saved the day, but I guess you do that several times per day... ;)
Thank you!

---

### Post by oldfred on 2016-12-14
Glad you got it working.

Windows 7 needs to be converted from DVD to flash drive to install in UEFI mode. And a couple files moved so UEFI can find the default boot of /EFI/Boot/bootx64.efi.
Best to let Windows install as in UEFI mode it wants a variety of partitions.

       You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Convert Windows 7 install to UEFI This user said he need the repair/recovery from his Windows 8 to convert Windows 7
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)

---

### Post by fullon on 2016-12-15
Dear oldfred,
Now it's being hard to install Win7 (or Win10). The system does not recognize the USB flash drive. I gave it priority in the boot sequence, but the system goes straight to Grub2. I tried changing Legacy Support and Secure boot, but in whatever configuration it does not work, the USB is not detected in any USB port. (now it is Legacy Support - enabled and Secure Boot - disabled).

The system recognizes the Ubuntu installation flash drive, but not any windows flash drive. I tried several online guides to make a Windows 7 USB Installler bootable for UEFI boot (like this: [https://www.youtube.com/watch?v=sDm8rWr3dV8](https://www.youtube.com/watch?v=sDm8rWr3dV8) ) also used , but none of them work. Tried this [https://support.lenovo.com/br/en/documents/ht076615](https://support.lenovo.com/br/en/documents/ht076615) to prep the flash drive, with no results.

To create UEFI bootable USB media that can be used to install  Microsoft Windows 7 or Windows 8 64-bit operating systems on Lenovo  Think Branded computers, follow the steps below:
 
[LIST=1]
[*]Open a Command Prompt with Administrator privileges in either Windows 7 Pro or Windows 8 Pro. 
[*]Insert the target USB boot media device into an available USB port. 
[*]Type "DiskPart" in the command prompt. 
[*]Type "List Disk” (make note of the disk number of the target USB drive). 
[*]Type "Select Disk X”, where X is the target USB drive noted in step 4. 
[*]Type "Clean”. 
[*]Type "Create Partition Primary”. 
[*]Type "format FS=fat32 quick”. 
[*]Type "Active”. 
[*]Type "Assign". 
[*]Type "list volume". 
[*]Type "Exit". 
[/LIST]


I'm missing something, because it boots Ubuntu install flash drive, but not a Win7 or Win10 flash drive. I can make it boot a Win7 DVD, but I'm afraid it will turn the drive back to MBR.
Any ideas?
Thank you.

---

### Post by oldfred on 2016-12-15
That looks like instructions to just create a bootable flash drive.
That works then when you extract Windows 8 or 10.

But Windows 7 does not have /EFI/Boot/bootmgr. You have to move files around. UEFI only boots from that file. Ubuntu uses same file name, but obviously different actual files.

You must have the 64 bit version of Windows.

Do not know if the Windows installers, copy files for a Windows 7 ISO correctly or not. Newer versions of Windows have files in correct places
See step 11.
[https://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](https://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)

Update, same issue with lots more info from Rod Smith (author of gdisk)
[http://askubuntu.com/questions/860729/is-it-possible-to-install-windows-7-alongside-with-ubuntu-and-windows-10-dualboo?noredirect=1#comment1327830_860729](http://askubuntu.com/questions/860729/is-it-possible-to-install-windows-7-alongside-with-ubuntu-and-windows-10-dualboo?noredirect=1#comment1327830_860729)

---

### Post by fullon on 2016-12-20
Dear Oldfred,
I gave up that hard drive, could not manage to make it dual boot in spite of inumerous system installations. How do I set "the boot flag for UEFI install"?

Now I have another problem. I removed the old hard drive and replaced it by an old Intel SSD 80 GB. I deleted everything on the drive and created a GPT partition table with Gparted. I installed ubuntu using a GPT flash drive created with Rufus. During the installation, I created an EFI partition and a BIOS partition in addition to a partition to Ubunto and another partition where I plan to install Win10.

The problem is that grub is not launching on startup. The system boots directly in Ubuntu, without passing through the boot manager (Grub). I tried to use Grub Customizer to see if it could fix it, but it didn't.
Any ideas?

Thanks!

---

### Post by oldfred on 2016-12-20
In gparted the boot flag is in right click set flags.

If you only have one install, grub assumes you want to directly boot that install. I reset mine to 3 sec from default of 10 sec, just so I have a chance to press key to  get grub menu.

If UEFI you must press escape key (perhaps more than once) between UEFI screen and grub starting boot. 
If BIOS you hold shift key until grub menu appears from BIOS screen.

---

### Post by fullon on 2016-12-24
Thank you, oldfred. You really helped me a lot.

I managed to get the system the way I wanted, even better because I ended putting the old Intel SSD to use. The only exception is that I need to press F9 during boot to access GRUB, otherwise the system boots straight into Win10.

I have two other notebooks, all from HP, I use them for academic research purposes, mainly processing X-ray crystallography data in Ubuntu. A Skylake, a Broadwell and this older Haswell, all with SSDs, but in the case of the newer ones the Ubuntu/Win10 dual boot configuration was straight forward, grub appears and I just select what I want ( [http://www.fullonline.org/science/bg_ubuntu_23-12-2016.png](http://www.fullonline.org/science/bg_ubuntu_23-12-2016.png) ). This Haswell for some reason is stubborn, but it is not really a problem, I just have to press F9 during booting (and I lost a some days trying to make it work).

Thank you!

---

### Post by oldfred on 2016-12-24
If you have other issues best to start a new thread with those issues in title.
Glad you have it working.

There are some other work arounds for difficult systems. Some also recommend rEFInd, which is another boot manager (menu). UEFI is a boot manager & grub is both a boot manager & boot loader.
       Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)
Rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by krio on 2017-12-21
> **fullon said:**
> Dear Oldfred,
I gave up that hard drive, could not manage to make it dual boot in spite of inumerous system installations. How do I set "the boot flag for UEFI install"?

Now I have another problem. I removed the old hard drive and replaced it by an old Intel SSD 80 GB. I deleted everything on the drive and created a GPT partition table with Gparted. I installed ubuntu using a GPT flash drive created with Rufus. During the installation, I created an EFI partition and a BIOS partition in addition to a partition to Ubunto and another partition where I plan to install Win10.

The problem is that grub is not launching on startup. The system boots directly in Ubuntu, without passing through the boot manager (Grub). I tried to use Grub Customizer to see if it could fix it, but it didn't.
Any ideas?

Thanks!

unfortunately for me that didn't work for me. what worked for me is simply as suggested in this -> [http://linuxbsdos.com/2017/08/29/solution-to-grub-efi-amd64-signed-package-failed-to-install-into-target/](http://linuxbsdos.com/2017/08/29/solution-to-grub-efi-amd64-signed-package-failed-to-install-into-target/) link to enable internet (WiFi or Ethernet) and check the box that says install updates while installing, at the beginning of the installation

---

### Post by sankalpkhare on 2018-06-18
> **krio said:**
> unfortunately for me that didn't work for me. what worked for me is simply as suggested in this -> [http://linuxbsdos.com/2017/08/29/solution-to-grub-efi-amd64-signed-package-failed-to-install-into-target/](http://linuxbsdos.com/2017/08/29/solution-to-grub-efi-amd64-signed-package-failed-to-install-into-target/) link to enable internet (WiFi or Ethernet) and check the box that says install updates while installing, at the beginning of the installation

This worked perfectly for me as well, in fixing the same error while installing Linux Mint 18.3 (Cinnamon). Thanks, @krio!

---

