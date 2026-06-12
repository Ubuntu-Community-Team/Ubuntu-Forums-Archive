---
title: "Computer Hangs At: enable remaining boot-time encrypted block devices"
date: 2016-03-25
forum: General Help
---

### Post by victor-hatley on 2016-03-25
Hello, I've been using Linux Mint 17.2 Cinnamon for several months now and have been having a recurring problem, fixable so far, but annoying none the less...


I'm running an older Toshiba C655, 3 GB Ram, Dual core AMD E-300, AMD Radeon HD 6310, 150 GB HDD, Adding in a Logitech USB Keyboard and Trackman wheel USB Mouse.


Running Linux Mint 17.2 Cinnamon:D in a dual boot situation with Windows 7 Home Premium:(.


Here's the problem:


When booted into Mint, while using either Firefox or Chrome, the computer will run out of memory, (using multi-core System Monitor to determine the RAM and CPU usage,) then lock up. When using ctrl+alt+backspace, F1, etc. nothing happens. I have to hard shut down the computer, (power button 10 secs,) and when the computer reboots it always hangs at:


Starting enable remaining boot-time encrypted block devices...[OK]


The GRUB menu is still there, and if I select the Windows 7 install it boots fine, just not the Mint 17. (My preferred OS.)


While attempting to figure this problem out, I ran across the program "boot-repair" for linux, and created a persistent USB Install disk, and installed the boot-repair on it. Then used that USB disk and boot-repair program to repair the Mint install on the HDD...and it worked perfectly!


I have disabled all the add-ons and extensions, added an extension to reduce the amount of RAM the browsers took up, (The Great Tab Suspender,) and while controlling the amount of RAM helped, it didn't solve it. Heres a list of the Chrome extensions I have and their status:


Autoscroll (Enabled)
Flashcontrol (E)
Google Docs Offline (Disabled)
LastPass (E)
OneTab (D)
SEO And Website Analysis (D)
TeamViewer (D)
The Great Suspender (E)


I mainly use Chrome, but Firefox has the bare bones (extensions) and does it too.


The problem is this:


I can recreate the issue, and repair the issue, but I can't for the life of me figure out exactly what boot-repair fixed to get Mint back Up-N-Running. When I run the program, I always select to fix the systemfiles, and have created the report and even allowed the program to upload something to the PasteBin locker, but I would really like to find out what boot-repair is doing so I can attempt to take measures to prevent the whole thing from happening...it's really annoying, even if I can get everything back running.

I saved the Boot-info Summary in a place I could find it, but can't figure out how to find the supposed PastBin file that was supposed to be uploaded. Here's the Bootinfo Summary:

```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]




============================= Boot Info Summary: ===============================


 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub.


sda1: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  SYSLINUX 4.05 20140113
    Boot sector info:  Syslinux looks at sector 794624 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the / directory.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /extlinux.conf 
                       /ldlinux.sys


sda2: __________________________________________________________________________


    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 17.2 Rafaela 
    Boot files:        /etc/fstab


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


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 17.2 Rafaela 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf 
                       /boot/grub/i386-pc/core.img


sdb4: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 


sdb5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        


sdb6: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb7: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 32.0 GB, 32015679488 bytes
64 heads, 32 sectors/track, 30532 cylinders, total 62530624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048    10,242,047    10,240,000  83 Linux
/dev/sda2          10,242,048    62,529,535    52,287,488  83 Linux




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sdb2             206,848   102,402,047   102,195,200   7 NTFS / exFAT / HPFS
/dev/sdb3         102,402,048   131,698,687    29,296,640  83 Linux
/dev/sdb4         131,700,734   312,580,095   180,879,362   5 Extended
/dev/sdb5         131,700,736   200,058,879    68,358,144  83 Linux
/dev/sdb6         297,713,664   312,580,095    14,866,432  82 Linux swap / Solaris
/dev/sdb7         200,060,928   296,726,943    96,666,016   7 NTFS / exFAT / HPFS




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        7eccbb70-fcba-44bd-aee7-60b4bf824617   ext4       Live Persistent
/dev/sda2        c75f3982-352e-4dc3-920a-72d684695ee1   ext2       casper-rw
/dev/sdb1        B4366F50366F12A2                       ntfs       System Reserved
/dev/sdb2        9CA07AB2A07A930E                       ntfs       
/dev/sdb3        6e513f3a-e5c9-477a-aebd-5b494aa7da29   ext4       
/dev/sdb5        fb6b915e-a013-4be6-9a83-34ada4e1199a   ext4       
/dev/sdb6        fced4701-d760-4828-86cf-016449f05a87   swap       
/dev/sdb7        6E06CD3138E90FC4                       ntfs       Storage


========================= "ls -l /dev/disk/by-id" output: ======================


total 0
lrwxrwxrwx 1 root root  9 Mar 20 13:42 ata-TSSTcorp_CDDVDW_TS-L633C_R7256GLZ726474 -> ../../sr0
lrwxrwxrwx 1 root root  9 Mar 20 18:43 ata-WDC_WD1600BEVT-22ZCT0_WD-WXL0E89T0508 -> ../../sdb
lrwxrwxrwx 1 root root 10 Mar 20 18:43 ata-WDC_WD1600BEVT-22ZCT0_WD-WXL0E89T0508-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Mar 20 18:43 ata-WDC_WD1600BEVT-22ZCT0_WD-WXL0E89T0508-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Mar 20 13:42 ata-WDC_WD1600BEVT-22ZCT0_WD-WXL0E89T0508-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Mar 20 13:42 ata-WDC_WD1600BEVT-22ZCT0_WD-WXL0E89T0508-part4 -> ../../sdb4
lrwxrwxrwx 1 root root 10 Mar 20 13:42 ata-WDC_WD1600BEVT-22ZCT0_WD-WXL0E89T0508-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Mar 20 13:42 ata-WDC_WD1600BEVT-22ZCT0_WD-WXL0E89T0508-part6 -> ../../sdb6
lrwxrwxrwx 1 root root 10 Mar 20 18:43 ata-WDC_WD1600BEVT-22ZCT0_WD-WXL0E89T0508-part7 -> ../../sdb7
lrwxrwxrwx 1 root root  9 Mar 20 18:43 usb-SanDisk_Cruzer_Glide_4C530699910228121171-0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 Mar 20 13:42 usb-SanDisk_Cruzer_Glide_4C530699910228121171-0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Mar 20 13:42 usb-SanDisk_Cruzer_Glide_4C530699910228121171-0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Mar 20 18:43 wwn-0x50014ee05712c07d -> ../../sdb
lrwxrwxrwx 1 root root 10 Mar 20 18:43 wwn-0x50014ee05712c07d-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Mar 20 18:43 wwn-0x50014ee05712c07d-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Mar 20 13:42 wwn-0x50014ee05712c07d-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Mar 20 13:42 wwn-0x50014ee05712c07d-part4 -> ../../sdb4
lrwxrwxrwx 1 root root 10 Mar 20 13:42 wwn-0x50014ee05712c07d-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Mar 20 13:42 wwn-0x50014ee05712c07d-part6 -> ../../sdb6
lrwxrwxrwx 1 root root 10 Mar 20 18:43 wwn-0x50014ee05712c07d-part7 -> ../../sdb7


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   ext4       (ro,noatime,data=ordered)
/dev/sda2        /media/mint/casper-rw    ext2       (rw,nosuid,nodev,uhelper=udisks2)




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


menuentry "Start Linux Mint 17.2 Cinnamon 64-bit" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/linuxmint.seed boot=casper iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Start Linux Mint 17.2 Cinnamon 64-bit (compatibility mode)" {
    linux    /casper/vmlinuz  file=/cdrom/preseed/linuxmint.seed boot=casper xforcevesa iso-scan/filename=${iso_path} ramdisk_size=1048576 root=/dev/ram rw noapic noacpi nosplash irqpoll --
    initrd    /casper/initrd.lz
}
menuentry "Check the integrity of the medium" {
    linux    /casper/vmlinuz  boot=casper integrity-check iso-scan/filename=${iso_path} quiet splash --
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
append initrd=/ubninit file=/cdrom/preseed/linuxmint.seed boot=casper quiet splash -- persistent


label ubnentry0
menu label Start Linux Mint
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/linuxmint.seed boot=casper  quiet splash -- persistent


label ubnentry1
menu label Start in compatibility mode
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/linuxmint.seed boot=casper xforcevesa nomodeset b43.blacklist=yes  ramdisk_size=1048576 root=/dev/ram rw noapic noacpi nosplash irqpoll -- persistent


label ubnentry2
menu label Integrity check
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- persistent


label ubnentry3
menu label Memory test
kernel /casper/memtest
append initrd=/ubninit  persistent


label ubnentry4
menu label Boot from local drive
kernel /ubnkern
append initrd=/ubninit hd0 persistent


label ubnentry5
menu label Start Linux Mint 17.2 Cinnamon 64-bit
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/linuxmint.seed boot=casper iso-scan/filename=${iso_path} quiet splash -- persistent


label ubnentry6
menu label Start Linux Mint 17.2 Cinnamon 64-bit (compatibility mode)
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/linuxmint.seed boot=casper xforcevesa iso-scan/filename=${iso_path} ramdisk_size=1048576 root=/dev/ram rw noapic noacpi nosplash irqpoll -- persistent


label ubnentry7
menu label Check the integrity of the medium
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check iso-scan/filename=${iso_path} quiet splash -- persistent


--------------------------------------------------------------------------------


============================= sda1/extlinux.conf: ==============================


--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100


label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/linuxmint.seed boot=casper quiet splash -- persistent


label ubnentry0
menu label Start Linux Mint
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/linuxmint.seed boot=casper  quiet splash -- persistent


label ubnentry1
menu label Start in compatibility mode
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/linuxmint.seed boot=casper xforcevesa nomodeset b43.blacklist=yes  ramdisk_size=1048576 root=/dev/ram rw noapic noacpi nosplash irqpoll -- persistent


label ubnentry2
menu label Integrity check
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- persistent


label ubnentry3
menu label Memory test
kernel /casper/memtest
append initrd=/ubninit  persistent


label ubnentry4
menu label Boot from local drive
kernel /ubnkern
append initrd=/ubninit hd0 persistent


label ubnentry5
menu label Start Linux Mint 17.2 Cinnamon 64-bit
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/linuxmint.seed boot=casper iso-scan/filename=${iso_path} quiet splash -- persistent


label ubnentry6
menu label Start Linux Mint 17.2 Cinnamon 64-bit (compatibility mode)
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/linuxmint.seed boot=casper xforcevesa iso-scan/filename=${iso_path} ramdisk_size=1048576 root=/dev/ram rw noapic noacpi nosplash irqpoll -- persistent


label ubnentry7
menu label Check the integrity of the medium
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check iso-scan/filename=${iso_path} quiet splash -- persistent


--------------------------------------------------------------------------------


============== sda1: Version of COM32(R) files used by Syslinux: ===============


 menu.c32                           :  COM32R module (v4.xx)


=============================== sda2/etc/fstab: ================================


--------------------------------------------------------------------------------
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb6 swap swap defaults 0 0
--------------------------------------------------------------------------------


=========================== sdb3/boot/grub/grub.cfg: ===========================


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
set root='hd0,msdos3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  6e513f3a-e5c9-477a-aebd-5b494aa7da29
else
  search --no-floppy --fs-uuid --set=root 6e513f3a-e5c9-477a-aebd-5b494aa7da29
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
insmod part_msdos
insmod ext2
set root='hd0,msdos3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  6e513f3a-e5c9-477a-aebd-5b494aa7da29
else
  search --no-floppy --fs-uuid --set=root 6e513f3a-e5c9-477a-aebd-5b494aa7da29
fi
insmod jpeg
if background_image /boot/saturn-cassini-heat-emission-101116-02.jpg; then
  set color_normal=light-gray/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###


### BEGIN /etc/grub.d/10_linux_proxy ###
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


menuentry "Linux Mint 17.2 Cinnamon 64-bit" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-6e513f3a-e5c9-477a-aebd-5b494aa7da29' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  6e513f3a-e5c9-477a-aebd-5b494aa7da29
    else
      search --no-floppy --fs-uuid --set=root 6e513f3a-e5c9-477a-aebd-5b494aa7da29
    fi
    linux    /boot/vmlinuz-3.16.0-38-generic root=UUID=6e513f3a-e5c9-477a-aebd-5b494aa7da29 ro  
    initrd    /boot/initrd.img-3.16.0-38-generic
}
### END /etc/grub.d/10_linux_proxy ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-B4366F50366F12A2' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  B4366F50366F12A2
    else
      search --no-floppy --fs-uuid --set=root B4366F50366F12A2
    fi
    parttool ${root} hidden-
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/31_linux_proxy ###
submenu "Advanced options for Linux Mint 17.2 Cinnamon 64-bit"{
menuentry "Linux Mint 17.2 Cinnamon 64-bit, with Linux 3.16.0-38-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-38-generic-advanced-6e513f3a-e5c9-477a-aebd-5b494aa7da29' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  6e513f3a-e5c9-477a-aebd-5b494aa7da29
        else
          search --no-floppy --fs-uuid --set=root 6e513f3a-e5c9-477a-aebd-5b494aa7da29
        fi
        echo    'Loading Linux 3.16.0-38-generic ...'
        linux    /boot/vmlinuz-3.16.0-38-generic root=UUID=6e513f3a-e5c9-477a-aebd-5b494aa7da29 ro  
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-38-generic
}
menuentry "Linux Mint 17.2 Cinnamon 64-bit, with Linux 3.16.0-38-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-38-generic-recovery-6e513f3a-e5c9-477a-aebd-5b494aa7da29' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos3'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  6e513f3a-e5c9-477a-aebd-5b494aa7da29
        else
          search --no-floppy --fs-uuid --set=root 6e513f3a-e5c9-477a-aebd-5b494aa7da29
        fi
        echo    'Loading Linux 3.16.0-38-generic ...'
        linux    /boot/vmlinuz-3.16.0-38-generic root=UUID=6e513f3a-e5c9-477a-aebd-5b494aa7da29 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.16.0-38-generic
}
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  6e513f3a-e5c9-477a-aebd-5b494aa7da29
    else
      search --no-floppy --fs-uuid --set=root 6e513f3a-e5c9-477a-aebd-5b494aa7da29
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos3'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  6e513f3a-e5c9-477a-aebd-5b494aa7da29
    else
      search --no-floppy --fs-uuid --set=root 6e513f3a-e5c9-477a-aebd-5b494aa7da29
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
}
### END /etc/grub.d/31_linux_proxy ###


### BEGIN /etc/grub.d/33_lupin ###
### END /etc/grub.d/33_lupin ###


### BEGIN /etc/grub.d/34_linux_xen ###


### END /etc/grub.d/34_linux_xen ###


### BEGIN /etc/grub.d/35_uefi-firmware ###
### END /etc/grub.d/35_uefi-firmware ###


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


=============================== sdb3/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=6e513f3a-e5c9-477a-aebd-5b494aa7da29 /               ext4    errors=remount-ro 0       0
# /home was on /dev/sda5 during installation
UUID=fb6b915e-a013-4be6-9a83-34ada4e1199a /home           ext4    defaults        0       0
# swap was on /dev/sda6 during installation
UUID=fced4701-d760-4828-86cf-016449f05a87 none            swap    sw              0       0
--------------------------------------------------------------------------------


====================== sdb3/boot/extlinux/extlinux.conf: =======================


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


============== sdb3: Version of COM32(R) files used by Syslinux: ===============


 boot/extlinux/chain.c32            :  COM32R module (v4.xx)


======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sdb4


00000000  12 83 bd 40 a9 ff ff 75  0f 84 90 00 00 00 e9 7f  |...@...u........|
00000010  79 01 00 48 8d bd f0 c1  ff ff 48 8d 35 32 4c 24  |y..H......H.52L$|
00000020  00 e8 7a a0 c3 ff 48 8d  bd 40 af ff ff ba 04 00  |..z...H..@......|
00000030  00 00 be 0e 00 00 00 e8  f8 86 cb ff 48 89 85 20  |............H.. |
00000040  af ff ff 48 89 95 28 af  ff ff 48 8b 85 20 af ff  |...H..(...H.. ..|
00000050  ff 48 89 85 00 c2 ff ff  48 8b 85 28 af ff ff 48  |.H......H..(...H|
00000060  89 85 08 c2 ff ff 48 8b  95 f0 c1 ff ff 48 8b 8d  |......H......H..|
00000070  f8 c1 ff ff 48 8b bd 00  c2 ff ff 48 8b b5 08 c2  |....H......H....|
00000080  ff ff e8 1b d9 c3 ff 84  c0 0f 85 03 79 01 00 c7  |............y...|
00000090  85 10 a8 ff ff f4 00 00  00 e9 fe 78 01 00 48 8d  |...........x..H.|
000000a0  bd 40 af ff ff be 0e 00  00 00 e8 13 58 db ff 3c  |.@..........X..<|
000000b0  6c 0f 95 c0 84 c0 0f 85  d6 78 01 00 48 8d bd 40  |l........x..H..@|
000000c0  af ff ff be 0f 00 00 00  e8 f5 57 db ff 0f be c0  |..........W.....|
000000d0  89 85 44 a9 ff ff 83 bd  44 a9 ff ff 65 74 12 83  |..D.....D...et..|
000000e0  bd 44 a9 ff ff 6f 0f 84  d4 00 00 00 e9 a1 78 01  |.D...o........x.|
000000f0  00 48 8d bd 40 af ff ff  be 10 00 00 00 e8 c0 57  |.H..@..........W|
00000100  db ff 0f be c0 89 85 48  a9 ff ff 83 bd 48 a9 ff  |.......H.....H..|
00000110  ff 73 74 0e 83 bd 48 a9  ff ff 75 74 54 e9 70 78  |.st...H...utT.px|
00000120  01 00 48 8d bd 40 af ff  ff be 11 00 00 00 e8 8f  |..H..@..........|
00000130  57 db ff 0f be c0 89 85  4c a9 ff ff 83 bd 4c a9  |W.......L.....L.|
00000140  ff ff 62 74 0e 83 bd 4c  a9 ff ff 68 74 14 e9 3f  |..bt...L...ht..?|
00000150  78 01 00 c7 85 10 a8 ff  ff 0c 01 00 00 e9 3a 78  |x.............:x|
00000160  01 00 c7 85 10 a8 ff ff  0d 01 00 00 e9 2b 78 01  |.............+x.|
00000170  00 48 8d bd 40 af ff ff  be 11 00 00 00 e8 40 57  |.H..@.........@W|
00000180  db ff 0f be c0 89 85 50  a9 ff ff 83 bd 50 a9 ff  |.......P.....P..|
00000190  ff 62 74 0e 83 bd 50 a9  ff ff 68 74 14 e9 f0 77  |.bt...P...ht...w|
000001a0  01 00 c7 85 10 a8 ff ff  0e 01 00 00 e9 eb 77 01  |..............w.|
000001b0  00 c7 85 10 a8 ff ff 0f  01 00 00 e9 dc 77 00 fe  |.............w..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 10 13 04 00 fe  |................|
000001d0  ff ff 05 fe ff ff a5 f4  e4 09 5d 0b e3 00 00 00  |..........].....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200




=============================== StdErr Messages: ===============================


cat: write error: Broken pipe
File descriptor 9 (/proc/4727/mounts) leaked on lvs invocation. Parent PID 14613: bash
File descriptor 63 (pipe:[40255]) leaked on lvs invocation. Parent PID 14613: bash
  No volume groups found


ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-03-20__18h43 ===================
boot-repair version : 4ppa35
boot-sav version : 4ppa35
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa35
boot-repair is executed in live-session (Linux Mint 17.2 Rafaela, rafaela, LinuxMint, x86_64)
CPU op-mode(s):        32-bit, 64-bit
initrd=/ubninit file=/cdrom/preseed/linuxmint.seed boot=casper quiet splash -- persistent BOOT_IMAGE=/ubnkern
ls: cannot access /home/usr/.config: No such file or directory


=================== os-prober:
/dev/sdb1:Windows 7 (loader):Windows:chain
/dev/sdb2:Windows 7 (loader):Windows1:chain
/dev/sdb3:Linux Mint 17.2 Rafaela (17.2):LinuxMint:linux


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="Live Persistent" UUID="7eccbb70-fcba-44bd-aee7-60b4bf824617" TYPE="ext4"
/dev/sda2: LABEL="casper-rw" UUID="c75f3982-352e-4dc3-920a-72d684695ee1" TYPE="ext2"
/dev/sdb1: LABEL="System Reserved" UUID="B4366F50366F12A2" TYPE="ntfs"
/dev/sdb2: UUID="9CA07AB2A07A930E" TYPE="ntfs"
/dev/sdb3: UUID="6e513f3a-e5c9-477a-aebd-5b494aa7da29" TYPE="ext4"
/dev/sdb5: UUID="fb6b915e-a013-4be6-9a83-34ada4e1199a" TYPE="ext4"
/dev/sdb6: UUID="fced4701-d760-4828-86cf-016449f05a87" TYPE="swap"
/dev/sdb7: LABEL="Storage" UUID="6E06CD3138E90FC4" TYPE="ntfs"




1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.


Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== /media/mint/casper-rw/etc/grub.d/ :
drwxr-xr-x 2 root root     4096 Mar 20 13:42 grub.d
total 24
-rwxr-xr-x 1 root root  9791 Dec 17 09:00 00_header
-rwxr-xr-x 1 root root 11620 Mar 20 13:42 10_linux




=================== No kernel in /media/mint/casper-rw/boot:
grub






=================== sdb3/etc/grub.d/ :
drwxr-xr-x  5 root root     4096 Feb 29 19:50 grub.d
total 96
-rwxr-xr-x 1 root root  9791 Dec 17 09:00 00_header
-rwxr-xr-x 1 root root  6058 May 13  2015 05_debian_theme
-rwxr-xr-x 1 root root  1180 Oct 25  2014 06_mint_theme
-rwxr-xr-x 1 root root   643 Jan 15 11:48 10_linux_proxy
-rwxr-xr-x 1 root root 11692 May 13  2015 30_os-prober
-rwxr-xr-x 1 root root  1229 Jan 15 11:48 31_linux_proxy
-rwxr-xr-x 1 root root 10634 Oct  1  2012 33_lupin
-rwxr-xr-x 1 root root 10412 May 13  2015 34_linux_xen
-rwxr-xr-x 1 root root  1416 May 13  2015 35_uefi-firmware
-rwxr-xr-x 1 root root   214 May 13  2015 40_custom
-rwxr-xr-x 1 root root   216 May 13  2015 41_custom
drwxr-xr-x 4 root root  4096 Jan 14 16:59 backup
drwxr-xr-x 2 root root  4096 Jan 14 16:59 bin
drwxr-xr-x 2 root root  4096 Jan 15 11:48 proxifiedScripts
-rw-r--r-- 1 root root   483 May 13  2015 README








=================== sdb3/etc/default/grub :


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


GRUB_CMDLINE_LINUX_DEFAULT=""
export GRUB_MENU_PICTURE="/boot/saturn-cassini-heat-emission-101116-02.jpg"






=================== sdb3recordfail=1/grub/grubenv :
recordfail=1








=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.




=================== PARTITIONS & DISKS:
sda2    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    update-grub,    64,    no-kernel,    no-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    nogrubinstall,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /media/mint/casper-rw.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb1.
sdb2    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb2.
sdb3    : sdb,    not-sepboot,    grubenv-ng    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    customized,    not-far,    /mnt/boot-sav/sdb3.
sdb5    : sdb,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb5.
sdb7    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb7.


sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     usb-disk,    no-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes




=================== parted -l:


Model: SanDisk Cruzer Glide (scsi)
Disk /dev/sda: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
1      1049kB  5244MB  5243MB  primary  ext4         boot
2      5244MB  32.0GB  26.8GB  primary  ext2




Model: ATA WDC WD1600BEVT-2 (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
1      1049kB  106MB   105MB   primary   ntfs            boot
2      106MB   52.4GB  52.3GB  primary   ntfs
3      52.4GB  67.4GB  15.0GB  primary   ext4
4      67.4GB  160GB   92.6GB  extended
5      67.4GB  102GB   35.0GB  logical   ext4
7      102GB   152GB   49.5GB  logical   ntfs
6      152GB   160GB   7612MB  logical   linux-swap(v1)


=================== parted -lm:


BYT;
/dev/sda:32.0GB:scsi:512:512:msdos:SanDisk Cruzer Glide;
1:1049kB:5244MB:5243MB:ext4::boot;
2:5244MB:32.0GB:26.8GB:ext2::;


BYT;
/dev/sdb:160GB:scsi:512:512:msdos:ATA WDC WD1600BEVT-2;
1:1049kB:106MB:105MB:ntfs::boot;
2:106MB:52.4GB:52.3GB:ntfs::;
3:52.4GB:67.4GB:15.0GB:ext4::;
4:67.4GB:160GB:92.6GB:::;
5:67.4GB:102GB:35.0GB:ext4::;
7:102GB:152GB:49.5GB:ntfs::;
6:152GB:160GB:7612MB:linux-swap(v1)::;


=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sda   disk           29.8G
sda1  part ext4       4.9G Live Persistent
sda2  part ext2        25G casper-rw
sdb   disk          149.1G
sdb1  part ntfs       100M System Reserved
sdb2  part ntfs      48.7G
sdb3  part ext4        14G
sdb4  part              1K
sdb5  part ext4      32.6G
sdb6  part swap       7.1G
sdb7  part ntfs      46.1G Storage
sr0   rom            1024M
loop0 loop squashfs   1.5G


KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /cdrom
sda2     1  0  0
sdb      1  0  0 running
sdb1     1  0  0         /mnt/boot-sav/sdb1
sdb2     1  0  0         /mnt/boot-sav/sdb2
sdb3     1  0  0         /mnt/boot-sav/sdb3
sdb4     1  0  0
sdb5     1  0  0         /mnt/boot-sav/sdb5
sdb6     1  0  0         [SWAP]
sdb7     1  0  0         /mnt/boot-sav/sdb7
sr0      1  0  1 running
loop0    1  1  0         /rofs




=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sda1 on /cdrom type ext4 (ro,noatime,data=ordered)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=mint)
/dev/sda2 on /media/mint/casper-rw type ext2 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb3 on /mnt/boot-sav/sdb3 type ext4 (rw)
/dev/sdb5 on /mnt/boot-sav/sdb5 type ext4 (rw)
/dev/sdb7 on /mnt/boot-sav/sdb7 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)




=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 sdb4 sdb5 sdb6 sdb7 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hpet input kmsg kvm log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdb1 sdb2 sdb3 sdb4 sdb5 sdb6 sdb7 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control


=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 1f 03 00 00 00 00 00  |................|
00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|
00000040  f6 00 00 00 01 00 00 00  a2 12 6f 36 50 6f 36 b4  |..........o6Po6.|
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
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 03 00  |........?....(..|
00000020  00 00 00 00 80 00 80 00  ff 5f 17 06 00 00 00 00  |........._......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  0e 93 7a a0 b2 7a a0 9c  |..........z..z..|
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


=================== hexdump -n512 -C /dev/sdb7
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 b0 ec 0b  |........?.......|
00000020  00 00 00 00 80 00 80 00  9f 01 c3 05 00 00 00 00  |................|
00000030  04 00 00 00 00 00 00 00  19 30 5c 00 00 00 00 00  |.........0.....|
00000040  f6 00 00 00 01 00 00 00  c4 0f e9 38 31 cd 06 6e  |...........81..n|
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
udev           devtmpfs   1.4G   12K  1.4G   1% /dev
tmpfs          tmpfs      276M  960K  275M   1% /run
/dev/sda1      ext4       4.7G  1.6G  2.9G  36% /cdrom
/dev/loop0     squashfs   1.5G  1.5G     0 100% /rofs
/cow           overlayfs   25G  2.4G   21G  11% /
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.4G  8.0K  1.4G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.4G  724K  1.4G   1% /run/shm
none           tmpfs      100M   12K  100M   1% /run/user
/dev/sda2      ext2        25G  2.4G   21G  11% /media/mint/casper-rw
/dev/sdb1      fuseblk    100M   25M   76M  25% /mnt/boot-sav/sdb1
/dev/sdb2      fuseblk     49G   21G   29G  42% /mnt/boot-sav/sdb2
/dev/sdb3      ext4        14G  6.9G  6.1G  53% /mnt/boot-sav/sdb3
/dev/sdb5      ext4        32G  4.9G   26G  17% /mnt/boot-sav/sdb5
/dev/sdb7      fuseblk     47G  6.9G   40G  15% /mnt/boot-sav/sdb7


=================== fdisk -l:


Disk /dev/sda: 32.0 GB, 32015679488 bytes
64 heads, 32 sectors/track, 30532 cylinders, total 62530624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000873b4


Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10242048    62529535    26143744   83  Linux


Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f35ab


Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   102402047    51097600    7  HPFS/NTFS/exFAT
/dev/sdb3       102402048   131698687    14648320   83  Linux
/dev/sdb4       131700734   312580095    90439681    5  Extended
/dev/sdb5       131700736   200058879    34179072   83  Linux
/dev/sdb6       297713664   312580095     7433216   82  Linux swap / Solaris
/dev/sdb7       200060928   296726943    48333008    7  HPFS/NTFS/exFAT


Partition table entries are not in disk order








=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to fix customized files) and reinstall the grub2 of sdb3 into the MBRs of all disks (except USB without OS).
Additional repair would be performed: unhide-bootmenu-10s




=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sdb (160GB) disk!




=================== User settings
The settings chosen by the user will not act on the boot.







```

Note that when this Summary was created I was booted to a Live USB persistent version of Mint 17.2, so sda is the USB thumb drive and sdb is the internal HDD present on the laptop. I have also changed the settings of Chrome and FF to use software acceleration, which seemed to help a bit.:) BUT I still get the issue if I open more than 4-5 tabs in either browser.:icon_frown:


Anyone have any suggestions on what I can do to figure out what exactly is going on here?!? THANKS a lot in advance...I really am liking Mint, just a few little annoying issues.

---

