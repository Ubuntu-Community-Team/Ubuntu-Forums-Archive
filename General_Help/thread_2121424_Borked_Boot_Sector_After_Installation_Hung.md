---
title: "Borked Boot Sector After Installation Hung"
date: 2013-03-01
forum: General Help
---

### Post by AndyOpie150 on 2013-03-01
I was trying to install Lubuntu from a CD which had the Lubuntu.iso burned to it.
It hung at the part where it creates the boot image/mbr? 
Now my Windows OS boot sector is totally borked. Tried the Boot Repair CD (all options where tried). Tried an option in Test Disk to repair boot sector (Was in the System Repair CD), but no go. Can see Windows thru Super OS 11. Gparted sees the partition, but there's a warning/question icon. It doesn't show up in the Xubuntu grub menu at all (after hung install of Lubuntu I installed Xubuntu successfully).

No WiFi right now, just slow 3G from phone. Can't respond except when low usage during off peak hours. Sometimes signal is strong enough to enable me to use Windows/Linux machine, but not very often.


Any help greatly appreciated.

---

### Post by oldfred on 2013-03-02
We need to see details.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by AndyOpie150 on 2013-03-06
Sorry for delay.

Having hard time posting Boot-Repair-Disk summary. This is the third browser on mobile device.

I'm not sure how to post this huge bit of info. Hopefully the hide tags are what is required.

