---
title: "Can't restore MBR or Grub? Win7 + Ubuntu Studio Dual Boot"
date: 2015-05-03
forum: General Help
---

### Post by billayk on 2015-05-03
Hi everyone,

Having an issue with my desktop which currently has both win 7 and Ubuntu Studio 14.04.2 installed, both 32 bit. I'm unable to boot either operating system, the only thing that comes up after start up checks is "boot from cd" and then nothing happens. 

This began after I attempted to switch from the KX studio distro back to Ubuntu Studio which I had run previously. I already had win 7 and KX studio booting fine from grub but was unable to get my computer to boot a live USB of U-studio. I wanted to keep the win 7 installation, delete KX studio and install Ubuntu Studio in it's place.

I got frustrated with not being able to boot from a USB (which I had done previously with the aid of a boot cd with PloP boot manager) and decided to delete all of the KX studio partitions from the win 7 partition manager. I guess I must have ruined something pretty well because now even after installing Ubuntu Studio to the freed partitions I can not boot either operating system. 

I have used the boot-repair program on a live usb to restore both Grub and the MBR, both of which had no effect. I still get the "insert boot cd" output on start up. 

Included below is the output of boot-repair. Please let me know if I should provide other info. Thanks!

```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20140113
    Boot sector info:  Syslinux looks at sector 1377344 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /ldlinux.sys

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.2 LTS 
    Boot files:        /etc/fstab

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/i386-pc/core.img

sdb9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7/2008: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    15,633,407    15,633,345   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2    *        206,848   488,386,559   488,179,712   7 NTFS / exFAT / HPFS
/dev/sdb3         488,388,606   976,771,071   488,382,466   5 Extended
/dev/sdb5         970,483,712   976,771,071     6,287,360  82 Linux swap / Solaris
/dev/sdb6         488,388,608   527,448,063    39,059,456  83 Linux
/dev/sdb7         527,450,112   918,073,343   390,623,232  83 Linux
/dev/sdb8         918,075,392   919,050,239       974,848  83 Linux
/dev/sdb9         919,052,288   939,814,911    20,762,624  83 Linux
/dev/sdb10        939,816,960   970,477,567    30,660,608  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63    58,593,812    58,593,750   c W95 FAT32 (LBA)
/dev/sdc2    *     58,593,813 1,465,144,064 1,406,550,252   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1C0D-2751                              vfat       MULTIBOOT
/dev/sdb1        081CAC5C1CAC4712                       ntfs       System Reserved
/dev/sdb10       2fcaec50-e264-4ac1-a9ec-03c29811ed3b   ext4       
/dev/sdb2        46DCD546DCD530C3                       ntfs       
/dev/sdb5        3217f142-adb4-4383-8d6d-1974cb2cb78e   swap       
/dev/sdb6        dd7ff55f-22ad-4b91-bb49-052b8dff2769   ext4       
/dev/sdb7        b10edbe0-b7ae-4e54-899e-54ec449a488c   ext4       
/dev/sdb8        79a55648-c4eb-45b9-b6ee-6e3023cd512e   ext4       
/dev/sdb9        c03b9f59-6321-477e-8125-226e5bce0366   ext4       
/dev/sdc1        BE16-8638                              vfat       EXCHANGE
/dev/sdc2        14621D6E621D5638                       ntfs       LaCie
/dev/sr0                                                iso9660    Plop Boot Manager 5.0.15
/dev/zram0       2eebec05-f7fc-4250-a99b-005095368b21   swap       
/dev/zram1       addc8564-1633-470e-9cf0-7d6fa6285f5c   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 May  3 19:50 ata-Hitachi_HDT721075SLA380_STA401MG03HGRA -> ../../sdc
lrwxrwxrwx 1 root root 10 May  3 19:49 ata-Hitachi_HDT721075SLA380_STA401MG03HGRA-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 May  3 19:50 ata-Hitachi_HDT721075SLA380_STA401MG03HGRA-part2 -> ../../sdc2
lrwxrwxrwx 1 root root  9 May  3 19:49 ata-LITE-ON_DVDRW_LDW-851S_2004031600004538 -> ../../sr0
lrwxrwxrwx 1 root root  9 May  3 19:50 ata-WDC_WD5000AAKX-001CA0_WD-WCAYUH725109 -> ../../sdb
lrwxrwxrwx 1 root root 10 May  3 19:50 ata-WDC_WD5000AAKX-001CA0_WD-WCAYUH725109-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 11 May  3 19:49 ata-WDC_WD5000AAKX-001CA0_WD-WCAYUH725109-part10 -> ../../sdb10
lrwxrwxrwx 1 root root 10 May  3 19:50 ata-WDC_WD5000AAKX-001CA0_WD-WCAYUH725109-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 May  3 19:50 ata-WDC_WD5000AAKX-001CA0_WD-WCAYUH725109-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 May  3 19:49 ata-WDC_WD5000AAKX-001CA0_WD-WCAYUH725109-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 May  3 19:49 ata-WDC_WD5000AAKX-001CA0_WD-WCAYUH725109-part6 -> ../../sdb6
lrwxrwxrwx 1 root root 10 May  3 19:49 ata-WDC_WD5000AAKX-001CA0_WD-WCAYUH725109-part7 -> ../../sdb7
lrwxrwxrwx 1 root root 10 May  3 19:49 ata-WDC_WD5000AAKX-001CA0_WD-WCAYUH725109-part8 -> ../../sdb8
lrwxrwxrwx 1 root root 10 May  3 19:49 ata-WDC_WD5000AAKX-001CA0_WD-WCAYUH725109-part9 -> ../../sdb9
lrwxrwxrwx 1 root root  9 May  3 19:50 usb-SanDisk_Cruzer_Switch_4C532000011015121533-0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 May  3 19:49 usb-SanDisk_Cruzer_Switch_4C532000011015121533-0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 May  3 19:50 wwn-0x5000cca348c19734 -> ../../sdc
lrwxrwxrwx 1 root root 10 May  3 19:49 wwn-0x5000cca348c19734-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 May  3 19:50 wwn-0x5000cca348c19734-part2 -> ../../sdc2
lrwxrwxrwx 1 root root  9 May  3 19:50 wwn-0x50014ee1ae69648c -> ../../sdb
lrwxrwxrwx 1 root root 10 May  3 19:50 wwn-0x50014ee1ae69648c-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 11 May  3 19:49 wwn-0x50014ee1ae69648c-part10 -> ../../sdb10
lrwxrwxrwx 1 root root 10 May  3 19:50 wwn-0x50014ee1ae69648c-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 May  3 19:50 wwn-0x50014ee1ae69648c-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 May  3 19:49 wwn-0x50014ee1ae69648c-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 May  3 19:49 wwn-0x50014ee1ae69648c-part6 -> ../../sdb6
lrwxrwxrwx 1 root root 10 May  3 19:49 wwn-0x50014ee1ae69648c-part7 -> ../../sdb7
lrwxrwxrwx 1 root root 10 May  3 19:49 wwn-0x50014ee1ae69648c-part8 -> ../../sdb8
lrwxrwxrwx 1 root root 10 May  3 19:49 wwn-0x50014ee1ae69648c-part9 -> ../../sdb9

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sr0         /media/lubuntu/Plop Boot Manager 5.0.15 iso9660    (ro,nosuid,nodev,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks2)


=========================== sda1/boot/grub/grub.cfg: ===========================

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

============================== sda1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^32bit session
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^32bit session (failsafe)
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper  noapic noapm nodma nomce nolapic nomodeset nosmp vga=normal --

label ubnentry3
menu label Boot-Repair-Disk session
kernel /ubnkern
append initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash --

--------------------------------------------------------------------------------

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=dd7ff55f-22ad-4b91-bb49-052b8dff2769 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda8 during installation
UUID=79a55648-c4eb-45b9-b6ee-6e3023cd512e /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=b10edbe0-b7ae-4e54-899e-54ec449a488c /home           ext4    defaults        0       2
# /tmp was on /dev/sda10 during installation
UUID=2fcaec50-e264-4ac1-a9ec-03c29811ed3b /tmp            ext4    defaults        0       2
# /var was on /dev/sda9 during installation
UUID=c03b9f59-6321-477e-8125-226e5bce0366 /var            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=3217f142-adb4-4383-8d6d-1974cb2cb78e none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

============================= sdb8/grub/grub.cfg: ==============================

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
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos6 --hint-efi=hd0,msdos6 --hint-baremetal=ahci0,msdos6  dd7ff55f-22ad-4b91-bb49-052b8dff2769
else
  search --no-floppy --fs-uuid --set=root dd7ff55f-22ad-4b91-bb49-052b8dff2769
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_AU
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/09_lowlatency ###
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
menuentry 'Ubuntu (lowlatency)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-dd7ff55f-22ad-4b91-bb49-052b8dff2769' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  79a55648-c4eb-45b9-b6ee-6e3023cd512e
    else
      search --no-floppy --fs-uuid --set=root 79a55648-c4eb-45b9-b6ee-6e3023cd512e
    fi
    linux    /vmlinuz-3.16.0-30-lowlatency root=UUID=dd7ff55f-22ad-4b91-bb49-052b8dff2769 ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.16.0-30-lowlatency
}

### END /etc/grub.d/09_lowlatency ###

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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-dd7ff55f-22ad-4b91-bb49-052b8dff2769' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  79a55648-c4eb-45b9-b6ee-6e3023cd512e
    else
      search --no-floppy --fs-uuid --set=root 79a55648-c4eb-45b9-b6ee-6e3023cd512e
    fi
    linux    /vmlinuz-3.16.0-30-lowlatency root=UUID=dd7ff55f-22ad-4b91-bb49-052b8dff2769 ro  quiet splash $vt_handoff
    initrd    /initrd.img-3.16.0-30-lowlatency
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-dd7ff55f-22ad-4b91-bb49-052b8dff2769' {
    menuentry 'Ubuntu, with Linux 3.16.0-30-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-lowlatency-advanced-dd7ff55f-22ad-4b91-bb49-052b8dff2769' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  79a55648-c4eb-45b9-b6ee-6e3023cd512e
        else
          search --no-floppy --fs-uuid --set=root 79a55648-c4eb-45b9-b6ee-6e3023cd512e
        fi
        echo    'Loading Linux 3.16.0-30-lowlatency ...'
        linux    /vmlinuz-3.16.0-30-lowlatency root=UUID=dd7ff55f-22ad-4b91-bb49-052b8dff2769 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.16.0-30-lowlatency
    }
    menuentry 'Ubuntu, with Linux 3.16.0-30-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-30-lowlatency-recovery-dd7ff55f-22ad-4b91-bb49-052b8dff2769' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos8'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  79a55648-c4eb-45b9-b6ee-6e3023cd512e
        else
          search --no-floppy --fs-uuid --set=root 79a55648-c4eb-45b9-b6ee-6e3023cd512e
        fi
        echo    'Loading Linux 3.16.0-30-lowlatency ...'
        linux    /vmlinuz-3.16.0-30-lowlatency root=UUID=dd7ff55f-22ad-4b91-bb49-052b8dff2769 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.16.0-30-lowlatency
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  79a55648-c4eb-45b9-b6ee-6e3023cd512e
    else
      search --no-floppy --fs-uuid --set=root 79a55648-c4eb-45b9-b6ee-6e3023cd512e
    fi
    knetbsd    /memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos8'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  79a55648-c4eb-45b9-b6ee-6e3023cd512e
    else
      search --no-floppy --fs-uuid --set=root 79a55648-c4eb-45b9-b6ee-6e3023cd512e
    fi
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-081CAC5C1CAC4712' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  081CAC5C1CAC4712
    else
      search --no-floppy --fs-uuid --set=root 081CAC5C1CAC4712
    fi
    parttool ${root} hidden-
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-46DCD546DCD530C3' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  46DCD546DCD530C3
    else
      search --no-floppy --fs-uuid --set=root 46DCD546DCD530C3
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

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/1998/mounts) leaked on lvs invocation. Parent PID 14898: bash
File descriptor 63 (pipe:[32274]) leaked on lvs invocation. Parent PID 14898: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-05-03__19h50 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/1998/mounts) leaked on lvs invocation. Parent PID 4483: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 32bit 29nov2014, trusty, Ubuntu, i686)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper quiet splash -- BOOT_IMAGE=/ubnkern

=================== os-prober:
/dev/sdb1:Windows 7 (loader):Windows:chain
/dev/sdb2:Windows 7 (loader):Windows1:chain
/dev/sdb6:Ubuntu 14.04.2 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="MULTIBOOT" UUID="1C0D-2751" TYPE="vfat"
/dev/sr0: LABEL="Plop Boot Manager 5.0.15" TYPE="iso9660"
/dev/sdb1: LABEL="System Reserved" UUID="081CAC5C1CAC4712" TYPE="ntfs"
/dev/sdb2: UUID="46DCD546DCD530C3" TYPE="ntfs"
/dev/sdb5: UUID="3217f142-adb4-4383-8d6d-1974cb2cb78e" TYPE="swap"
/dev/sdb6: UUID="dd7ff55f-22ad-4b91-bb49-052b8dff2769" TYPE="ext4"
/dev/sdb7: UUID="b10edbe0-b7ae-4e54-899e-54ec449a488c" TYPE="ext4"
/dev/sdb8: UUID="79a55648-c4eb-45b9-b6ee-6e3023cd512e" TYPE="ext4"
/dev/sdb9: UUID="c03b9f59-6321-477e-8125-226e5bce0366" TYPE="ext4"
/dev/sdb10: UUID="2fcaec50-e264-4ac1-a9ec-03c29811ed3b" TYPE="ext4"
/dev/sdc1: LABEL="EXCHANGE" UUID="BE16-8638" TYPE="vfat"
/dev/sdc2: LABEL="LaCie" UUID="14621D6E621D5638" TYPE="ntfs"
/dev/zram0: UUID="2eebec05-f7fc-4250-a99b-005095368b21" TYPE="swap"
/dev/zram1: UUID="addc8564-1633-470e-9cf0-7d6fa6285f5c" TYPE="swap"


1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== sdb6/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Feb 18 20:14 grub.d
total 88
-rwxr-xr-x 1 root root  9424 May 15  2014 00_header
-rwxr-xr-x 1 root root  6058 May  8  2014 05_debian_theme
-rwxr-xr-x 1 root root  9921 Apr  9  2014 09_lowlatency
-rwxr-xr-x 1 root root 11608 May 15  2014 10_linux
-rwxr-xr-x 1 root root 10412 May 15  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 May 15  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15  2014 40_custom
-rwxr-xr-x 1 root root   216 May 15  2014 41_custom
-rw-r--r-- 1 root root   483 May 15  2014 README




=================== sdb6/etc/default/grub :

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



/boot detected in the fstab of sdb6: UUID=79a55648-c4eb-45b9-b6ee-6e3023cd512e  (sdb8)
=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb1.
sdb2    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb2.
sdb6    : sdb,    not-sepboot,    no-grubenv    grub2,    grub-pc ,    update-grub,    32,    no-boot,    is-os,    not--efi--part,    fstab-has-goodBOOT,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb6.
sdb7    : sdb,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb7.
sdb8    : sdb,    is-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb8.
sdb9    : sdb,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb9.
sdb10    : sdb,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb10.
sdc1    : sdc,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdc1.
sdc2    : sdc,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdc2.

sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdc    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    63 sectors * 512 bytes


=================== parted -l:

Model: SanDisk Cruzer Switch (scsi)
Disk /dev/sda: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  8004MB  8004MB  primary  fat32        boot, lba


Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  106MB  105MB   primary   ntfs            boot
2      106MB   250GB  250GB   primary   ntfs
3      250GB   500GB  250GB   extended
6      250GB   270GB  20.0GB  logical   ext4
7      270GB   470GB  200GB   logical   ext4
8      470GB   471GB  499MB   logical   ext4
9      471GB   481GB  10.6GB  logical   ext4
10      481GB   497GB  15.7GB  logical   ext4
5      497GB   500GB  3219MB  logical   linux-swap(v1)


Model: ATA Hitachi HDT72107 (scsi)
Disk /dev/sdc: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  30.0GB  30.0GB  primary  fat32        lba
2      30.0GB  750GB   720GB   primary  ntfs         boot



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:8004MB:scsi:512:512:msdos:SanDisk Cruzer Switch;
1:32.3kB:8004MB:8004MB:fat32::boot, lba;

BYT;
/dev/sdb:500GB:scsi:512:512:msdos:ATA WDC WD5000AAKX-0;
1:1049kB:106MB:105MB:ntfs::boot;
2:106MB:250GB:250GB:ntfs::;
3:250GB:500GB:250GB:::;
6:250GB:270GB:20.0GB:ext4::;
7:270GB:470GB:200GB:ext4::;
8:470GB:471GB:499MB:ext4::;
9:471GB:481GB:10.6GB:ext4::;
10:481GB:497GB:15.7GB:ext4::;
5:497GB:500GB:3219MB:linux-swap(v1)::;

BYT;
/dev/sdc:750GB:scsi:512:512:msdos:ATA Hitachi HDT72107;
1:32.3kB:30.0GB:30.0GB:fat32::lba;
2:30.0GB:750GB:720GB:ntfs::boot;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sda1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
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
/dev/sr0 on /media/lubuntu/Plop Boot Manager 5.0.15 type iso9660 (ro,nosuid,nodev,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks2)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb6 on /mnt/boot-sav/sdb6 type ext4 (rw)
/dev/sdb7 on /mnt/boot-sav/sdb7 type ext4 (rw)
/dev/sdb8 on /mnt/boot-sav/sdb8 type ext4 (rw)
/dev/sdb9 on /mnt/boot-sav/sdb9 type ext4 (rw)
/dev/sdb10 on /mnt/boot-sav/sdb10 type ext4 (rw)
/dev/sdc1 on /mnt/boot-sav/sdc1 type vfat (rw)
/dev/sdc2 on /mnt/boot-sav/sdc2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/fd0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb10 sdb2 sdb3 sdb5 sdb6 sdb7 sdb8 sdb9 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 sdc2 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu_dma_latency cuse disk dri ecryptfs fb0 fd fd0 full fuse fw0 hidraw0 hidraw1 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdb10 sdb2 sdb3 sdb5 sdb6 sdb7 sdb8 sdb9 sdc sdc1 sdc2 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 f0 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 1f 03 00 00 00 00 00  |................|
00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|
00000040  f6 00 00 00 01 00 00 00  12 47 ac 1c 5c ac 1c 08  |.........G.....|
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

=================== hexdump -n512 -C /dev/sdb2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 f0 00 00 28 03 00  |........?....(..|
00000020  00 00 00 00 80 00 80 00  ff 07 19 1d 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  c3 30 d5 dc 46 d5 dc 46  |.........0..F..F|
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

=================== hexdump -n512 -C /dev/sdc1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 20 4c 10  |.X.MSDOS5.0.. L.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  d6 11 7e 03 da 37 00 00  00 00 00 00 02 00 00 00  |..~..7..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 38 86 16 be 4e  4f 20 4e 41 4d 45 20 20  |..)8...NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

=================== hexdump -n512 -C /dev/sdc2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 15 12 7e 03  |........?.....~.|
00000020  00 00 00 00 80 00 80 00  eb 40 d6 53 00 00 00 00  |.........@.S....|
00000030  00 00 0c 00 00 00 00 00  0e 64 3d 05 00 00 00 00  |.........d=.....|
00000040  f6 00 00 00 01 00 00 00  38 56 1d 62 6e 1d 62 14  |........8V.bn.b.|
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

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.5G  6.2M  1.5G   1% /
udev           devtmpfs   1.5G   12K  1.5G   1% /dev
tmpfs          tmpfs      303M  1.2M  302M   1% /run
/dev/sda1      vfat       7.5G  643M  6.8G   9% /cdrom
/dev/loop0     squashfs   543M  543M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.5G  8.0K  1.5G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.5G     0  1.5G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sr0       iso9660    544K  544K     0 100% /media/lubuntu/Plop Boot Manager 5.0.15
/dev/sdb1      fuseblk    100M   25M   76M  25% /mnt/boot-sav/sdb1
/dev/sdb2      fuseblk    233G   96G  138G  42% /mnt/boot-sav/sdb2
/dev/sdb6      ext4        19G  5.3G   12G  31% /mnt/boot-sav/sdb6
/dev/sdb7      ext4       184G   60M  174G   1% /mnt/boot-sav/sdb7
/dev/sdb8      ext4       453M   39M  387M  10% /mnt/boot-sav/sdb8
/dev/sdb9      ext4       9.7G  485M  8.7G   6% /mnt/boot-sav/sdb9
/dev/sdb10     ext4        15G   37M   14G   1% /mnt/boot-sav/sdb10
/dev/sdc1      vfat        28G  152M   28G   1% /mnt/boot-sav/sdc1
/dev/sdc2      fuseblk    671G  235G  436G  36% /mnt/boot-sav/sdc2

=================== fdisk -l:

Disk /dev/sda: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007ee0f

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    15633407     7816672+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf9992496

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   488386559   244089856    7  HPFS/NTFS/exFAT
/dev/sdb3       488388606   976771071   244191233    5  Extended
/dev/sdb5       970483712   976771071     3143680   82  Linux swap / Solaris
/dev/sdb6       488388608   527448063    19529728   83  Linux
/dev/sdb7       527450112   918073343   195311616   83  Linux
/dev/sdb8       918075392   919050239      487424   83  Linux
/dev/sdb9       919052288   939814911    10381312   83  Linux
/dev/sdb10      939816960   970477567    15330304   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000de2e0

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    58593812    29296875    c  W95 FAT32 (LBA)
/dev/sdc2   *    58593813  1465144064   703275126    7  HPFS/NTFS/exFAT


/boot detected. Please check the options.


=================== Default settings of Boot Repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sdb6 into the MBRs of all disks (except USB without OS), using the following options:        sdb8/boot,
Additional repair would be performed: unhide-bootmenu-10s


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sdb (500GB) disk!


=================== User settings
The settings chosen by the user will restore the [(generic mbr)] MBR in sdb, and make it boot on sdb2.
Additional repair will be performed: unhide-bootmenu-10s


Will restore the MBR_TO_RESTORE : sdb (generic mbr) into sdb
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdb
0+1 records in
0+1 records out
parted /dev/sdb set 2 boot on

                                                                          
Information: You may need to update /etc/fstab.


```

