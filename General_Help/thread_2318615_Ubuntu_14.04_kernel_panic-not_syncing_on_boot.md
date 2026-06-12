---
title: "Ubuntu 14.04 kernel panic-not syncing on boot"
date: 2016-03-27
forum: General Help
---

### Post by josh172 on 2016-03-27
I am dual booting Ubuntu 14.04 and Windows 7. The machine is a Core 2 Duo 2.53 GHz, 4GB memory. Ubuntu has been installed for about 2 months, I use it several times a week and have had few problems so far. I used it yesterday without problems, today it would not boot:

[ATTACH=CONFIG]268017[/ATTACH]

I tried all of the advanced boot options, all gave the same result. I tried the boot repair disk, recommended repair. It told me to paste a few lines in a terminal, it gave me multiple errors and stopped due to errors.

I haven't updated Ubuntu within the past few days, and didn't the last time I used it. The only changes in hardware I've had was the graphics card starting to cause problems in Windows, I switched to the onboard graphics 2 days before and then switched back yesterday after cleaning the computer out, it worked fine in Ubuntu & Windows the rest of the day. Windows has worked normally today except wanting to run CHKDSK after I tried using the Ubuntu boot repair disk.

Here is the boot info file from the boot repair disk:

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]




============================= Boot Info Summary: ===============================


 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 3db4817a-8342-4390-a2fe-16206b723ba2 root hd1,msdos5 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => Windows 7/8/2012 is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       
    Boot sector type:  Grub Legacy
    Boot sector info:  Grub Legacy (v0.97) is installed in the boot sector 
                       of sda1 and looks at sector 2098 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #1 
                       for /boot/grub/menu.lst.
    Mounting failed:   mount: unknown filesystem type ''


sda2: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr


sdb1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb2: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 


sdb5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.3 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img


sdb6: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1               2,048    41,945,087    41,943,040  bf Solaris
/dev/sda2    *     41,945,088 1,953,519,615 1,911,574,528   7 NTFS / exFAT / HPFS




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1               2,048 3,697,311,743 3,697,309,696   7 NTFS / exFAT / HPFS
/dev/sdb2       3,697,313,790 3,907,028,991   209,715,202   5 Extended
/dev/sdb5    *  3,697,313,792 3,900,217,343   202,903,552  83 Linux
/dev/sdb6       3,900,219,392 3,907,028,991     6,809,600  82 Linux swap / Solaris




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda2        70CE5614CE55D348                       ntfs       MCP
/dev/sda5        9712230012476227400                    zfs_member rpool
/dev/sdb1        4A2C02CA2C02B0CD                       ntfs       HAL
/dev/sdb5        3db4817a-8342-4390-a2fe-16206b723ba2   ext4       
/dev/sr0                                                iso9660    Boot-Repair-Disk 64bit
/dev/zram0       b23ddc79-855c-4030-97bf-28b6ddea7e19   swap       
/dev/zram1       5623c815-0ea4-464e-a390-5e9f913cc2ef   swap       


========================= "ls -l /dev/disk/by-id" output: ======================