```
    Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info August 2nd 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  70    87,466,053    87,465,984   7 NTFS / exFAT / HPFS
/dev/sda2          87,474,174   234,436,544   146,962,371   f W95 Extended (LBA)
/dev/sda5          87,474,176    93,976,575     6,502,400  83 Linux
/dev/sda6          93,980,313    98,092,889     4,112,577  82 Linux swap / Solaris
/dev/sda7          98,092,953   191,671,514    93,578,562  83 Linux
/dev/sda8    *    191,671,578   234,436,544    42,764,967  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        01CDE593F34C4EB0                       ntfs       
/dev/sda5        7d3928a4-c8a3-4c83-9a7c-773876d78490   ext4       
/dev/sda6                                               swap       
/dev/sda7        aae45919-94a6-4a77-995a-4837a6ffeac6   ext4       
/dev/sda8        516e92d8-ffbb-4741-b862-611a7f53d831   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sr0         /live/image              iso9660    (ro,noatime)


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
search --no-floppy --fs-uuid --set=root 7d3928a4-c8a3-4c83-9a7c-773876d78490
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 7d3928a4-c8a3-4c83-9a7c-773876d78490
  set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d3928a4-c8a3-4c83-9a7c-773876d78490
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=7d3928a4-c8a3-4c83-9a7c-773876d78490 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d3928a4-c8a3-4c83-9a7c-773876d78490
    echo    'Loading Linux 3.2.0-29-generic ...'
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=7d3928a4-c8a3-4c83-9a7c-773876d78490 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d3928a4-c8a3-4c83-9a7c-773876d78490
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7d3928a4-c8a3-4c83-9a7c-773876d78490
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-26-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root aae45919-94a6-4a77-995a-4837a6ffeac6
    linux /boot/vmlinuz-3.0.0-26-generic root=UUID=aae45919-94a6-4a77-995a-4837a6ffeac6 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-26-generic
}
menuentry "Ubuntu, with Linux 3.0.0-26-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root aae45919-94a6-4a77-995a-4837a6ffeac6
    linux /boot/vmlinuz-3.0.0-26-generic root=UUID=aae45919-94a6-4a77-995a-4837a6ffeac6 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-26-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root aae45919-94a6-4a77-995a-4837a6ffeac6
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=aae45919-94a6-4a77-995a-4837a6ffeac6 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root aae45919-94a6-4a77-995a-4837a6ffeac6
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=aae45919-94a6-4a77-995a-4837a6ffeac6 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.2.0-29-generic-pae (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 516e92d8-ffbb-4741-b862-611a7f53d831
    linux /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=516e92d8-ffbb-4741-b862-611a7f53d831 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-29-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 516e92d8-ffbb-4741-b862-611a7f53d831
    linux /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=516e92d8-ffbb-4741-b862-611a7f53d831 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-29-generic-pae
}
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
UUID=7d3928a4-c8a3-4c83-9a7c-773876d78490 /               ext4    errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/initrd.img-3.2.0-29-generic               4
            ?? = ??             boot/vmlinuz-3.2.0-29-generic                  2
            ?? = ??             initrd.img                                     4
            ?? = ??             vmlinuz                                        2

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root aae45919-94a6-4a77-995a-4837a6ffeac6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root aae45919-94a6-4a77-995a-4837a6ffeac6
  set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 3.0.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root aae45919-94a6-4a77-995a-4837a6ffeac6
    linux    /boot/vmlinuz-3.0.0-26-generic root=UUID=aae45919-94a6-4a77-995a-4837a6ffeac6 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root aae45919-94a6-4a77-995a-4837a6ffeac6
    echo    'Loading Linux 3.0.0-26-generic ...'
    linux    /boot/vmlinuz-3.0.0-26-generic root=UUID=aae45919-94a6-4a77-995a-4837a6ffeac6 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-26-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root aae45919-94a6-4a77-995a-4837a6ffeac6
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=aae45919-94a6-4a77-995a-4837a6ffeac6 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root aae45919-94a6-4a77-995a-4837a6ffeac6
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=aae45919-94a6-4a77-995a-4837a6ffeac6 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root aae45919-94a6-4a77-995a-4837a6ffeac6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root aae45919-94a6-4a77-995a-4837a6ffeac6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.2.0-29-generic-pae (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 516e92d8-ffbb-4741-b862-611a7f53d831
    linux /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=516e92d8-ffbb-4741-b862-611a7f53d831 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-29-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 516e92d8-ffbb-4741-b862-611a7f53d831
    linux /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=516e92d8-ffbb-4741-b862-611a7f53d831 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-29-generic-pae
}
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
# / was on /dev/sda6 during installation
UUID=aae45919-94a6-4a77-995a-4837a6ffeac6 /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/initrd.img-3.0.0-12-generic               3
            ?? = ??             boot/initrd.img-3.0.0-26-generic               2
            ?? = ??             boot/vmlinuz-3.0.0-12-generic                  1
            ?? = ??             boot/vmlinuz-3.0.0-26-generic                  2
            ?? = ??             initrd.img.old                                 3
            ?? = ??             vmlinuz                                        2
            ?? = ??             vmlinuz.old                                    1

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root 516e92d8-ffbb-4741-b862-611a7f53d831
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root 516e92d8-ffbb-4741-b862-611a7f53d831
  set locale_dir=($root)/boot/grub/locale
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 516e92d8-ffbb-4741-b862-611a7f53d831
    linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=516e92d8-ffbb-4741-b862-611a7f53d831 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 516e92d8-ffbb-4741-b862-611a7f53d831
    echo    'Loading Linux 3.2.0-29-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=516e92d8-ffbb-4741-b862-611a7f53d831 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 516e92d8-ffbb-4741-b862-611a7f53d831
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 516e92d8-ffbb-4741-b862-611a7f53d831
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-26-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root aae45919-94a6-4a77-995a-4837a6ffeac6
    linux /boot/vmlinuz-3.0.0-26-generic root=UUID=aae45919-94a6-4a77-995a-4837a6ffeac6 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-26-generic
}
menuentry "Ubuntu, with Linux 3.0.0-26-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root aae45919-94a6-4a77-995a-4837a6ffeac6
    linux /boot/vmlinuz-3.0.0-26-generic root=UUID=aae45919-94a6-4a77-995a-4837a6ffeac6 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-26-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root aae45919-94a6-4a77-995a-4837a6ffeac6
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=aae45919-94a6-4a77-995a-4837a6ffeac6 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root aae45919-94a6-4a77-995a-4837a6ffeac6
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=aae45919-94a6-4a77-995a-4837a6ffeac6 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
}
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=516e92d8-ffbb-4741-b862-611a7f53d831 /               ext4    errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/initrd.img-3.2.0-29-generic-pae           3
            ?? = ??             boot/vmlinuz-3.2.0-29-generic-pae              2
            ?? = ??             initrd.img                                     3
            ?? = ??             vmlinuz                                        2

=============================== StdErr Messages: ===============================

File descriptor 7 (pipe:[11715]) leaked on lvscan invocation. Parent PID 20199: bash
File descriptor 8 (pipe:[11715]) leaked on lvscan invocation. Parent PID 20199: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-06-29__21h10 ===================
boot-repair version : 3.18-0ppa52~lucid
boot-sav version : 3.192-0ppa24~lucid
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
boot-sav-nonfree version : 3.18-0ppa14~lucid
Please connect internet. Then close this window.
/usr/share/boot-sav/gui-update.sh: line 328: add-apt-repository: command not found
/usr/share/boot-sav/gui-update.sh: line 328: add-apt-repository: command not found
deb [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu) lucid main
/usr/share/boot-sav/gui-update.sh: line 328: add-apt-repository: command not found
/usr/share/boot-sav/gui-update.sh: line 328: add-apt-repository: command not found
deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) lucid main
W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze/Release.gpg](http://cdn.debian.net/debian/dists/squeeze/Release.gpg)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en.bz2](http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en_US.bz2](http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en_US.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/Release.gpg](http://security.debian.org/dists/squeeze/updates/Release.gpg)  Could not resolve 'security.debian.org'

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en.bz2](http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en.bz2)  Could not resolve 'security.debian.org'

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en_US.bz2](http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.debian.org'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze-updates/Release.gpg](http://cdn.debian.net/debian/dists/squeeze-updates/Release.gpg)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en.bz2](http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en_US.bz2](http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.


0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 55 not upgraded.
WARNING: The following packages cannot be authenticated!
os-uninstaller
Err [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/) lucid/main os-uninstaller all 3.18-0ppa12~lucid
Could not resolve 'ppa.launchpad.net'
Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/pool/main/o/os-uninstaller/os-uninstaller_3.18-0ppa12~lucid_all.deb](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/pool/main/o/os-uninstaller/os-uninstaller_3.18-0ppa12~lucid_all.deb)  Could not resolve 'ppa.launchpad.net'
E: Some files failed to download

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 55 not upgraded.
WARNING: The following packages cannot be authenticated!
boot-repair
Err [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) lucid/main boot-repair all 3.18-0ppa52~lucid
Could not resolve 'ppa.launchpad.net'
Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/pool/main/b/boot-repair/boot-repair_3.18-0ppa52~lucid_all.deb](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/pool/main/b/boot-repair/boot-repair_3.18-0ppa52~lucid_all.deb)  Could not resolve 'ppa.launchpad.net'
E: Some files failed to download
File descriptor 7 (pipe:[11715]) leaked on lvs invocation. Parent PID 11671: /bin/sh
File descriptor 8 (pipe:[11715]) leaked on lvs invocation. Parent PID 11671: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 18.07.2012, squeeze, Debian, i686)
CPU op-mode(s):        32-bit

=================== os-prober:
/dev/sda5:Ubuntu 12.04.1 LTS (12.04):Ubuntu:linux
/dev/sda7:Ubuntu 11.10 (11.10):Ubuntu1:linux
/dev/sda8:Ubuntu 12.04.1 LTS (12.04):Ubuntu2:linux

=================== blkid:
/dev/sda1: UUID="01CDE593F34C4EB0" TYPE="ntfs"
/dev/sda5: UUID="7d3928a4-c8a3-4c83-9a7c-773876d78490" TYPE="ext4"
/dev/sda6: TYPE="swap"
/dev/sda7: UUID="aae45919-94a6-4a77-995a-4837a6ffeac6" TYPE="ext4"
/dev/sda8: UUID="516e92d8-ffbb-4741-b862-611a7f53d831" TYPE="ext4"
/dev/loop0: TYPE="squashfs"


1 disks with OS, 3 OS : 3 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== sda5/etc/default/grub :

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





=================== sda5/etc/grub.d/ :
drwxr-xr-x  2 root root        4096 Aug 17  2012 grub.d
total 56
-rwxr-xr-x 1 root root 6715 May 17  2012 00_header
-rwxr-xr-x 1 root root 5522 May 17  2012 05_debian_theme
-rwxr-xr-x 1 root root 7407 May 17  2012 10_linux
-rwxr-xr-x 1 root root 6335 May 17  2012 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 May 17  2012 30_os-prober
-rwxr-xr-x 1 root root  214 May 17  2012 40_custom
-rwxr-xr-x 1 root root   95 May 17  2012 41_custom
-rw-r--r-- 1 root root  483 May 17  2012 README





=================== sda7/etc/default/grub :

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





=================== sda7/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Oct 12  2011 grub.d
total 56
-rwxr-xr-x 1 root root 6698 Oct  1  2011 00_header
-rwxr-xr-x 1 root root 5522 Oct  1  2011 05_debian_theme
-rwxr-xr-x 1 root root 7269 Oct  1  2011 10_linux
-rwxr-xr-x 1 root root 6344 Oct  1  2011 20_linux_xen
-rwxr-xr-x 1 root root 1588 May  2  2011 20_memtest86+
-rwxr-xr-x 1 root root 7545 Oct  1  2011 30_os-prober
-rwxr-xr-x 1 root root  214 Oct  1  2011 40_custom
-rwxr-xr-x 1 root root   95 Oct  1  2011 41_custom
-rw-r--r-- 1 root root  483 Oct  1  2011 README





=================== sda8/etc/default/grub :

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





=================== sda8/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Aug 17  2012 grub.d
total 56
-rwxr-xr-x 1 root root 6715 May 17  2012 00_header
-rwxr-xr-x 1 root root 5522 May 17  2012 05_debian_theme
-rwxr-xr-x 1 root root 7407 May 17  2012 10_linux
-rwxr-xr-x 1 root root 6335 May 17  2012 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 May 17  2012 30_os-prober
-rwxr-xr-x 1 root root  214 May 17  2012 40_custom
-rwxr-xr-x 1 root root   95 May 17  2012 41_custom
-rw-r--r-- 1 root root  483 May 17  2012 README




=================== dmesg | grep EFI :
This live-session is not EFI-compatible.




=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda5    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda5.
sda7    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda7.
sda8    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda8.

sda    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    70 sectors * 512 bytes

=================== parted -l:

Model: ATA ST3120022A (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      35.8kB  44.8GB  44.8GB  primary   ntfs
2      44.8GB  120GB   75.2GB  extended                  lba
5      44.8GB  48.1GB  3329MB  logical   ext4
6      48.1GB  50.2GB  2106MB  logical   linux-swap(v1)
7      50.2GB  98.1GB  47.9GB  logical   ext4
8      98.1GB  120GB   21.9GB  logical   ext4            boot



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


=================== mount:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sr0 on /live/image type iso9660 (ro,noatime)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type ext4 (rw)
/dev/sda7 on /mnt/boot-sav/sda7 type ext4 (rw)
/dev/sda8 on /mnt/boot-sav/sda8 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda5 sda6 sda7 sda8 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  agpgart block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dvd dvdrw fd full fuse fw0 hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hpet initctl input kmsg log MAKEDEV md mem net network_latency network_throughput null port ppp psaux ptmx pts radio0 random rfkill rtc rtc0 scd0 sda sda1 sda2 sda5 sda6 sda7 sda8 sg0 sg1 shm snapshot snd sndstat sr0 stderr stdin stdout urandom usb v4l vbi0 vga_arbiter video0 video24 video32 xconsole zero
ls /dev/md:
ls /mnt/boot-sav/sda1: WINDOWS SDK RECYCLER QtADB-cwm_edition Files Program plop Netgear MSOCache FrameworkFlasher-1.1.4 Downloads Settings and Documents Config.Msi boot-sav APK-Multi-Tool

=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    490M  7.5M  483M   2% /
tmpfs        tmpfs    490M     0  490M   0% /lib/init/rw
udev         tmpfs    485M  212K  485M   1% /dev
tmpfs        tmpfs    490M     0  490M   0% /dev/shm
/dev/sr0   iso9660    347M  347M     0 100% /live/image
tmpfs        tmpfs    490M  7.5M  483M   2% /live/cow
tmpfs        tmpfs    490M     0  490M   0% /live
tmpfs        tmpfs    490M  104K  490M   1% /tmp
/dev/sda1  fuseblk     42G  4.6G   38G  11% /mnt/boot-sav/sda1
/dev/sda5     ext4    3.1G  1.9G  1.1G  65% /mnt/boot-sav/sda5
/dev/sda7     ext4     44G   25G   18G  59% /mnt/boot-sav/sda7
/dev/sda8     ext4     21G  2.2G   17G  12% /mnt/boot-sav/sda8

=================== fdisk -l:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7fd5b960

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5445    43732992    7  HPFS/NTFS
/dev/sda2            5446       14593    73481185+   f  W95 Ext'd (LBA)
/dev/sda5            5446        5850     3251200   83  Linux
/dev/sda6            5851        6106     2056288+  82  Linux swap / Solaris
/dev/sda7            6107       11931    46789281   83  Linux
/dev/sda8   *       11932       14593    21382483+  83  Linux



=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sda5 into the MBR of sda.
The boot flag will be placed on sda8.
Additional repair will be performed: unhide-bootmenu-10s


parted /dev/sda set 8 boot on

                                                                          
Information: You may need to update /etc/fstab.

mount: special device /run does not exist

Reinstall the GRUB of sda5 into the MBR of sda
grub-install (GRUB) 1.99-21ubuntu3.1
grub-install --recheck /dev/sda: Installation finished. No error reported.
exit code of grub-install /dev/sda:0

chroot /mnt/boot-sav/sda5 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.10 (11.10) on /dev/sda7
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sda8
umount: /mnt/boot-sav/sda5/run: not mounted
Unhide GRUB boot menu in sda5/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.

Please connect internet. Then close this window.
 
```
Firefox seems to have gotten it done. Good thing they lowered the CPU Max speed requirements or I couldn't have used it