---

### Post by Mark Phelps on 2015-05-03
If it were my machine, I would focus on getting Win7 running again -- and once that was done, repairing the Linux distro boot.

Unfortunately, it appears you ran the boot-repair default that installed GRUB to all the drives -- which, when installed to a Windows drive, can confuse the Windows boot loader, preventing it from booting.

To repair Win7, you need install media or a Win7 Repair CD.  If you don't have install media, then you will need to go to the site in the link, purchase the Win7 repair ISO, download it to a working PC -- and burn a CD from that.  Then, boot from that CD and run Startup Repair three times, that's right -- three times.  Once that is done, you should then be able to reboot into Win7. Link: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

---

### Post by oldfred on 2015-05-03
Your system seems to be one of those that has promoted flash drive to sda or first drive. When you plugged drives into motherboard did you skip SATA1? If flash drive is plugged in or not changes drive order then which can add issues.

Your Windows has the standard 100MB boot partition with boot files, but boot flag is on second drive. Boot-Repair may have copied bootmgr & BCD to that partition so from BIOS you should be able to boot Windows. You have a Windows boot loader in that second drive. 

You have extra system partitions, so Boot-Repair cannot fix your system. It works with standard installs with just / & swap or those with a /boot. Whether you have /home as a separate partition does not matter for boot issue repairs. But Boot-Repair does not mount other system partitions assuming the are in / (root), it only checks for /boot as a possibility.

So the only way you can repair your system is full chroot or a reinstall.
If your system is so old as to require 32bit, then you may also have a BIOS that needs boot files near beginning of drive. Some old BIOS will only boot using boot files within the first 137GB of a drive. So either all of / (root) or all of a /boot partition must be inside the first 137GB of a drive.

Probably better with two drives to have Windows on one drive and Ubuntu on the other drive. And not have separate system partitions. I typically suggest / (root) of 25GB and then rest of drive as /home, /mnt/data or shared NTFS data partition(s).

Move boot flag back to sda1 or sdb1 whichever system is seeing Windows 100MB boot partition as. And then from BIOS see if you can boot Windows with either flash plugged in or not. Windows used to be vary particular about drive order, but I thought Windows 7 started to be less so.

---

