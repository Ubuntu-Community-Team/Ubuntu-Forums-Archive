---
title: "No Boot after restore from Redo Backup"
date: 2015-08-25
forum: General Help
---

### Post by ewcga on 2015-08-25
I have restored my Ubuntu server using Redo Backup and Recovery, from a backup I took last year. This is a Dell server with  Perc 5/i RAID controller running RAID 1.

After the restore, the server won't boot, it just gets stuck in a restart loop. I have run Boot-Repair and I get the grub-pc purge cancelled message at the completion of the boot-repair process. It still won't boot after boot repair was run. 

The boot-info below is after boot repair was run. I can log into a live CD and browse all the files. Is it possible to repair this installation so it can boot again?


```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Nov2014]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

cganagios-vg-root: _____________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

cganagios-vg-swap_1: ___________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 72.7 GB, 72746008576 bytes
255 heads, 63 sectors/track, 8844 cylinders, total 142082048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       499,711       497,664  83 Linux
/dev/sda2             501,758   142,079,999   141,578,242   5 Extended
/dev/sda5             501,760   142,079,999   141,578,240  8e Linux LVM


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/cganagios--vg-root dacd1655-3a1e-4d20-8257-1b777af08f7c   ext4       
/dev/mapper/cganagios--vg-swap_1 8daf36e2-7cdc-4548-989a-8f3c4018bb0b   swap       
/dev/sda1        cb6dc053-6e55-4f53-978a-2a22f595221c   ext2       
/dev/sda5        DXGmQ9-vfWm-NgZG-3yXE-9UwK-zkj4-CIetZS LVM2_member 
/dev/sr0                                                iso9660    Boot-Repair-Disk 64bit
/dev/zram0       439ef505-8711-439e-95e7-cc506db9ab2e   swap       
/dev/zram1       fe0db8d8-d330-45af-a6ca-c7ce7d0f5f94   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Aug 24 22:05 ata-HL-DT-STCD-RW_DVD-ROM_GCC-T10N -> ../../sr0
lrwxrwxrwx 1 root root 10 Aug 24 22:07 dm-name-cganagios--vg-root -> ../../dm-0
lrwxrwxrwx 1 root root 10 Aug 24 22:07 dm-name-cganagios--vg-swap_1 -> ../../dm-1
lrwxrwxrwx 1 root root 10 Aug 24 22:07 dm-uuid-LVM-YntYUK83bV6J2A5aIaVyiOWQD1nsJKOYB55WDQGoYnFcrLSSj2l8Dl7PD6TNLc0r -> ../../dm-1
lrwxrwxrwx 1 root root 10 Aug 24 22:07 dm-uuid-LVM-YntYUK83bV6J2A5aIaVyiOWQD1nsJKOYkCvhLueZWuE6Jeh4DOxXky6JU1S82yUY -> ../../dm-0
lrwxrwxrwx 1 root root  9 Aug 24 22:07 scsi-36001c230c8fdbd000efe8c19eba35ac4 -> ../../sda
lrwxrwxrwx 1 root root 10 Aug 24 22:05 scsi-36001c230c8fdbd000efe8c19eba35ac4-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Aug 24 22:05 scsi-36001c230c8fdbd000efe8c19eba35ac4-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Aug 24 22:05 scsi-36001c230c8fdbd000efe8c19eba35ac4-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Aug 24 22:07 wwn-0x6001c230c8fdbd000efe8c19eba35ac4 -> ../../sda
lrwxrwxrwx 1 root root 10 Aug 24 22:05 wwn-0x6001c230c8fdbd000efe8c19eba35ac4-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Aug 24 22:05 wwn-0x6001c230c8fdbd000efe8c19eba35ac4-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Aug 24 22:05 wwn-0x6001c230c8fdbd000efe8c19eba35ac4-part5 -> ../../sda5

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
cganagios--vg-root
cganagios--vg-swap_1
control

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


============================= sda1/grub/grub.cfg: ==============================

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
insmod lvm
insmod ext2
set root='lvm/cganagios--vg-root'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint='lvm/cganagios--vg-root'  dacd1655-3a1e-4d20-8257-1b777af08f7c
else
  search --no-floppy --fs-uuid --set=root dacd1655-3a1e-4d20-8257-1b777af08f7c
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
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-dacd1655-3a1e-4d20-8257-1b777af08f7c' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  cb6dc053-6e55-4f53-978a-2a22f595221c
    else
      search --no-floppy --fs-uuid --set=root cb6dc053-6e55-4f53-978a-2a22f595221c
    fi
    linux    /vmlinuz-3.11.0-18-generic root=/dev/mapper/cganagios--vg-root ro   
    initrd    /initrd.img-3.11.0-18-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-dacd1655-3a1e-4d20-8257-1b777af08f7c' {
    menuentry 'Ubuntu, with Linux 3.11.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-18-generic-advanced-dacd1655-3a1e-4d20-8257-1b777af08f7c' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  cb6dc053-6e55-4f53-978a-2a22f595221c
        else
          search --no-floppy --fs-uuid --set=root cb6dc053-6e55-4f53-978a-2a22f595221c
        fi
        echo    'Loading Linux 3.11.0-18-generic ...'
        linux    /vmlinuz-3.11.0-18-generic root=/dev/mapper/cganagios--vg-root ro   
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.11.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-18-generic-recovery-dacd1655-3a1e-4d20-8257-1b777af08f7c' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  cb6dc053-6e55-4f53-978a-2a22f595221c
        else
          search --no-floppy --fs-uuid --set=root cb6dc053-6e55-4f53-978a-2a22f595221c
        fi
        echo    'Loading Linux 3.11.0-18-generic ...'
        linux    /vmlinuz-3.11.0-18-generic root=/dev/mapper/cganagios--vg-root ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.11.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-advanced-dacd1655-3a1e-4d20-8257-1b777af08f7c' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  cb6dc053-6e55-4f53-978a-2a22f595221c
        else
          search --no-floppy --fs-uuid --set=root cb6dc053-6e55-4f53-978a-2a22f595221c
        fi
        echo    'Loading Linux 3.11.0-12-generic ...'
        linux    /vmlinuz-3.11.0-12-generic root=/dev/mapper/cganagios--vg-root ro   
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.11.0-12-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-recovery-dacd1655-3a1e-4d20-8257-1b777af08f7c' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  cb6dc053-6e55-4f53-978a-2a22f595221c
        else
          search --no-floppy --fs-uuid --set=root cb6dc053-6e55-4f53-978a-2a22f595221c
        fi
        echo    'Loading Linux 3.11.0-12-generic ...'
        linux    /vmlinuz-3.11.0-12-generic root=/dev/mapper/cganagios--vg-root ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.11.0-12-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  cb6dc053-6e55-4f53-978a-2a22f595221c
    else
      search --no-floppy --fs-uuid --set=root cb6dc053-6e55-4f53-978a-2a22f595221c
    fi
    linux16    /memtest86+.bin
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  cb6dc053-6e55-4f53-978a-2a22f595221c
    else
      search --no-floppy --fs-uuid --set=root cb6dc053-6e55-4f53-978a-2a22f595221c
    fi
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  89 94 24 b0 00 00 00 74  0b 49 83 7a 18 00 0f 84  |..$....t.I.z....|
00000010  3c 12 00 00 48 8b 84 24  b0 00 00 00 8b 48 04 31  |<...H..$.....H.1|
00000020  c0 85 c9 74 0f 48 8b 05  a4 24 a0 00 8d 51 ff 48  |...t.H...$...Q.H|
00000030  8b 44 d0 08 48 83 78 20  00 0f 84 3f 0e 00 00 48  |.D..H.x ...?...H|
00000040  8b 43 20 48 8b 54 24 60  41 be 01 00 00 00 48 89  |.C H.T$`A.....H.|
00000050  02 e9 fa fb ff ff bf 09  00 00 00 45 31 f6 e8 ad  |...........E1...|
00000060  1f 02 00 84 c0 0f 84 e5  fb ff ff 48 8b 0d 56 24  |...........H..V$|
00000070  a0 00 ba 20 00 00 00 be  01 00 00 00 bf 18 2f c3  |... ........../.|
00000080  00 e8 5a eb c7 ff e9 c5  fb ff ff 4c 89 e7 88 4c  |..Z........L...L|
00000090  24 30 4c 89 44 24 28 4c  89 54 24 18 44 88 5c 24  |$0L.D$(L.T$.D.\$|
000000a0  20 e8 9a 77 f1 ff 0f b6  4c 24 30 4c 8b 44 24 28  | ..w....L$0L.D$(|
000000b0  4c 8b 54 24 18 44 0f b6  5c 24 20 e9 bb fc ff ff  |L.T$.D..\$ .....|
000000c0  31 f6 4c 89 e7 4c 89 44  24 28 4c 89 54 24 18 44  |1.L..L.D$(L.T$.D|
000000d0  88 5c 24 20 e8 17 f9 ff  ff 48 85 c0 4c 8b 44 24  |.\$ .....H..L.D$|
000000e0  28 4c 8b 54 24 18 44 0f  b6 5c 24 20 0f 85 bb fe  |(L.T$.D..\$ ....|
000000f0  ff ff bf 09 00 00 00 45  31 f6 e8 11 1f 02 00 84  |.......E1.......|
00000100  c0 0f 84 49 fb ff ff 48  8b 0d ba 23 a0 00 ba 2a  |...I...H...#...*|
00000110  00 00 00 be 01 00 00 00  bf 68 2f c3 00 e8 be ea  |.........h/.....|
00000120  c7 ff e9 29 fb ff ff 48  89 ac 24 b0 00 00 00 4c  |...)...H..$....L|
00000130  89 84 24 c8 00 00 00 c6  84 24 a0 00 00 00 00 c7  |..$......$......|
00000140  84 24 8c 00 00 00 01 00  00 00 c7 84 24 04 01 00  |.$..........$...|
00000150  00 01 00 00 00 48 8b bc  24 c8 00 00 00 31 f6 4c  |.....H..$....1.L|
00000160  89 44 24 28 4c 89 54 24  18 44 88 5c 24 20 e8 fd  |.D$(L.T$.D.\$ ..|
00000170  20 33 00 85 c0 89 84 24  88 00 00 00 4c 8b 44 24  | 3.....$....L.D$|
00000180  28 4c 8b 54 24 18 44 0f  b6 5c 24 20 0f 84 d0 11  |(L.T$.D..\$ ....|
00000190  00 00 83 bc 24 88 00 00  00 04 74 18 80 bc 24 bb  |....$.....t...$.|
000001a0  00 00 00 00 74 0e 83 bc  24 88 00 00 00 01 0f 85  |....t...$.......|
000001b0  c9 11 00 00 4d 85 ff 74  17 49 8b 57 30 48 00 3b  |....M..t.I.W0H.;|
000001c0  1d 1f 8e fe ff ff 02 00  00 00 00 50 70 08 00 00  |...........Pp...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on cganagios-vg-root


Unknown BootLoader on cganagios-vg-swap_1



=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
File descriptor 9 (/proc/9157/mounts) leaked on lvs invocation. Parent PID 17064: bash
File descriptor 63 (pipe:[32286]) leaked on lvs invocation. Parent PID 17064: bash
File descriptor 9 (/proc/9157/mounts) leaked on lvchange invocation. Parent PID 17439: bash
File descriptor 63 (pipe:[32286]) leaked on lvchange invocation. Parent PID 17439: bash
  skip_dev_dir: Couldn't split up device name cganagios-vg-root
  Volume group "cganagios-vg-root" not found
  Skipping volume group cganagios-vg-root
hexdump: /dev/mapper/cganagios-vg-root: No such file or directory
hexdump: /dev/mapper/cganagios-vg-root: No such file or directory
File descriptor 9 (/proc/9157/mounts) leaked on lvchange invocation. Parent PID 17439: bash
File descriptor 63 (pipe:[32286]) leaked on lvchange invocation. Parent PID 17439: bash
  skip_dev_dir: Couldn't split up device name cganagios-vg-swap_1
  Volume group "cganagios-vg-swap_1" not found
  Skipping volume group cganagios-vg-swap_1
hexdump: /dev/mapper/cganagios-vg-swap_1: No such file or directory
hexdump: /dev/mapper/cganagios-vg-swap_1: No such file or directory
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-08-24__22h07 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
BLKID BEFORE LVM ACTIVATION:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/sda1: UUID="cb6dc053-6e55-4f53-978a-2a22f595221c" TYPE="ext2"
/dev/sda5: UUID="DXGmQ9-vfWm-NgZG-3yXE-9UwK-zkj4-CIetZS" TYPE="LVM2_member"
/dev/mapper/cganagios--vg-root: UUID="dacd1655-3a1e-4d20-8257-1b777af08f7c" TYPE="ext4"
/dev/mapper/cganagios--vg-swap_1: UUID="8daf36e2-7cdc-4548-989a-8f3c4018bb0b" TYPE="swap"
/dev/zram0: UUID="439ef505-8711-439e-95e7-cc506db9ab2e" TYPE="swap"
/dev/zram1: UUID="fe0db8d8-d330-45af-a6ca-c7ce7d0f5f94" TYPE="swap"
MODPROBE
VGSCAN
File descriptor 9 (/proc/9157/mounts) leaked on vgscan invocation. Parent PID 9165: /bin/bash
Reading all physical volumes.  This may take a while...
Found volume group "cganagios-vg" using metadata type lvm2
VGCHANGE
File descriptor 9 (/proc/9157/mounts) leaked on vgchange invocation. Parent PID 9165: /bin/bash
2 logical volume(s) in volume group "cganagios-vg" now active
File descriptor 9 (/proc/9157/mounts) leaked on lvscan invocation. Parent PID 9165: /bin/bash
LVSCAN:
ACTIVE            '/dev/cganagios-vg/root' [63.51 GiB] inherit
ACTIVE            '/dev/cganagios-vg/swap_1' [4.00 GiB] inherit
Is there RAID on this computer? yes

BLKID BEFORE RAID ACTIVATION:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/sda1: UUID="cb6dc053-6e55-4f53-978a-2a22f595221c" TYPE="ext2"
/dev/sda5: UUID="DXGmQ9-vfWm-NgZG-3yXE-9UwK-zkj4-CIetZS" TYPE="LVM2_member"
/dev/mapper/cganagios--vg-root: UUID="dacd1655-3a1e-4d20-8257-1b777af08f7c" TYPE="ext4"
/dev/mapper/cganagios--vg-swap_1: UUID="8daf36e2-7cdc-4548-989a-8f3c4018bb0b" TYPE="swap"
/dev/zram0: UUID="439ef505-8711-439e-95e7-cc506db9ab2e" TYPE="swap"
/dev/zram1: UUID="fe0db8d8-d330-45af-a6ca-c7ce7d0f5f94" TYPE="swap"
dmraid -si -c: no raid disks
No DMRAID disk.
[dmraid] packages may interfere with MDraid. Do you want to remove them? no
User chose to keep dmraid. It may interfere with mdadm.
Scanning MDraid Partitions
mdadm: No arrays found in config file or automatically
mdadm --detail --scan:
Warning: no DMRAID nor MD_ARRAY.
File descriptor 9 (/proc/9157/mounts) leaked on lvs invocation. Parent PID 10690: /bin/sh
File descriptor 9 (/proc/9157/mounts) leaked on vgs invocation. Parent PID 10808: grub-probe
File descriptor 9 (/proc/9157/mounts) leaked on vgs invocation. Parent PID 10808: grub-probe
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[dmraid -sa -c] no
[dmraid -sa -c] raid
[dmraid -sa -c] disks
Set sda as corresponding disk of mapper/cganagios--vg-root
Disk /dev/mapper/cganagios--vg-root doesn't contain a valid partition table
Disk /dev/mapper/cganagios--vg-swap_1 doesn't contain a valid partition table

=================== os-prober:
/dev/mapper/cganagios--vg-root:Ubuntu 13.10 (13.10):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sr0: LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660"
/dev/sda1: UUID="cb6dc053-6e55-4f53-978a-2a22f595221c" TYPE="ext2"
/dev/sda5: UUID="DXGmQ9-vfWm-NgZG-3yXE-9UwK-zkj4-CIetZS" TYPE="LVM2_member"
/dev/mapper/cganagios--vg-root: UUID="dacd1655-3a1e-4d20-8257-1b777af08f7c" TYPE="ext4"
/dev/mapper/cganagios--vg-swap_1: UUID="8daf36e2-7cdc-4548-989a-8f3c4018bb0b" TYPE="swap"
/dev/zram0: UUID="439ef505-8711-439e-95e7-cc506db9ab2e" TYPE="swap"
/dev/zram1: UUID="fe0db8d8-d330-45af-a6ca-c7ce7d0f5f94" TYPE="swap"

[dmraid -sa -c] no
[dmraid -sa -c] raid
[dmraid -sa -c] disks
Set sda as corresponding disk of mapper/cganagios--vg-root

1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

=================== mapper/cganagios--vg-root/etc/grub.d/ :
drwxr-xr-x 2 root root    4096 Mar 20  2014 grub.d
total 72
-rwxr-xr-x 1 root root  7850 Oct 23  2013 00_header
-rwxr-xr-x 1 root root  5949 Aug 15  2013 05_debian_theme
-rwxr-xr-x 1 root root 11479 Oct 23  2013 10_linux
-rwxr-xr-x 1 root root 10258 Oct 23  2013 20_linux_xen
-rwxr-xr-x 1 root root  1798 Jun 17  2013 20_memtest86+
-rwxr-xr-x 1 root root 11531 Oct 23  2013 30_os-prober
-rwxr-xr-x 1 root root  1426 Oct 23  2013 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 23  2013 40_custom
-rwxr-xr-x 1 root root   216 Oct 23  2013 41_custom
-rw-r--r-- 1 root root   483 Oct 23  2013 README




=================== mapper/cganagios--vg-root/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
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



/boot detected in the fstab of mapper/cganagios--vg-root: UUID=cb6dc053-6e55-4f53-978a-2a22f595221c  (sda1)
=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    is-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
mapper/cganagios--vg-root    : sda,    not-sepboot,    no-grubenv    grub2,    grub-pc ,    update-grub,    64,    no-boot,    is-os,    not--efi--part,    fstab-has-goodBOOT,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/mapper/cganagios--vg-root.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: DELL PERC 5/i (scsi)
Disk /dev/sda: 72.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
1      1049kB  256MB   255MB   primary   ext2         boot
2      257MB   72.7GB  72.5GB  extended
5      257MB   72.7GB  72.5GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/cganagios--vg-root: 68.2GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
1      0.00B  68.2GB  68.2GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/cganagios--vg-swap_1: 4291MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
1      0.00B  4291MB  4291MB  linux-swap(v1)



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:72.7GB:scsi:512:512:msdos:DELL PERC 5/i;
1:1049kB:256MB:255MB:ext2::boot;
2:257MB:72.7GB:72.5GB:::;
5:257MB:72.7GB:72.5GB:::lvm;

BYT;
/dev/mapper/cganagios--vg-root:68.2GB:dm:512:512:loop:Linux device-mapper (linear);
1:0.00B:68.2GB:68.2GB:ext4::;

BYT;
/dev/mapper/cganagios--vg-swap_1:4291MB:dm:512:512:loop:Linux device-mapper (linear);
1:0.00B:4291MB:4291MB:linux-swap(v1)::;


                                                                          
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
/dev/sda1 on /mnt/boot-sav/sda1 type ext2 (rw)
/dev/mapper/cganagios--vg-root on /mnt/boot-sav/mapper/cganagios--vg-root type ext4 (rw)


=================== ls:
/sys/block/dm-0 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-1 (filtered):  alignment_offset bdi capability dev discard_alignment dm ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cganagios-vg char console core cpu cpu_dma_latency cuse disk dm-0 dm-1 dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg kvm log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom vga_arbiter vhci vhost-net zero
ls /dev/mapper:  cganagios--vg-root cganagios--vg-swap_1 control
Disk /dev/mapper/cganagios--vg-root doesn't contain a valid partition table
Disk /dev/mapper/cganagios--vg-swap_1 doesn't contain a valid partition table

=================== df -Th:

Filesystem                     Type       Size  Used Avail Use% Mounted on
/cow                           overlayfs  2.0G   28M  2.0G   2% /
udev                           devtmpfs   2.0G   12K  2.0G   1% /dev
tmpfs                          tmpfs      395M 1004K  394M   1% /run
/dev/sr0                       iso9660    614M  614M     0 100% /cdrom
/dev/loop0                     squashfs   549M  549M     0 100% /rofs
none                           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs                          tmpfs      2.0G  8.0K  2.0G   1% /tmp
none                           tmpfs      5.0M     0  5.0M   0% /run/lock
none                           tmpfs      2.0G     0  2.0G   0% /run/shm
none                           tmpfs      100M   16K  100M   1% /run/user
/dev/sda1                      ext2       236M   61M  163M  28% /mnt/boot-sav/sda1
/dev/mapper/cganagios--vg-root ext4        63G  2.4G   57G   4% /mnt/boot-sav/mapper/cganagios--vg-root

=================== fdisk -l:

Disk /dev/sda: 72.7 GB, 72746008576 bytes
255 heads, 63 sectors/track, 8844 cylinders, total 142082048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a837b

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   142079999    70789121    5  Extended
/dev/sda5          501760   142079999    70789120   8e  Linux LVM

Disk /dev/mapper/cganagios--vg-root: 68.2 GB, 68195188736 bytes
255 heads, 63 sectors/track, 8290 cylinders, total 133193728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/cganagios--vg-swap_1: 4290 MB, 4290772992 bytes
255 heads, 63 sectors/track, 521 cylinders, total 8380416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


/boot detected. Please check the options.

=================== Recommended repair
The default repair of the Boot-Repair utility will purge (in order to enable-raid enable-lvm) and reinstall the grub2 of mapper/cganagios--vg-root into the MBR of sda, using the following options:        sda1/boot,
Additional repair will be performed: unhide-bootmenu-10s


/boot added in mapper/cganagios--vg-root/fstab
Mount sda1 on /mnt/boot-sav/mapper/cganagios--vg-root/boot
chroot /mnt/boot-sav/mapper/cganagios--vg-root apt-get -y --force-yes update
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/saucy-security/main/source/Sources  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/saucy-security/restricted/source/Sources  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/saucy-security/universe/source/Sources  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/saucy-security/multiverse/source/Sources  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/saucy-security/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/saucy-security/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/saucy-security/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/saucy-security/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/saucy-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/saucy-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/saucy-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/saucy-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.201 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy/main/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy/restricted/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy/universe/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy/multiverse/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/main/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/restricted/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-backports/main/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-backports/universe/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/source/Sources  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-backports/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-backports/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-backports/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.14 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
Purge the GRUB of mapper/cganagios--vg-root
grub-pc available

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 2 not upgraded.
WARNING: The following packages cannot be authenticated!
grub-pc
Err http://us.archive.ubuntu.com/ubuntu/ saucy-updates/main grub-pc amd64 2.00-19ubuntu2.1
404  Not Found [IP: 91.189.91.13 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_2.00-19ubuntu2.1_amd64.deb  404  Not Found [IP: 91.189.91.13 80]
E: Some files failed to download
DEBCHECK debNG, grub-pc
DEBCHECK debNG
=================== grub-pc purge cancelled
grub-pc purge cancelled. Please report this message to boot.repair@gmail.com


=================== Suggested repair
The default repair of the Boot-Repair utility will purge (in order to enable-raid enable-lvm) and reinstall the grub-pc of mapper/cganagios--vg-root into the MBR of sda, using the following options:        sda1/boot,
Additional repair will be performed: unhide-bootmenu-10s


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2015-08-25
Your Saucy 13.10 when end of life a year ago.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Most with servers use LTS releases to avoid the EOL issues.

---