total 0
lrwxrwxrwx 1 root root  9 Mar 27 18:59 ata-HL-DT-ST_DVDRAM_GH24NSB0_K38E5LB1626 -> ../../sr0
lrwxrwxrwx 1 root root  9 Mar 27 23:08 ata-Hitachi_HUA722020ALA331_B9G6H46F -> ../../sdb
lrwxrwxrwx 1 root root 10 Mar 27 23:08 ata-Hitachi_HUA722020ALA331_B9G6H46F-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Mar 27 19:01 ata-Hitachi_HUA722020ALA331_B9G6H46F-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Mar 27 18:59 ata-Hitachi_HUA722020ALA331_B9G6H46F-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Mar 27 18:59 ata-Hitachi_HUA722020ALA331_B9G6H46F-part6 -> ../../sdb6
lrwxrwxrwx 1 root root  9 Mar 27 23:08 ata-TOSHIBA_DT01ACA100_237J013PS -> ../../sda
lrwxrwxrwx 1 root root 10 Mar 27 18:59 ata-TOSHIBA_DT01ACA100_237J013PS-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Mar 27 23:08 ata-TOSHIBA_DT01ACA100_237J013PS-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Mar 27 18:59 ata-TOSHIBA_DT01ACA100_237J013PS-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Mar 27 18:59 ata-TOSHIBA_DT01ACA100_237J013PS-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Mar 27 18:59 ata-TOSHIBA_DT01ACA100_237J013PS-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 Mar 27 23:08 wwn-0x5000039ff2f18c95 -> ../../sda
lrwxrwxrwx 1 root root 10 Mar 27 18:59 wwn-0x5000039ff2f18c95-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Mar 27 23:08 wwn-0x5000039ff2f18c95-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Mar 27 18:59 wwn-0x5000039ff2f18c95-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Mar 27 18:59 wwn-0x5000039ff2f18c95-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Mar 27 18:59 wwn-0x5000039ff2f18c95-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 Mar 27 23:08 wwn-0x5000cca222c2f30b -> ../../sdb
lrwxrwxrwx 1 root root 10 Mar 27 23:08 wwn-0x5000cca222c2f30b-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Mar 27 19:01 wwn-0x5000cca222c2f30b-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Mar 27 18:59 wwn-0x5000cca222c2f30b-part5 -> ../../sdb5
lrwxrwxrwx 1 root root 10 Mar 27 18:59 wwn-0x5000cca222c2f30b-part6 -> ../../sdb6
lrwxrwxrwx 1 root root  9 Mar 27 18:59 wwn-0x5001480000000000 -> ../../sr0


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)




========================== sda2/grldr embedded menu: ===========================


--------------------------------------------------------------------------------
--------------------------------------------------------------------------------


=========================== sdb5/boot/grub/grub.cfg: ===========================


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
   set default="Windows 7 (loader) (on /dev/sda2)"
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
set root='hd1,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3db4817a-8342-4390-a2fe-16206b723ba2
else
  search --no-floppy --fs-uuid --set=root 3db4817a-8342-4390-a2fe-16206b723ba2
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###


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


