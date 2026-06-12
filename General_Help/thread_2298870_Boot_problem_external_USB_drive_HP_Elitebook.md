---
title: "Boot problem external USB drive HP Elitebook"
date: 2015-10-14
forum: General Help
---

### Post by Urs_Helfenstein on 2015-10-14
Hello,

I struggle since a longer time with an issue which is as follows:

I created a USB HD with an Ubuntu to use it at the work place that I do not need to touch the system installed by the company. This works perfectly for all computers. Just plugin and use Ubuntu. There is one exception. It did not work on all HP Elitbooks I tried so far. 

Grub is loading but it went into the "grub rescue" with the error message:

```
error: attempt to read or write outside of disk 'hd1'. 
Entering rescue mode... 
grub rescue>
```

I used now the tool "Boot Repair Disk" (a live Linux to fix boot issues). This helps a bit, now the Grub menu is shown, but if I chose to start Ubuntu the same error message appears".

Here you can see the report of Boot Repair. May be someone could point me in the right direction to solve that. As said, on all the other computers and Laptops I tried so far it worked. Also the HP support pointed to some safety settings within the BIOS but it did not solve the issue.

Thank you for any help,
Urs




```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]

============================= Boot Info Summary: ===============================
 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 82acfc50-9cfa-4557-83b8-c2f1201c4522 root hd1,msdos1 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub.
sda1: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD
sda2: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       249860095 sectors, but according to the info from 
                       fdisk, it has 249875009 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe
sda3: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
sdb1: __________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img
sdb2: __________________________________________________________________________
    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 1677719552.
    Operating System:  
    Boot files:        
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1    *             63       208,844       208,782   7 NTFS / exFAT / HPFS
/dev/sda2             208,845   250,083,854   249,875,010   7 NTFS / exFAT / HPFS
/dev/sda3         250,085,376   414,099,455   164,014,080   7 NTFS / exFAT / HPFS

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdb1    *          2,048 1,677,718,191 1,677,716,144  83 Linux
/dev/sdb2       1,677,719,552 1,953,458,175   275,738,624   c W95 FAT32 (LBA)

"blkid" output: ________________________________________________________________
Device           UUID                                   TYPE       LABEL
/dev/loop0                                              squashfs   
/dev/sda1        9EFC0482FC045745                       ntfs       System-reserviert
/dev/sda2        D2EC063CEC061B7D                       ntfs       BOOT
/dev/sda3        A63CE3DB3CE3A511                       ntfs       Volume
/dev/sdb1        82acfc50-9cfa-4557-83b8-c2f1201c4522   ext4       sdh1
/dev/sdb2        8146-2145                              vfat       
/dev/sr0                                                iso9660    Boot-Repair-Disk 64bit
/dev/zram0       480a6ec7-e4e5-45ca-a2ce-53f0571c0f13   swap       
========================= "ls -l /dev/disk/by-id" output: ======================
total 0
lrwxrwxrwx 1 root root  9 Oct 14 10:44 ata-Samsung_SSD_840_PRO_Series_S12RNEAD352966K -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 14 10:44 ata-Samsung_SSD_840_PRO_Series_S12RNEAD352966K-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 14 10:44 ata-Samsung_SSD_840_PRO_Series_S12RNEAD352966K-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 14 10:44 ata-Samsung_SSD_840_PRO_Series_S12RNEAD352966K-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Oct 14 10:36 ata-hp_BD-RE_BT10N_KVGAAPE3600 -> ../../sr0
lrwxrwxrwx 1 root root  9 Oct 14 10:44 usb-WD_My_Passport_0748_575851314335324E30323539-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Oct 14 10:36 usb-WD_My_Passport_0748_575851314335324E30323539-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Oct 14 10:36 usb-WD_My_Passport_0748_575851314335324E30323539-0:0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root  9 Oct 14 10:44 wwn-0x50025385502955a3 -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 14 10:44 wwn-0x50025385502955a3-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 14 10:44 wwn-0x50025385502955a3-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 14 10:44 wwn-0x50025385502955a3-part3 -> ../../sda3
================================ Mount points: =================================
Device           Mount_Point              Type       Options
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/lubuntu/sdh1      ext4       (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb2        /media/lubuntu/8146-2145 vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)

=========================== sdb1/boot/grub/grub.cfg: ===========================
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
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
else
  search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
fi
    font="/usr/share/grub/unicode.pf2"
fi
if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=de_DE
  insmod gettext
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
 recordfail
 load_video
 gfxmode $linux_gfx_mode
 insmod gzio
 insmod part_msdos
 insmod ext2
 set root='hd1,msdos1'
 if [ x$feature_platform_search_hint = xy ]; then
   search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
 else
   search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
 fi
 linux /boot/vmlinuz-3.13.0-65-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
 initrd /boot/initrd.img-3.13.0-65-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
 menuentry 'Ubuntu, with Linux 3.13.0-65-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-65-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-65-generic ...'
  linux /boot/vmlinuz-3.13.0-65-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-65-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-65-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-65-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-65-generic ...'
  linux /boot/vmlinuz-3.13.0-65-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-65-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-63-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-63-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-63-generic ...'
  linux /boot/vmlinuz-3.13.0-63-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-63-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-63-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-63-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-63-generic ...'
  linux /boot/vmlinuz-3.13.0-63-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-63-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-57-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-57-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-57-generic ...'
  linux /boot/vmlinuz-3.13.0-57-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-57-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-57-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-57-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-57-generic ...'
  linux /boot/vmlinuz-3.13.0-57-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-57-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-55-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-55-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-55-generic ...'
  linux /boot/vmlinuz-3.13.0-55-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-55-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-55-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-55-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-55-generic ...'
  linux /boot/vmlinuz-3.13.0-55-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-55-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-54-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-54-generic ...'
  linux /boot/vmlinuz-3.13.0-54-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-54-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-54-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-54-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-54-generic ...'
  linux /boot/vmlinuz-3.13.0-54-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-54-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-53-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-53-generic ...'
  linux /boot/vmlinuz-3.13.0-53-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-53-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-53-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-53-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-53-generic ...'
  linux /boot/vmlinuz-3.13.0-53-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-53-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-52-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-52-generic ...'
  linux /boot/vmlinuz-3.13.0-52-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-52-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-52-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-52-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-52-generic ...'
  linux /boot/vmlinuz-3.13.0-52-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-52-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-51-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-51-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-51-generic ...'
  linux /boot/vmlinuz-3.13.0-51-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-51-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-51-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-51-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-51-generic ...'
  linux /boot/vmlinuz-3.13.0-51-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-51-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-49-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-49-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-49-generic ...'
  linux /boot/vmlinuz-3.13.0-49-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-49-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-49-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-49-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-49-generic ...'
  linux /boot/vmlinuz-3.13.0-49-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-49-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-48-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-48-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-48-generic ...'
  linux /boot/vmlinuz-3.13.0-48-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-48-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-48-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-48-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-48-generic ...'
  linux /boot/vmlinuz-3.13.0-48-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-48-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-46-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-46-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-46-generic ...'
  linux /boot/vmlinuz-3.13.0-46-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-46-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-46-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-46-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-46-generic ...'
  linux /boot/vmlinuz-3.13.0-46-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-46-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-45-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-45-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-45-generic ...'
  linux /boot/vmlinuz-3.13.0-45-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-45-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-45-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-45-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-45-generic ...'
  linux /boot/vmlinuz-3.13.0-45-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-45-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-44-generic ...'
  linux /boot/vmlinuz-3.13.0-44-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-44-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-44-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-44-generic ...'
  linux /boot/vmlinuz-3.13.0-44-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-44-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-43-generic ...'
  linux /boot/vmlinuz-3.13.0-43-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-43-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-43-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-43-generic ...'
  linux /boot/vmlinuz-3.13.0-43-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-43-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-40-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-40-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-40-generic ...'
  linux /boot/vmlinuz-3.13.0-40-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-40-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-40-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-40-generic ...'
  linux /boot/vmlinuz-3.13.0-40-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-40-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-37-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-37-generic ...'
  linux /boot/vmlinuz-3.13.0-37-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-37-generic
 }
 menuentry 'Ubuntu, with Linux 3.13.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-37-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.13.0-37-generic ...'
  linux /boot/vmlinuz-3.13.0-37-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.13.0-37-generic
 }
 menuentry 'Ubuntu, with Linux 3.8.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-35-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.8.0-35-generic ...'
  linux /boot/vmlinuz-3.8.0-35-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.8.0-35-generic
 }
 menuentry 'Ubuntu, with Linux 3.8.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-35-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.8.0-35-generic ...'
  linux /boot/vmlinuz-3.8.0-35-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.8.0-35-generic
 }
 menuentry 'Ubuntu, with Linux 3.5.0-42-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-42-generic-advanced-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  gfxmode $linux_gfx_mode
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.5.0-42-generic ...'
  linux /boot/vmlinuz-3.5.0-42-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro  quiet splash $vt_handoff
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.5.0-42-generic
 }
 menuentry 'Ubuntu, with Linux 3.5.0-42-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-42-generic-recovery-82acfc50-9cfa-4557-83b8-c2f1201c4522' {
  recordfail
  load_video
  insmod gzio
  insmod part_msdos
  insmod ext2
  set root='hd1,msdos1'
  if [ x$feature_platform_search_hint = xy ]; then
    search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
  else
    search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
  fi
  echo 'Loading Linux 3.5.0-42-generic ...'
  linux /boot/vmlinuz-3.5.0-42-generic root=UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 ro recovery nomodeset 
  echo 'Loading initial ramdisk ...'
  initrd /boot/initrd.img-3.5.0-42-generic
 }
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
 insmod part_msdos
 insmod ext2
 set root='hd1,msdos1'
 if [ x$feature_platform_search_hint = xy ]; then
   search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
 else
   search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
 fi
 knetbsd /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
 insmod part_msdos
 insmod ext2
 set root='hd1,msdos1'
 if [ x$feature_platform_search_hint = xy ]; then
   search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  82acfc50-9cfa-4557-83b8-c2f1201c4522
 else
   search --no-floppy --fs-uuid --set=root 82acfc50-9cfa-4557-83b8-c2f1201c4522
 fi
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-D2EC063CEC061B7D' {
 insmod part_msdos
 insmod ntfs
 set root='hd0,msdos2'
 if [ x$feature_platform_search_hint = xy ]; then
   search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  D2EC063CEC061B7D
 else
   search --no-floppy --fs-uuid --set=root D2EC063CEC061B7D
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
=============================== sdb1/etc/fstab: ================================
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=82acfc50-9cfa-4557-83b8-c2f1201c4522 /               ext4    errors=remount-ro 0       1
# /data was on /dev/sdb5 during installation
# /windows was on /dev/sdb6 during installation
#UUID=B5A8-B429  /windows        vfat    utf8,umask=007,gid=46 0       1
#/dev/disk/by-id/usb-WD_My_Passport_0748_575851314335324E30323539-0:0-part5 /mnt/usb-WD_My_Passport_0748_575851314335324E30323539-0:0-part5 auto nosuid,nodev,nofail 0 0
#//chnls26/ablagen_r\046d/Ablagen\040R&D/Srd_M/D_SRDM_Member/UHE /mnt/UHE cifs _netdev,cred=/etc/UHEpass,uid=dem,gid=users    1 2
//chnls26/ablagen_r\046d/Ablagen\040R&D/Srd_M/D_SRDM_Member/UHE /mnt/UHE cifs auto,credentials=/etc/UHEpass,uid=dem,gid=users    0 0
--------------------------------------------------------------------------------
========= Devices which don't seem to have a corresponding hard drive: =========
{All_DMRaid} 
=============================== StdErr Messages: ===============================
ERROR: ddf1: Cannot find physical drive description on /dev/sda!
ERROR: ddf1: setting up RAID device /dev/sda
ERROR: ddf1: Cannot find physical drive description on /dev/sda!
ERROR: ddf1: setting up RAID device /dev/sda
ERROR: ddf1: Cannot find physical drive description on /dev/sda!
ERROR: ddf1: setting up RAID device /dev/sda
cat: write error: Broken pipe
cat: write error: Broken pipe
ERROR: ddf1: Cannot find physical drive description on /dev/sda!
ERROR: ddf1: setting up RAID device /dev/sda
File descriptor 9 (/proc/20972/mounts) leaked on lvs invocation. Parent PID 29114: bash
File descriptor 63 (pipe:[39610]) leaked on lvs invocation. Parent PID 29114: bash
  No volume groups found
ADDITIONAL INFORMATION :
=================== log of boot-info 2015-10-14__10h44 ===================
boot-info version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
ERROR: ddf1: Cannot find physical drive description on /dev/sda!
ERROR: ddf1: setting up RAID device /dev/sda
ERROR: ddf1: Cannot find physical drive description on /dev/sda!
ERROR: ddf1: setting up RAID device /dev/sda
ERROR: ddf1: Cannot find physical drive description on /dev/sda!
ERROR: ddf1: setting up RAID device /dev/sda
ERROR: ddf1: Cannot find physical drive description on /dev/sda!
ERROR: ddf1: setting up RAID device /dev/sda
ERROR: ddf1: Cannot find physical drive description on /dev/sda!
ERROR: ddf1: setting up RAID device /dev/sda
File descriptor 9 (/proc/20972/mounts) leaked on lvs invocation. Parent PID 22471: /bin/sh
No volume groups found
boot-info is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal -- debian-installer/language=de keyboard-configuration/layoutcode=ch
=================== os-prober:
/dev/sdb1:Ubuntu 14.04.3 LTS (14.04):Ubuntu:linux
=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="System-reserviert" UUID="9EFC0482FC045745" TYPE="ntfs"
/dev/sda2: LABEL="BOOT" UUID="D2EC063CEC061B7D" TYPE="ntfs"
/dev/sda3: LABEL="Volume" UUID="A63CE3DB3CE3A511" TYPE="ntfs"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/sdb1: LABEL="sdh1" UUID="82acfc50-9cfa-4557-83b8-c2f1201c4522" TYPE="ext4"
/dev/sdb2: UUID="8146-2145" TYPE="vfat"
/dev/zram0: UUID="480a6ec7-e4e5-45ca-a2ce-53f0571c0f13" TYPE="swap"

1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.
Windows not detected by os-prober on sda2.
=================== /media/lubuntu/sdh1/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Jul  9 07:54 grub.d
total 76
-rwxr-xr-x 1 root root  9424 Jun 26 11:16 00_header
-rwxr-xr-x 1 root root  6058 Apr 10  2014 05_debian_theme
-rwxr-xr-x 1 root root 11608 Apr 11  2014 10_linux
-rwxr-xr-x 1 root root 10412 Apr 11  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mär 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 Apr 11  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 Apr 11  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Okt 14  2012 40_custom
-rwxr-xr-x 1 root root   216 Okt 14  2012 41_custom
-rw-r--r-- 1 root root   483 Okt 14  2012 README
 

=================== /media/lubuntu/sdh1/etc/default/grub :
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
 
=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.

=================== PARTITIONS & DISKS:
sda1 : sda, not-sepboot, no-grubenv nogrub, no-docgrub, no-update-grub, 32, no-boot, no-os, not--efi--part, part-has-no-fstab, part-has-no-fstab, no-nt, no-winload, no-recov-nor-hid, bootmgr, is-winboot, nopakmgr, nogrubinstall, no---usr, part-has-no-fstab, not-sep-usr, standard, not-far, /mnt/boot-sav/sda1.
sda2 : sda, not-sepboot, no-grubenv nogrub, no-docgrub, no-update-grub, 32, no-boot, is-os, not--efi--part, part-has-no-fstab, part-has-no-fstab, no-nt, haswinload, no-recov-nor-hid, bootmgr, is-winboot, nopakmgr, nogrubinstall, no---usr, part-has-no-fstab, not-sep-usr, standard, farbios, /mnt/boot-sav/sda2.
sda3 : sda, not-sepboot, no-grubenv nogrub, no-docgrub, no-update-grub, 32, no-boot, no-os, not--efi--part, part-has-no-fstab, part-has-no-fstab, no-nt, no-winload, no-recov-nor-hid, no-bmgr, notwinboot, nopakmgr, nogrubinstall, no---usr, part-has-no-fstab, not-sep-usr, standard, farbios, /mnt/boot-sav/sda3.
sdb1 : sdb, not-sepboot, grubenv-ok grub2, grub-pc , update-grub, 64, with-boot, is-os, not--efi--part, fstab-without-boot, fstab-without-efi, no-nt, no-winload, no-recov-nor-hid, no-bmgr, notwinboot, apt-get, grub-install, with--usr, fstab-without-usr, not-sep-usr, standard, farbios, /media/lubuntu/sdh1.
sdb2 : sdb, not-sepboot, no-grubenv nogrub, no-docgrub, no-update-grub, 32, no-boot, no-os, not--efi--part, part-has-no-fstab, part-has-no-fstab, no-nt, no-winload, no-recov-nor-hid, no-bmgr, notwinboot, nopakmgr, nogrubinstall, no---usr, part-has-no-fstab, not-sep-usr, standard, farbios, /media/lubuntu/8146-2145.
sda : not-GPT, BIOSboot-not-needed, has-no-EFIpart,  not-usb, has-os, 63 sectors * 512 bytes
sdb : not-GPT, BIOSboot-not-needed, has-no-EFIpart,  usb-disk, has-os, 2048 sectors * 512 bytes

=================== parted -l:
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End    Size    Type     File system  Flags
1      32.3kB  107MB  107MB   primary  ntfs         boot
2      107MB   128GB  128GB   primary  ntfs
3      128GB   212GB  84.0GB  primary  ntfs

Model: WD My Passport 0748 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End     Size   Type     File system  Flags
1      1049kB  859GB   859GB  primary  ext4         boot
2      859GB   1000GB  141GB  primary  fat32        lba

                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
                                                                          
Error: /dev/sr0: unrecognised disk label
                                                                          
Error: /dev/zram0: unrecognised disk label
=================== parted -lm:
BYT;
/dev/sda:256GB:scsi:512:512:msdos:ATA Samsung SSD 840;
1:32.3kB:107MB:107MB:ntfs::boot;
2:107MB:128GB:128GB:ntfs::;
3:128GB:212GB:84.0GB:ntfs::;
BYT;
/dev/sdb:1000GB:scsi:512:512:msdos:WD My Passport 0748;
1:1049kB:859GB:859GB:ext4::boot;
2:859GB:1000GB:141GB:fat32::lba;
                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
                                                                          
Error: /dev/sr0: unrecognised disk label
                                                                          
Error: /dev/zram0: unrecognised disk label

=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sdb2 on /media/lubuntu/8146-2145 type vfat (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
/dev/sdb1 on /media/lubuntu/sdh1 type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk ecryptfs fd full fuse fw0 hidraw0 hidraw1 hpet input kmsg log mapper mei mem net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sdb2 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout tpm0 uhid uinput urandom v4l vga_arbiter vhci vhost-net video0 watchdog watchdog0 zero
ls /dev/mapper:  control
=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  88 2f 03 00 00 00 00 00  |........./......|
00000030  e2 15 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  45 57 04 fc 82 04 fc 9e  |........EW......|
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
=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 cd 2f 03 00  |........?..../..|
00000020  00 00 00 00 80 00 80 00  ff 8f e4 0e 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  7d 1b 06 ec 3c 06 ec d2  |........}...<...|
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
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 46 65  |t.............Fe|
00000190  68 6c 65 72 20 62 65 69  6d 20 4c 65 73 65 6e 20  |hler beim Lesen |
000001a0  64 65 73 20 44 61 74 65  6e 74 72 84 67 65 72 73  |des Datentr.gers|
000001b0  00 0d 0a 42 4f 4f 54 4d  47 52 20 66 65 68 6c 74  |...BOOTMGR fehlt|
000001c0  00 0d 0a 42 4f 4f 54 4d  47 52 20 6b 6f 6d 70 72  |...BOOTMGR kompr|
000001d0  69 6d 69 65 72 74 00 0d  0a 4e 65 75 73 74 61 72  |imiert...Neustar|
000001e0  74 20 6d 69 74 20 53 74  72 67 2b 41 6c 74 2b 45  |t mit Strg+Alt+E|
000001f0  6e 74 66 0d 0a 00 0a 00  8c b1 c1 d7 00 00 55 aa  |ntf...........U.|
00000200
=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 e8 0e  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff a7 c6 09 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  11 a5 e3 3c db e3 3c a6  |...........<..<.|
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
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 46 65  |t.............Fe|
00000190  68 6c 65 72 20 62 65 69  6d 20 4c 65 73 65 6e 20  |hler beim Lesen |
000001a0  64 65 73 20 44 61 74 65  6e 74 72 84 67 65 72 73  |des Datentr.gers|
000001b0  00 0d 0a 42 4f 4f 54 4d  47 52 20 66 65 68 6c 74  |...BOOTMGR fehlt|
000001c0  00 0d 0a 42 4f 4f 54 4d  47 52 20 6b 6f 6d 70 72  |...BOOTMGR kompr|
000001d0  69 6d 69 65 72 74 00 0d  0a 4e 65 75 73 74 61 72  |imiert...Neustar|
000001e0  74 20 6d 69 74 20 53 74  72 67 2b 41 6c 74 2b 45  |t mit Strg+Alt+E|
000001f0  6e 74 66 0d 0a 00 0a 00  8c b1 c1 d7 00 00 55 aa  |ntf...........U.|
00000200
=================== hexdump -n512 -C /dev/sdb2
00000000  eb 58 90 6d 6b 64 6f 73  66 73 00 00 02 20 20 00  |.X.mkdosfs...  .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 70 6f 10 e0 06 01 00  00 00 00 00 02 00 00 00  |.po.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 45 21 46 81 4e  4f 20 4e 41 4d 45 20 20  |..)E!F.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
=================== df -Th:
Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  7.9G   44M  7.8G   1% /
udev           devtmpfs   7.8G   12K  7.8G   1% /dev
tmpfs          tmpfs      1.6G  1.3M  1.6G   1% /run
/dev/sr0       iso9660    614M  614M     0 100% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      7.9G  772K  7.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      7.9G     0  7.9G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sdb2      vfat       132G   11G  122G   8% /media/lubuntu/8146-2145
/dev/sdb1      ext4       788G  396G  353G  53% /media/lubuntu/sdh1
/dev/sda1      fuseblk    102M   25M   78M  24% /mnt/boot-sav/sda1
/dev/sda2      fuseblk    120G  115G  5.0G  96% /mnt/boot-sav/sda2
/dev/sda3      fuseblk     79G   12G   67G  16% /mnt/boot-sav/sda3
=================== fdisk -l:
Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4d9c3739
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      208844      104391    7  HPFS/NTFS/exFAT
/dev/sda2          208845   250083854   124937505    7  HPFS/NTFS/exFAT
/dev/sda3       250085376   414099455    82007040    7  HPFS/NTFS/exFAT
Disk /dev/sdb: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2ab64d88
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1677718191   838858072   83  Linux
/dev/sdb2      1677719552  1953458175   137869312    c  W95 FAT32 (LBA)
 

=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sdb1 into the MBRs of all disks (except USB without OS).
Additional repair would be performed: unhide-bootmenu-10s

=================== Final advice in case of suggested repair
Bitte stellen Sie sicher, dass ihr BIOS von sdb (1000GB) bootet!

=================== User settings
The settings chosen by the user will not act on the boot.

```