---

### Post by oldfred on 2013-03-07
Better to use hard wired Ethernet connection if wi-fi issues. And then you can post just the link as Boot-Repair auto copies to pastebin.

Your sda1, NTFS partition does not show any Windows boot files. Sometimes script missing them, but it does not look like a boot partition. It did mount it and sees PBR - partition boot sector has ntldr and correct end code, but still could be wrong. Have you tried chkdsk?

You are not showing any of these, which script usually finds & posts:
 Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by AndyOpie150 on 2013-03-07
No way to get a hardwired connection. I only have data connection from phone. Will try to use phones hotspot when 3G signal isn't so bad. Might be a couple of nights before the signals strong enough to allow it though.
If it was a laptop it wouldn't be a problem I could just tote it to McDonald's, but It's a desktop.
Could put it into a cart and wheel it over to McDonald's. Wouldn't that be a hoot. Lol.

How would I utilize chkdsk command thru Ubuntu or Xubuntu? Isn't that a Windows command? Sorry for confusion. 


PS: To cariboo907. Thanks for fixing the tags.

---

### Post by AndyOpie150 on 2013-03-07
Duh! Ok. I see what you mean about the wireless. I have my drivers and some of the packages for ndiswraper (7 in all), but I wasn't thinking I might need a huge amount of dependencies installed. Then there is the fact I put the Boot-Repair.iso onto a CD-R instead of a CD-RW. Double Duh!

 Will have to wait until my residence changes to one that has a WiFi so I can hook straight up to the router. Then run the Boot-Repair-Disk. Might go ahead and put the .iso onto a CD-RW anyway. Then try to figure out all the packages/dependencies that are needed and save them to my flash drive and try again. Will keep them in case I'm ever in the same spot again.