### END /etc/grub.d/10_linux_proxy ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-70CE5614CE55D348' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  70CE5614CE55D348
    else
      search --no-floppy --fs-uuid --set=root 70CE5614CE55D348
    fi
    parttool ${root} hidden-
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/33_linux_proxy ###
menuentry "Ubuntu" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-3db4817a-8342-4390-a2fe-16206b723ba2' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3db4817a-8342-4390-a2fe-16206b723ba2
    else
      search --no-floppy --fs-uuid --set=root 3db4817a-8342-4390-a2fe-16206b723ba2
    fi
    linux    /boot/vmlinuz-3.19.0-51-generic root=UUID=3db4817a-8342-4390-a2fe-16206b723ba2 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.19.0-51-generic
}
submenu "Advanced options for Ubuntu"{
menuentry "Ubuntu, with Linux 3.19.0-51-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-51-generic-advanced-3db4817a-8342-4390-a2fe-16206b723ba2' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3db4817a-8342-4390-a2fe-16206b723ba2
        else
          search --no-floppy --fs-uuid --set=root 3db4817a-8342-4390-a2fe-16206b723ba2
        fi
        echo    'Loading Linux 3.19.0-51-generic ...'
        linux    /boot/vmlinuz-3.19.0-51-generic root=UUID=3db4817a-8342-4390-a2fe-16206b723ba2 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-51-generic
}
menuentry "Ubuntu, with Linux 3.19.0-51-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-51-generic-recovery-3db4817a-8342-4390-a2fe-16206b723ba2' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3db4817a-8342-4390-a2fe-16206b723ba2
        else
          search --no-floppy --fs-uuid --set=root 3db4817a-8342-4390-a2fe-16206b723ba2
        fi
        echo    'Loading Linux 3.19.0-51-generic ...'
        linux    /boot/vmlinuz-3.19.0-51-generic root=UUID=3db4817a-8342-4390-a2fe-16206b723ba2 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-51-generic
}
menuentry "Ubuntu, with Linux 3.19.0-49-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-49-generic-advanced-3db4817a-8342-4390-a2fe-16206b723ba2' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3db4817a-8342-4390-a2fe-16206b723ba2
        else
          search --no-floppy --fs-uuid --set=root 3db4817a-8342-4390-a2fe-16206b723ba2
        fi
        echo    'Loading Linux 3.19.0-49-generic ...'
        linux    /boot/vmlinuz-3.19.0-49-generic root=UUID=3db4817a-8342-4390-a2fe-16206b723ba2 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-49-generic
}
menuentry "Ubuntu, with Linux 3.19.0-49-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-49-generic-recovery-3db4817a-8342-4390-a2fe-16206b723ba2' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3db4817a-8342-4390-a2fe-16206b723ba2
        else
          search --no-floppy --fs-uuid --set=root 3db4817a-8342-4390-a2fe-16206b723ba2
        fi
        echo    'Loading Linux 3.19.0-49-generic ...'
        linux    /boot/vmlinuz-3.19.0-49-generic root=UUID=3db4817a-8342-4390-a2fe-16206b723ba2 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-49-generic
}
menuentry "Ubuntu, with Linux 3.19.0-47-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-47-generic-advanced-3db4817a-8342-4390-a2fe-16206b723ba2' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3db4817a-8342-4390-a2fe-16206b723ba2
        else
          search --no-floppy --fs-uuid --set=root 3db4817a-8342-4390-a2fe-16206b723ba2
        fi
        echo    'Loading Linux 3.19.0-47-generic ...'
        linux    /boot/vmlinuz-3.19.0-47-generic root=UUID=3db4817a-8342-4390-a2fe-16206b723ba2 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-47-generic
}
menuentry "Ubuntu, with Linux 3.19.0-47-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-47-generic-recovery-3db4817a-8342-4390-a2fe-16206b723ba2' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3db4817a-8342-4390-a2fe-16206b723ba2
        else
          search --no-floppy --fs-uuid --set=root 3db4817a-8342-4390-a2fe-16206b723ba2
        fi
        echo    'Loading Linux 3.19.0-47-generic ...'
        linux    /boot/vmlinuz-3.19.0-47-generic root=UUID=3db4817a-8342-4390-a2fe-16206b723ba2 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-47-generic
}
menuentry "Ubuntu, with Linux 3.19.0-25-generic" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-25-generic-advanced-3db4817a-8342-4390-a2fe-16206b723ba2' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3db4817a-8342-4390-a2fe-16206b723ba2
        else
          search --no-floppy --fs-uuid --set=root 3db4817a-8342-4390-a2fe-16206b723ba2
        fi
        echo    'Loading Linux 3.19.0-25-generic ...'
        linux    /boot/vmlinuz-3.19.0-25-generic root=UUID=3db4817a-8342-4390-a2fe-16206b723ba2 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-25-generic
}
menuentry "Ubuntu, with Linux 3.19.0-25-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.19.0-25-generic-recovery-3db4817a-8342-4390-a2fe-16206b723ba2' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3db4817a-8342-4390-a2fe-16206b723ba2
        else
          search --no-floppy --fs-uuid --set=root 3db4817a-8342-4390-a2fe-16206b723ba2
        fi
        echo    'Loading Linux 3.19.0-25-generic ...'
        linux    /boot/vmlinuz-3.19.0-25-generic root=UUID=3db4817a-8342-4390-a2fe-16206b723ba2 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.19.0-25-generic
}
}
### END /etc/grub.d/33_linux_proxy ###


### BEGIN /etc/grub.d/34_linux_xen ###


### END /etc/grub.d/34_linux_xen ###