---

### Post by sudodus on 2015-10-14
Welcome to the Ubuntu Forums :-)

> I created a USB HD with an Ubuntu to use it at the work place that I do not need to touch the system installed by the company. This works perfectly for all computers. Just plugin and use Ubuntu. There is one exception. It did not work on all HP Elitbooks I tried so far. 

We have an HP Elitbook 8560P in my family. It was unwilling to boot via grub (which is the case with installed systems) until I found that ***it needs the boot flag***. But I see that you have already the boot flag in the boot partition.

> ```
=================== parted -l:
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End    Size    Type     File system  Flags
1      32.3kB  107MB  107MB   primary  ntfs         boot
2      107MB   128GB  128GB   primary  ntfs
3      128GB   212GB  84.0GB  primary  ntfs

Model: WD My Passport 0748 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End     Size   Type     File system  Flags
1      1049kB  859GB   859GB  primary  ext4         boot
2      859GB   1000GB  141GB  primary  fat32        lba
```

Observations:

- Operating System:  Ubuntu 14.04.3 LTS

- The recent kernel is 3.13.0-65 (the trusty kernel)

- The oldest kernel is 3.5.0-42 (the quantal kernel)

This indicates that the system has been 'updated/upgraded' and 'do-release-upgraded' many times. There may be some old cruft from previous versions, that creates confusion for the 'sensitive' HP boot sequence.