I hope I don't need more than 20 packages, as thats a lot of typing in a command line. This might take a considerable amount of time as well to download packages onto phones sd card and transfer to flash drive. My 3G is terrible. Might only be able to download a package a day.

Thanks for your help and patience oldfred.

---

### Post by oldfred on 2013-03-08
Chkdsk is a Windows only command. And it is the only way to repair corrupted NTFS partitions. Linux runs its fsck every 40 or 60 reboots, but Windows seems to wait until broken and then you have to manually run chkdsk. Windows also has to run chkdsk on any resize of a NTFS partition.

Some ways to off line or server download once for install.
 Offline Updates:
[https://launchpad.net/keryx/+download](https://launchpad.net/keryx/+download)
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
apt-cache search foo
[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)
Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

---

### Post by AndyOpie150 on 2013-03-09
Thanks. 
Processing info, see what I can do.

Edit: Wow, that's some super info you linked me to. 
Double Thanks!

---

### Post by AndyOpie150 on 2013-03-26
Managed to get Hirens Boot CD.iso burned to CD.
It had a mini XP OS that had chkdsk utility. It added missing files. 
Used Boot Repair Disk CD to repair grub.
After reboot Windows partition was back in grub menu and booted up with no problems.

Thanks for all the great info oldfred, and for always being their when I really needed the help.

Now on to a bigger challenge.... BSD.

Edit: Sidetracked by Knoppix

---

