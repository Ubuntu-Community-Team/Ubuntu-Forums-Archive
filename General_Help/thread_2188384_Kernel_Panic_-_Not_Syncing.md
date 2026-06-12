---
title: "Kernel Panic - Not Syncing"
date: 2013-11-16
forum: General Help
---

### Post by mckenzie-park on 2013-11-16
Hello there,

I have Ubuntu dual-installed on a Dell Inspiron laptop alongside Windows 7. This past week, without having installed any system updates, I began to get an error message when starting up my computer. After choosing the Ubuntu partition from the grub menu I get the following message: [     0.956743] Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0). I'm able to load the Windows partition without problem and to boot from a livecd. I'm still fairly new to Ubuntu (started using about a year ago) and am not really sure where to go from here. Any help is appreciated.

---

### Post by philinux on 2013-11-17
Hi and welcome.

Run the bootinfoscript to help diagnose this.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by mckenzie-park on 2013-11-17
Ok, here are the results from running bootinfoscript:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  DreamStudio 12.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2    *        206,848    30,926,847    30,720,000   7 NTFS / exFAT / HPFS
/dev/sda3          30,926,848   166,419,751   135,492,904   7 NTFS / exFAT / HPFS
/dev/sda4         166,420,478   625,141,759   458,721,282   5 Extended
/dev/sda5         166,420,480   619,132,927   452,712,448  83 Linux
/dev/sda6         619,134,976   625,141,759     6,006,784  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DELLUTILITY
/dev/sda2        CC70378A703779F2                       ntfs       Recovery
/dev/sda3        AC7C4EC27C4E86D4                       ntfs       OS
/dev/sda5        ff3c2f2d-f1af-4ffa-8e04-6bf04b803703   ext4       
/dev/sda6        7e942e2d-3d6e-426a-9a95-4b1b73cccda4   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04.3 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== sda3/Wubi/boot/grub/grub.cfg: =========================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root AC7C4EC27C4E86D4
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ntfs
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root AC7C4EC27C4E86D4
  loopback loop0 /ubuntu/disks/root.disk
  set root=(loop0)
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
if [ ${recordfail} != 1 ]; then
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
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root AC7C4EC27C4E86D4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=AC7C4EC27C4E86D4 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root AC7C4EC27C4E86D4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 3.0.0-15-generic ...'
    linux    /boot/vmlinuz-3.0.0-15-generic root=UUID=AC7C4EC27C4E86D4 loop=/ubuntu/disks/root.disk ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-15-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root AC7C4EC27C4E86D4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=AC7C4EC27C4E86D4 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root AC7C4EC27C4E86D4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=AC7C4EC27C4E86D4 loop=/ubuntu/disks/root.disk ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root AC7C4EC27C4E86D4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=AC7C4EC27C4E86D4 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root AC7C4EC27C4E86D4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=AC7C4EC27C4E86D4 loop=/ubuntu/disks/root.disk ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
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

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============================= sda3/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/host/ubuntu/disks/swap.disk    none    swap    sw    0    0
--------------------------------------------------------------------------------