Another issue might be the graphics driver. In such a portable USB system there should be only the free drivers, no proprietary driver, but the HP Elitebooks might have an nvidia or amd graphics chip, that needs a proprietary driver. You could check if it works with the [boot option](https://help.ubuntu.com/community/BootOptions) nomodeset.

There might be similar problems with the wifi driver (depending on the wifi chip).

-o-

Maybe you can test a system based on a fresh installation of Lubuntu 14.04.3 in a pendrive or another USB HDD. Add the boot flag with gparted, if it is not there automatically.

---

### Post by Urs_Helfenstein on 2015-10-14
Hey sudodus

Thanks a lot for the fast reply, the welcoming, and your analysis.

You are right. I updated it many times and in Grub I can chose under options different kernels to boot. But no matter which one I chose, the result is always the same. 

The laptop I use has an Nvidea internal graphic card. But I do not think that the problem is due to a driver issue, because the error appears immediately after I chose some option to boot and is as far as I understand it an error of Grub before anything else is loaded.
On the HP Workstations we have (also with Nvidea graphic cards) it runs without any issue. But I am lucky to hear that it run on your Elitebook. But did you also use a external hard drive? I can imagine that it may be a difference if it is an external hard drive or an internal one. 

Cheers, 
Urs

---

### Post by sudodus on 2015-10-14
I have used USB pendrives and HDDs and SSDs connected via eSATA and USB (via an eSATA & USB box). I can double-check later with eSATA and USB - if you wish - because I may forget some details.

---

### Post by oldfred on 2015-10-14
It looks like Boot-Repair installed grub to sda, your Windows drive. You then need external drive attached to boot Windows. Better to reinstall a Windows boot loader to sda. You can use Boot-Repair's advanced mode or your Windows repair CD/flash drive and run fixMBR.

With very old BIOS and some BIOS/USB combinations system will not boot from beyond a certain point on drive. The old BIOS had a 137GB limit back when a 120GB drive was very large. 

But we have seen similar issues with very large drives like your 1TB drive as USB drive. Some kernel files may be anywhere in / so may be beyond the limit. Boot-Repair has suggested 100GB as point not to have any part of boot files past that point. Either a smaller / (root) partition or separate /boot may solve issue.
I normally suggest 25GB for / and then have /home or /mnt/data partition(s). 

If your / partition is not filled with data and you can shrink to less than 100GB you can quickly test if that is issue just by shrinking /. About half of users I have suggest this to found it works. And they then can reinstall or create /home and move it or create data partitions.

---

### Post by Urs_Helfenstein on 2015-10-14
Yes, that would be great. I am looking forward to hear from you. 

I tried it on a HP ElitBook 8740w and on a HP ZBook with the same result. Both have internally an SSD.

---

### Post by sudodus on 2015-10-14
> **sudodus said:**
> I have used USB pendrives and HDDs and SSDs connected via eSATA and USB (via an eSATA & USB box). I can double-check later with eSATA and USB - if you wish - because I may forget some details.

> **Urs_Helfenstein said:**
> Yes, that would be great. I am looking forward to hear from you. 

I tried it on a HP ElitBook 8740w and on a HP ZBook with the same result. Both have internally an SSD.

I have double-checked now: I know since before that it works to boot USB 2 and USB 3 pendrives via syslinux and via grub. I tested also that it works to boot Ubuntu 14.04.3 LTS 64-bit, installed system in an SSD, that sits in an Akasa (USB 3 & eSATA) enclosure. ***It boots and runs like it should via USB (2) as well as via eSATA.***

This computer is an HP Elitebook 8560p. I tested in BIOS mode today, but I have tested earlier in UEFI mode, and it boots in UEFI mode too, but it is an early (maybe experimental) UEFI version.

-o-

Are your [company's] Elitebooks running in BIOS mode or UEFI mode? If you want an installed system to work in BIOS mode as well as in UEFI mode, you must tweak the installation. A standard installed system is not likely to work in both modes. Furthermore, I know that new HP computers have non-standard UEFI systems, tweaked to make it hard to boot from anything else than Windows. I don't know if this applies to your [company's] Elitebooks. See this link and links from it for more details about booting from UEFI

[FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by Urs_Helfenstein on 2015-10-15
Thanks a lot for your efforts as well as your support. Both laptops run with a BIOS. Can it be that the BIOS restricted something that the error appears? I played around with boot repair and now the following error appears:

```
error: attempt to read or write outside of disk >>hd0<<.
unaligned pointer 0xabd57ff7
(aboarted)
```

In the boot repair tool is something mentioned with an ATA mode which should solve the "out-of-disk" error. I tried it but it did not help too. 

Can it be that the issue is caused by BIOS limitations because the partition is about 860 GB? Would be strange to me because the ZBook is just one week old and shows the same issues.


Thanks again!

---

### Post by sudodus on 2015-10-15
0. You can try to boot the Elitebooks with an Ubuntu boot DVD or pendrive (a ***regular live drive***).

1. You can ***install*** a test system (into a USB drive) within the first 100 GB in another computer and see if it works in the Elitebooks.

2. You can make a ***persistent live system*** in another computer (made with [mkusb](https://help.ubuntu.com/community/mkusb)) and see if it works in the Elitebooks.

---

### Post by Frogs Hair on 2015-10-15
My Elitebook boots Ubuntu fine from a live DVD , but I've not tried persistent or live USB. I had to remove the HP tools for Ubuntu installation though due to the factory partition setup, but even before that it would boot Ubuntu from DVD.

---

### Post by Urs_Helfenstein on 2015-10-16
My plan is as follows: I ordered a 2 TB USB hard drive to create a clone of the existing one (with Clonezilla). After this I will try to create a 1 GB partition at the beginning of the drive to load \boot into this place (should be possible with boot repair disk). After this I hope it will work. I keep you informed. 

With live DVD's and USB Sticks it works on this Elitebooks too. But this systems are not 860 GB and not USB hard drives. I think we isolate the problem more and more and came closer to the cause. 
Thanks to each one of you for your help!

---

### Post by oldfred on 2015-10-16
I normally suggest separate / (root) and /home then rather than /boot. You can allocate 20 or 25GB to / and usually have lots of room in /, unless installing lots of large games.

I also like to recommend gpt if drive is only going to be Ubuntu and if an external drive it will not be Windows.
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

But if gpt partitioned you have to have either an ESP - efi system partition for UEFI boot or a bios_grub partition for BIOS boot. I actually have both on all drives, even my larger flash drives so I can convert from older BIOS to newer UEFI without totally having to reformat.

       
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by Urs_Helfenstein on 2015-10-21
Hi Everybody, 

I am back. I got the 2 TB USB hard drive and created 3 partitions. A 1 GB EXT4 at the beginning as a boot partition, a 1.8 TB ECT4 partition for the Linux system, and the rest as a NTFS partition to be used as shared memory between Windows and Linux.
With Clonezilla I cloned the existing system to the 1.8 TB partition. I started with the boot-repair-live system and used the option to create a separate /boot partition (into sdg1) and copy grub into sdg. This ends with an error and I got the following link of boot repair:

[http://paste.ubuntu.com/12884079/](http://paste.ubuntu.com/12884079/)

When I restarted, Grub only showed the option to boot Windows which is installed on the internal SSD hard drive of the workstation. I started boot repair again and let the standard boot repair procedure run. It told that boot is repaired now and showed the following link:

[http://paste.ubuntu.com/12884098/](http://paste.ubuntu.com/12884098/)

After this I was able to boot Ubuntu again on the workstation. But when I go to the HP Elitebooks and Zbook I have still the same error that it try to read or write outside hd0.

My question:
 - Does Grub boot from the small 1 GB boot partition or still from the 1800 GB partition
 - Why ends the separating of /boot with an error?

If Grub now try to boot from the 1 GB partition and it still fails, it need to be another cause than a too big partition for the BIOS.
If the separation process really fails and the system now still boot from the 1800 GB partition. Is it possible to help that the separation process did not fail? 

Or should I  pursue the solution proposed by oldfred to separate /root and /home. Is this possible without a new installation? I have a lot of tools installed and compiled and therefore I try to avoid a new installation. Is there anywhere an instruction how to replace /home to another partition?

Thanks a lot to all of you!

---

### Post by oldfred on 2015-10-21
This cannot be correct, one is a partition list and the other the blkid to list UUIDs.

 /dev/sdg2           1,955,840 3,517,581,311 3,515,625,472   7 NTFS / exFAT / HPFS
/dev/sdg2        82acfc50-9cfa-4557-83b8-c2f1201c4522   ext4       sdh1

Partition cannot be both NTFS & ext4, and your Linux partition must be ext4.
So use Disks on live installer and change (do not format) partition sdg2 from NTFS to ext4.

Sectors do not look like they extend beyond end of drive.
      [http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk](http://gparted.org/h2-fix-msdos-pt.php#partition-outside-disk)

What partition tool did you use to format external drive. It starts at sector 63 which Windows stopped using with Windows 7 and Linux about a year after Windows 7 came out. All new partition tools start at sector 2048 for compatibility with newer 4K drives or SSDs. Your drive is still an 512 sector drive so should be ok.

 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[URL="https://help.ubuntu.com/community/Partitioning/Home/Moving"]https://help.ubuntu.com/community/Partitioning/Home/Moving
[/URL]

---

### Post by Urs_Helfenstein on 2015-10-29
Okay Folks, 

It works now on the HP EliteBooks too. The problem was really that the partition containing /boot was to large. 

I created at the beginning a partition of 80 GB for "/" and a 1.7 TB partition for "/home". A swap partition I did not install because the systems we use have all 12 GB RAM or more. To create the partitions and resize them I used the live system "Boot Repair Disk". After partitioning and resizing I started the boot repair procedure of this live system and than I was able to boot even from the HP laptops. 

So thanks a lot to every one to contribute to solve this long lasting and annoying problem. And once again it was not an Ubuntu problem. I like this system as well as the community more and more. Thanks!

Urs

---

