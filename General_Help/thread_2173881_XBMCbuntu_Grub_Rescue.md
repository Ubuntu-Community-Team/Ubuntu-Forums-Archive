---
title: "XBMCbuntu Grub Rescue"
date: 2013-09-11
forum: General Help
---

### Post by Rhys_Mahabal on 2013-09-11
I rebooted my dedicated xbmc machine the other day and I got a;

 ```

error: invalid arch-independent ELF magic.
grub rescue>
```

I usually suspend and have done for about 4 months without a full reboot. I can boot into a desktop using a live usb, although only 12.04 server and XBMCbuntu 12.10 work, 12.04, 12.10 and 13.04 live usb freeze and I'm having to force a reboot even after an hour or so. 

This is the machine I'm using;
Linux 3.5.0-22-generic
Ubuntu 12.10 - XBMCbuntu quantal
Skin: Aeon Nox
CPU: Intel Celeron G1610 2.60GHz
GPU: Enhanced Intel HD Graphics 2000/3000
RAM: 2GB
SSD: 32GB

As I'm only able to boot into a basic ubuntu desktop I don't have a lot of tools other than the CLI. 

Here are some outputs;
```

>lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0  29.8G  0 disk 
&#9500;&#9472;sda1   8:1    0  27.9G  0 part 
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   1.9G  0 part [SWAP]
sdb      8:16   1  30.5G  0 disk 
&#9492;&#9472;sdb1   8:17   1  30.5G  0 part /cdrom
loop0    7:0    0 646.7M  1 loop /rofs
loop1    7:1    0     1G  0 loop 
```

```

> df -h
Filesystem      Size  Used Avail Use% Mounted on
aufs           1008M   64M  894M   7% /
udev            949M  4.0K  949M   1% /dev
tmpfs           383M  576K  383M   1% /run
/dev/sdb1        31G   14G   18G  43% /cdrom
/dev/loop0      647M  647M     0 100% /rofs
tmpfs           957M  280K  957M   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            957M   18M  940M   2% /run/shm
none            100M     0  100M   0% /run/user
```

```

>sudo parted -l
Model: ATA V4-CT032V4SSD2 (scsi)
Disk /dev/sda: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  30.0GB  30.0GB  primary   ext4            boot
 2      30.0GB  32.0GB  2058MB  extended
 5      30.0GB  32.0GB  2058MB  logical   linux-swap(v1)


Model: PNY USB 2.0 FD (scsi)
Disk /dev/sdb: 32.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  32.7GB  32.7GB  primary  fat32        boot, lba
```

I also can't install anything new, I tried to install testdisk, however the package cannot be found, even after a sudo apt-get update. 

What should I do next?

Any help is much appreciated.

EDIT:

I found this [script ]("http://bootinfoscript.sourceforge.net/")which I thought might have something interesting that could be the cause of my problem;

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20130218
    Boot sector info:  Syslinux looks at sector 60192000 of /dev/sdb1 for 
                       its second stage. SYSLINUX is installed in the  
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /efi/BOOT/grubx64.efi 
                       /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    58,509,311    58,507,264  83 Linux
/dev/sda2          58,511,358    62,531,583     4,020,226   5 Extended
/dev/sda5          58,511,360    62,531,583     4,020,224  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 32.7 GB, 32717537280 bytes
256 heads, 36 sectors/track, 6933 cylinders, total 63901440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    63,901,439    63,901,408   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       b0e9d453-bc59-48e7-9573-44ac4e2e59bb   ext3       
/dev/sda1        8930f81d-cec6-4a78-b913-7680675d087c   ext4       
/dev/sda5        cba9a4ff-1f1f-44b5-a66f-006fe7c50d59   swap       
/dev/sdb1        3A8B-2F12                              vfat       USB20FD

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  8930f81d-cec6-4a78-b913-7680675d087c
else
  search --no-floppy --fs-uuid --set=root 8930f81d-cec6-4a78-b913-7680675d087c
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
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
set linux_gfx_mode=keep
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8930f81d-cec6-4a78-b913-7680675d087c' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  8930f81d-cec6-4a78-b913-7680675d087c
    else
      search --no-floppy --fs-uuid --set=root 8930f81d-cec6-4a78-b913-7680675d087c
    fi
    linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=8930f81d-cec6-4a78-b913-7680675d087c ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-22-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-8930f81d-cec6-4a78-b913-7680675d087c' {
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-advanced-8930f81d-cec6-4a78-b913-7680675d087c' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  8930f81d-cec6-4a78-b913-7680675d087c
        else
          search --no-floppy --fs-uuid --set=root 8930f81d-cec6-4a78-b913-7680675d087c
        fi
        echo    'Loading Linux 3.5.0-22-generic ...'
        linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=8930f81d-cec6-4a78-b913-7680675d087c ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-22-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-22-generic-recovery-8930f81d-cec6-4a78-b913-7680675d087c' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  8930f81d-cec6-4a78-b913-7680675d087c
        else
          search --no-floppy --fs-uuid --set=root 8930f81d-cec6-4a78-b913-7680675d087c
        fi
        echo    'Loading Linux 3.5.0-22-generic ...'
        linux    /boot/vmlinuz-3.5.0-22-generic root=UUID=8930f81d-cec6-4a78-b913-7680675d087c ro single nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-22-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  8930f81d-cec6-4a78-b913-7680675d087c
    else
      search --no-floppy --fs-uuid --set=root 8930f81d-cec6-4a78-b913-7680675d087c
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  8930f81d-cec6-4a78-b913-7680675d087c
    else
      search --no-floppy --fs-uuid --set=root 8930f81d-cec6-4a78-b913-7680675d087c
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=8930f81d-cec6-4a78-b913-7680675d087c /               ext4    noatime,discard,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cba9a4ff-1f1f-44b5-a66f-006fe7c50d59 none            swap    sw              0       0


192.168.1.76:/mnt/fs01/tv_shows /home/rhys/tv_shows nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.76:/mnt/fs01/movies /home/rhys/movies nfs rsize=8192,wsize=8192,timeo=14,intr
192.168.1.76:/mnt/fs01/flac_music /home/rhys/flac_music nfs rsize=8192,wsize=8192,timeo=14,intr
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-28-generic               1
               =                boot/initrd.img-3.5.0-22-generic               1
               =                boot/vmlinuz-3.5.0-22-generic                  1
               =                initrd.img                                     1
               =                vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 0
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/xbmc/Downloads/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
  No volume groups found
```

---

### Post by Rhys_Mahabal on 2013-09-14
Sorry to bump, I know there are a lot of Grub threads around, I have tried to follow a few of them, but I just need a little help on the next step?

---