================= sda3/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic              55
               =                boot/initrd.img-3.0.0-14-generic              156
               =                boot/initrd.img-3.0.0-15-generic              58
               =                boot/vmlinuz-3.0.0-12-generic                 20
               =                boot/vmlinuz-3.0.0-14-generic                 49
               =                boot/vmlinuz-3.0.0-15-generic                 43
               =                vmlinuz                                       43
               =                vmlinuz.old                                   49

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
set default="0"
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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.8.0-29-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux    /boot/vmlinuz-3.8.0-29-lowlatency root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.8.0-29-lowlatency
}
menuentry 'Ubuntu, with Linux 3.8.0-29-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    echo    'Loading Linux 3.8.0-29-lowlatency ...'
    linux    /boot/vmlinuz-3.8.0-29-lowlatency root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.8.0-29-lowlatency
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-52-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux    /boot/vmlinuz-3.2.0-52-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-52-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-52-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    echo    'Loading Linux 3.2.0-52-generic ...'
    linux    /boot/vmlinuz-3.2.0-52-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-52-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-40-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux    /boot/vmlinuz-3.2.0-40-lowlatency root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-40-lowlatency
}
menuentry 'Ubuntu, with Linux 3.2.0-40-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    echo    'Loading Linux 3.2.0-40-lowlatency ...'
    linux    /boot/vmlinuz-3.2.0-40-lowlatency root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-40-lowlatency
}
menuentry 'Ubuntu, with Linux 3.2.0-40-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux    /boot/vmlinuz-3.2.0-40-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-40-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    echo    'Loading Linux 3.2.0-40-generic ...'
    linux    /boot/vmlinuz-3.2.0-40-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-40-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-38-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux    /boot/vmlinuz-3.2.0-38-lowlatency root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-38-lowlatency
}
menuentry 'Ubuntu, with Linux 3.2.0-38-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    echo    'Loading Linux 3.2.0-38-lowlatency ...'
    linux    /boot/vmlinuz-3.2.0-38-lowlatency root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-38-lowlatency
}
menuentry 'Ubuntu, with Linux 3.2.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux    /boot/vmlinuz-3.2.0-38-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-38-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    echo    'Loading Linux 3.2.0-38-generic ...'
    linux    /boot/vmlinuz-3.2.0-38-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-38-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux    /boot/vmlinuz-3.2.0-34-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-34-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    echo    'Loading Linux 3.2.0-34-generic ...'
    linux    /boot/vmlinuz-3.2.0-34-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-34-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-33-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux    /boot/vmlinuz-3.2.0-33-lowlatency root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-33-lowlatency
}
menuentry 'Ubuntu, with Linux 3.2.0-33-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    echo    'Loading Linux 3.2.0-33-lowlatency ...'
    linux    /boot/vmlinuz-3.2.0-33-lowlatency root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-33-lowlatency
}
menuentry 'Ubuntu, with Linux 3.2.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux    /boot/vmlinuz-3.2.0-33-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-33-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    echo    'Loading Linux 3.2.0-33-generic ...'
    linux    /boot/vmlinuz-3.2.0-33-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-33-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux    /boot/vmlinuz-3.2.0-32-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    echo    'Loading Linux 3.2.0-32-generic ...'
    linux    /boot/vmlinuz-3.2.0-32-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-32-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux    /boot/vmlinuz-3.2.0-31-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-31-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    echo    'Loading Linux 3.2.0-31-generic ...'
    linux    /boot/vmlinuz-3.2.0-31-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-31-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    echo    'Loading Linux 3.2.0-29-generic ...'
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux    /boot/vmlinuz-3.2.0-26-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    echo    'Loading Linux 3.2.0-26-generic ...'
    linux    /boot/vmlinuz-3.2.0-26-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux    /boot/vmlinuz-3.2.0-25-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    echo    'Loading Linux 3.2.0-25-generic ...'
    linux    /boot/vmlinuz-3.2.0-25-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-25-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux    /boot/vmlinuz-3.0.0-19-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.0.0-19-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    echo    'Loading Linux 3.0.0-19-generic ...'
    linux    /boot/vmlinuz-3.0.0-19-generic root=UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-19-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root ff3c2f2d-f1af-4ffa-8e04-6bf04b803703
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root CC70378A703779F2
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root AC7C4EC27C4E86D4
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
if [ -f  $prefix/custom.cfg ]; then
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ff3c2f2d-f1af-4ffa-8e04-6bf04b803703 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda6 during installation
UUID=7e942e2d-3d6e-426a-9a95-4b1b73cccda4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-19-generic               2
               =                boot/initrd.img-3.2.0-24-generic               2
               =                boot/initrd.img-3.2.0-25-generic               2
               =                boot/initrd.img-3.2.0-26-generic               2
               =                boot/initrd.img-3.2.0-29-generic               4
               =                boot/initrd.img-3.2.0-31-generic               2
               =                boot/initrd.img-3.2.0-32-generic               1
               =                boot/initrd.img-3.2.0-33-generic               1
               =                boot/initrd.img-3.2.0-33-lowlatency            3
               =                boot/initrd.img-3.2.0-34-generic               3
               =                boot/initrd.img-3.2.0-38-generic               2
               =                boot/initrd.img-3.2.0-38-lowlatency            2
               =                boot/initrd.img-3.2.0-40-generic               1
               =                boot/initrd.img-3.2.0-40-lowlatency            4
               =                boot/initrd.img-3.2.0-52-generic               2
               =                boot/initrd.img-3.8.0-29-lowlatency            3
               =                boot/vmlinuz-3.0.0-19-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  2
               =                boot/vmlinuz-3.2.0-25-generic                  1
               =                boot/vmlinuz-3.2.0-26-generic                  2
               =                boot/vmlinuz-3.2.0-29-generic                  1
               =                boot/vmlinuz-3.2.0-31-generic                  2
               =                boot/vmlinuz-3.2.0-32-generic                  1
               =                boot/vmlinuz-3.2.0-33-generic                  1
               =                boot/vmlinuz-3.2.0-33-lowlatency               1
               =                boot/vmlinuz-3.2.0-34-generic                  1
               =                boot/vmlinuz-3.2.0-38-generic                  2
               =                boot/vmlinuz-3.2.0-38-lowlatency               1
               =                boot/vmlinuz-3.2.0-40-generic                  1
               =                boot/vmlinuz-3.2.0-40-lowlatency               1
               =                boot/vmlinuz-3.2.0-52-generic                  2
               =                boot/vmlinuz-3.8.0-29-lowlatency               2
               =                vmlinuz                                        2
               =                vmlinuz.old                                    2

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

---

### Post by philinux on 2013-11-17
Is this wubi as well as a dual boot?

---

### Post by mckenzie-park on 2013-11-17
Yes, it was a windows-based install.

---

### Post by philinux on 2013-11-17
> **mckenzie-park said:**
> Yes, it was a windows-based install.

Uninstall it then from windows. It's meant for exploring ubuntu only. Better to have a proper dual boot. It's not worth the effort of sorting it out to be honest? 

Or if you're game see this. [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