### BEGIN /etc/grub.d/35_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3db4817a-8342-4390-a2fe-16206b723ba2
    else
      search --no-floppy --fs-uuid --set=root 3db4817a-8342-4390-a2fe-16206b723ba2
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3db4817a-8342-4390-a2fe-16206b723ba2
    else
      search --no-floppy --fs-uuid --set=root 3db4817a-8342-4390-a2fe-16206b723ba2
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/35_memtest86+ ###


### BEGIN /etc/grub.d/36_uefi-firmware ###
### END /etc/grub.d/36_uefi-firmware ###


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


=============================== sdb5/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=3db4817a-8342-4390-a2fe-16206b723ba2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
#UUID=d49dfcee-3d5f-457a-9c33-514b87f5a9ba none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=70CE5614CE55D348  /media/MCP  ntfs-3g  defaults,windows_names,locale=en_US.utf8  0 0
UUID=4A2C02CA2C02B0CD  /media/HAL  ntfs-3g  defaults,windows_names,locale=en_US.utf8  0 0
--------------------------------------------------------------------------------


=============================== StdErr Messages: ===============================


cat: write error: Broken pipe
File descriptor 9 (/proc/13080/mounts) leaked on lvs invocation. Parent PID 21741: bash
File descriptor 63 (pipe:[189861]) leaked on lvs invocation. Parent PID 21741: bash
  No volume groups found


ADDITIONAL INFORMATION :
=================== log of boot-info 2016-03-27__23h08 ===================
boot-info version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/13080/mounts) leaked on lvs invocation. Parent PID 14585: /bin/sh
No volume groups found
boot-info is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
mount: unknown filesystem type 'zfs_member'
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: unknown filesystem type 'zfs_member'
mount -r /dev/sda5 : Error code 32


=================== os-prober:
/dev/sda2:Windows 7 (loader):Windows:chain
/dev/sdb5:Ubuntu 14.04.3 LTS (14.04):Ubuntu:linux


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda2: LABEL="MCP" UUID="70CE5614CE55D348" TYPE="ntfs"
/dev/sda5: LABEL="rpool" UUID="9712230012476227400" UUID_SUB="17045480245477868706" TYPE="zfs_member"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/sdb1: LABEL="HAL" UUID="4A2C02CA2C02B0CD" TYPE="ntfs"
/dev/sdb5: UUID="3db4817a-8342-4390-a2fe-16206b723ba2" TYPE="ext4"
/dev/zram0: UUID="b23ddc79-855c-4030-97bf-28b6ddea7e19" TYPE="swap"
/dev/zram1: UUID="5623c815-0ea4-464e-a390-5e9f913cc2ef" TYPE="swap"




2 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.


mount: unknown filesystem type 'zfs_member'
mount /dev/sda5 : Error code 32
mount -r /dev/sda5 /mnt/boot-sav/sda5
mount: unknown filesystem type 'zfs_member'
mount -r /dev/sda5 : Error code 32
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== sdb5/etc/grub.d/ :
drwxr-xr-x  5 root root         4096 Feb  1 05:20 grub.d
total 84
-rwxr-xr-x 1 root root  9791 Dec 17 15:00 00_header
-rwxr-xr-x 1 root root  6058 May 13  2015 05_debian_theme
-rwxr-xr-x 1 root root   694 Feb  1 05:20 10_linux_proxy
-rwxr-xr-x 1 root root 11692 Jun 26  2015 30_os-prober
-rwxr-xr-x 1 root root   694 Feb  1 05:20 33_linux_proxy
-rwxr-xr-x 1 root root 10412 Jun 26  2015 34_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 35_memtest86+
-rwxr-xr-x 1 root root  1416 Jun 26  2015 36_uefi-firmware
-rwxr-xr-x 1 root root   214 Jun 26  2015 40_custom
-rwxr-xr-x 1 root root   216 Jun 26  2015 41_custom
drwxr-xr-x 4 root root  4096 Feb  1 05:20 backup
drwxr-xr-x 2 root root  4096 Feb  1 05:20 bin
drwxr-xr-x 2 root root  4096 Feb  1 05:20 proxifiedScripts
-rw-r--r-- 1 root root   483 Jun 26  2015 README








=================== sdb5/etc/default/grub :


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT="Windows 7 (loader) (on /dev/sda2)"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
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


GRUB_SAVEDEFAULT="false"






=================== sdb5recordfail=1/grub/grubenv :
recordfail=1






=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.




=================== PARTITIONS & DISKS:
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sda5    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda5.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb1.
sdb5    : sdb,    not-sepboot,    grubenv-ng    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    customized,    farbios,    /mnt/boot-sav/sdb5.


sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes




=================== parted -l:


Model: ATA TOSHIBA DT01ACA1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
1      1049kB  21.5GB  21.5GB  primary
2      21.5GB  1000GB  979GB   primary  ntfs         boot




Model: ATA Hitachi HUA72202 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system  Flags
1      1049kB  1893GB  1893GB  primary   ntfs
2      1893GB  2000GB  107GB   extended
5      1893GB  1997GB  104GB   logical   ext4         boot
6      1997GB  2000GB  3487MB  logical






                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.


                                                                          
Error: /dev/sr0: unrecognised disk label




                                                                          
Error: /dev/zram0: unrecognised disk label




                                                                          
Error: /dev/zram1: unrecognised disk label


=================== parted -lm:


BYT;
/dev/sda:1000GB:scsi:512:4096:msdos:ATA TOSHIBA DT01ACA1;
1:1049kB:21.5GB:21.5GB:::;
2:21.5GB:1000GB:979GB:ntfs::boot;


BYT;
/dev/sdb:2000GB:scsi:512:512:msdos:ATA Hitachi HUA72202;
1:1049kB:1893GB:1893GB:ntfs::;
2:1893GB:2000GB:107GB:::;
5:1893GB:1997GB:104GB:ext4::boot;
6:1997GB:2000GB:3487MB:::;




                                                                          
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
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /mnt/boot-sav/sdb5 type ext4 (rw)




=================== ls:
/sys/block/fd0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb5 sdb6 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd fd0 full fuse hidraw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sda6 sda7 sdb sdb1 sdb2 sdb5 sdb6 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control


=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 80 02  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 4f f0 71 00 00 00 00  |.........O.q....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  48 d3 55 ce 14 56 ce 70  |........H.U..V.p|
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


=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 77 60 dc 00 00 00 00  |.........w`.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  cd b0 02 2c ca 02 2c 4a  |...........,..,J|
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


=================== df -Th:


Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.6G   42M  1.6G   3% /
udev           devtmpfs   1.6G   12K  1.6G   1% /dev
tmpfs          tmpfs      327M  1.1M  325M   1% /run
/dev/sr0       iso9660    614M  614M     0 100% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      1.6G   48K  1.6G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.6G     0  1.6G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sda2      fuseblk    912G  783G  129G  86% /mnt/boot-sav/sda2
/dev/sdb1      fuseblk    1.8T  214G  1.6T  13% /mnt/boot-sav/sdb1
/dev/sdb5      ext4        96G   20G   71G  22% /mnt/boot-sav/sdb5


=================== fdisk -l:


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xfab5e374


Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    41945087    20971520   bf  Solaris
/dev/sda2   *    41945088  1953519615   955787264    7  HPFS/NTFS/exFAT


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x851caf0c


Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3697311743  1848654848    7  HPFS/NTFS/exFAT
/dev/sdb2      3697313790  3907028991   104857601    5  Extended
/dev/sdb5   *  3697313792  3900217343   101451776   83  Linux
/dev/sdb6      3900219392  3907028991     3404800   82  Linux swap / Solaris




User choice: Is sdb (2000GB) a removable disk? no




gui-tab-other.sh: line 94: _checkbutton_repairfilesystems: command not found




=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to fix customized files) and reinstall the grub2 of sdb5 into the MBRs of all disks (except USB without OS).
The boot flag would be placed on sdb5.
Additional repair would be performed: unhide-bootmenu-10s repair-filesystems




=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sdb (2000GB) disk!




=================== User settings
The settings chosen by the user will not act on the boot.

---

