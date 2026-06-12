---
title: "Trouble Restoring Boot Partition"
date: 2017-12-04
forum: General Help
---

### Post by webmanoffesto on 2017-12-04
I now have a HP ProBook and there is Linux on two partions. In the past I  had Linux 7. I later partitioned the HD the way I wanted and created  root, home, and swap partitions and installed Ubuntu Gnome 16.
So that leaves me with

```
$ sudo fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1808337985   904167969   83  Linux  [925GB, that's Linux 7]
/dev/sda2      1808338942  1953523711    72592385    5  Extended
/dev/sda5      1808338944  1847399490    19530273+  83  Linux [20 GB, that's Ubuntu 16]
/dev/sda6      1847402496  1953523711    53060608   82  Linux swap / Solaris [54GB] 
```

I believe the * tells me that sda1 is now my boot partition. But it is sda5 which I want to be the boot partition, if it will successfully boot me into Ubuntu 16. 

After repair attempts using programs such as Boot Repair Disk and Super Grub 2 I can reboot and get to a Gnu Grub v2.02 screen.
[[IMG]http://en.zimagez.com/avatar/gnugrubcroppedv02n01v01.png[/IMG]]("http://en.zimagez.com/zimage/gnugrubcroppedv02n01v01.php")
I'm able to boot into Linux 7 (sda1). But if I select Ubuntu (which is on sda5) then I get to the

Failed to execute /init (error -0)
... end kernel panic - not syncing: No working init found.
[[IMG]http://en.zimagez.com/avatar/kernelpanicn01v01.png[/IMG]]("http://en.zimagez.com/zimage/kernelpanicn01v01.php")

I wasn't able to open the init.txt file on my computer but I found this online
[https://www.mjmwired.net/kernel/Documentation/init.txt](https://www.mjmwired.net/kernel/Documentation/init.txt)

This problem leaves me running "Debian GNU/Linux 7 (wheezy)".

---

### Post by yancek on 2017-12-04
Since you already have the boot repair software I would suggest you run it again but this time, instead of trying to make repairs, you select the option to Create BootInfo Summary and post the link to the output here so we have some details.

Also, has this ever worked?  You indicate you have Debian 7 (sda1) plus an Ubuntu root partition, home partition and swap partition.  Your fdisk output only shows Debian, the Ubuntu system partition and a swap partition??

---

### Post by webmanoffesto on 2017-12-04
> **yancek said:**
> Since you already have the boot repair software I  would suggest you run it again but this time, instead of trying to make  repairs, you select the option to Create BootInfo Summary and post the  link to the output here so we have some details.

Right now nothing is working for me and I haven't been able to get my Flash Drive Multiboot working correctly, so I haven't been able to run anything which can get me that Boot Info Summary.

> **yancek said:**
> Has this ever worked?  You indicate you have Debian 7 (sda1) plus  an Ubuntu root partition, home partition and swap partition.  Your fdisk  output only shows Debian, the Ubuntu system partition and a swap  partition??

My partitions:
/dev/sda1 * 2048 1808337985 904167969 83 Linux [925GB, that's Linux 7]
The newer install, Ubuntu 16 Gnome uses this as the Home folder.
I recently discovered that this can boot the the older Linux install, Debian Linux 7. That did work correctly for a while. And it puts Home in the same partition. 
That explains why there are two "Documents" folders.
"/home/tom/Documents" contains older "Home" files
and
"/tom/Documents" which seems to have all the files that are in "/home/tom/Documents" plus newer files.
I'm now running using this laptop and this partition to run Linux 7 because the Ubuntu 16 partition won't correctly boot.

and
/dev/sda5      1808338944  1847399490    19530273+  83  Linux [20 GB, that's Ubuntu 16]
This is a newer partition. 
Is where the Ubuntu 16 install was. That is my most recent install. That worked correctly for a few months.

And, of course, I created a swap partition
/dev/sda6      1847402496  1953523711    53060608   82  Linux swap / Solaris [54GB]

I'm not sure what the below partition is for.
/dev/sda2      1808338942  1953523711    72592385    5  Extended

---

### Post by ajgreeny on 2017-12-04
An extended partition is simply a wrapper which contains logical partitions which in your case are sda5 (Ubuntu 16.##) and sda6 (swap) and it means you must be using MBR/BIOS not UEFI.

When you installed Ubuntu, grub from that would normally take control of the boot process away from Debian 7.11 which is also on the machine unless in the Ubuntu installation process you used the "Something Else" option and asked for grub to be installed somewhere other than the root of the first disk, ie /dev/sda, not one of the partitions such as /dev/sda1, which might explain your difficulty if it was to a partition.

The output of the Boot-info script from Boot-Repair in my signature would be very useful and without that information it is not easy to know what else to suggest at this stage.  Maybe the boot info script will run from Debian, assuming you can still boot to that; it is simply a script, not a package which needs installing, so see if you can run it from your Debian 7.11.

---

### Post by webmanoffesto on 2017-12-05
> **ajgreeny said:**
> The output of the Boot-info script 

I managed to get this Boot Info Script running. I hope it has some useful information.

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 88 for .

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Debian GNU/Linux 7
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,808,337,985 1,808,335,938  83 Linux
/dev/sda2       1,808,338,942 1,953,523,711   145,184,770   5 Extended
/dev/sda5       1,808,338,944 1,847,399,490    39,060,547  83 Linux
/dev/sda6       1,847,402,496 1,953,523,711   106,121,216  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        32730290-3726-43d4-b7c0-0d0fe62946c8   ext4       
/dev/sda5        fed80f39-139e-4fc2-8767-3feaa5e98d86   ext4       
/dev/sda6        4241ce6d-a454-48ac-8e60-a6cba2023f05   swap       
/dev/sr0         2016-07-20-12-16-02-00                 iso9660    Lubuntu 16.04.1 LTS amd64
/dev/zram0       dd307188-0f3b-4913-8b67-334c005ba199   swap       
/dev/zram1       a7a3482d-a748-4663-b727-0ef854911863   swap       
/dev/zram2       28ea4aef-4314-4518-a11b-3b5f414fce94   swap       
/dev/zram3       076f96c8-d64a-4ad7-af58-5025352139ba   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 32730290-3726-43d4-b7c0-0d0fe62946c8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 32730290-3726-43d4-b7c0-0d0fe62946c8
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
set timeout=10
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 32730290-3726-43d4-b7c0-0d0fe62946c8
insmod png
if background_image /usr/share/images/desktop-base/joy-grub.png; then
  set color_normal=white/black
  set color_highlight=black/white
else
  set menu_color_normal=cyan/blue
  set menu_color_highlight=white/blue
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Debian GNU/Linux, with Linux 3.4-9-rtai-686-pae' --class debian --class gnu-linux --class gnu --class os {
    load_video
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 32730290-3726-43d4-b7c0-0d0fe62946c8
    echo    'Loading Linux 3.4-9-rtai-686-pae ...'
    linux    /boot/vmlinuz-3.4-9-rtai-686-pae root=UUID=32730290-3726-43d4-b7c0-0d0fe62946c8 ro initrd=/install/gtk/initrd.gz lapic quiet rootdelay=5
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.4-9-rtai-686-pae
}
menuentry 'Debian GNU/Linux, with Linux 3.4-9-rtai-686-pae (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
    load_video
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 32730290-3726-43d4-b7c0-0d0fe62946c8
    echo    'Loading Linux 3.4-9-rtai-686-pae ...'
    linux    /boot/vmlinuz-3.4-9-rtai-686-pae root=UUID=32730290-3726-43d4-b7c0-0d0fe62946c8 ro single initrd=/install/gtk/initrd.gz
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.4-9-rtai-686-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 32730290-3726-43d4-b7c0-0d0fe62946c8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 32730290-3726-43d4-b7c0-0d0fe62946c8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
menuentry "Memory test (memtest86+, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 32730290-3726-43d4-b7c0-0d0fe62946c8
    multiboot    /boot/memtest86+_multiboot.bin
}
menuentry "Memory test (memtest86+, serial console 115200, experimental multiboot)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 32730290-3726-43d4-b7c0-0d0fe62946c8
    multiboot    /boot/memtest86+_multiboot.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
UUID=32730290-3726-43d4-b7c0-0d0fe62946c8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=6ba69c54-9f95-4685-9f0d-a98c9830cc64 none            swap    sw              0       0
UUID=4241ce6d-a454-48ac-8e60-a6cba2023f05 none            swap    sw              0       0
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


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
set root='hd1,msdos5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd1,msdos5'  fed80f39-139e-4fc2-8767-3feaa5e98d86
else
  search --no-floppy --fs-uuid --set=root fed80f39-139e-4fc2-8767-3feaa5e98d86
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
if background_color 45,51,53; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-fed80f39-139e-4fc2-8767-3feaa5e98d86' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd1,msdos5'  fed80f39-139e-4fc2-8767-3feaa5e98d86
    else
      search --no-floppy --fs-uuid --set=root fed80f39-139e-4fc2-8767-3feaa5e98d86
    fi
    linux    /boot/vmlinuz-4.8.0-59-lowlatency root=UUID=fed80f39-139e-4fc2-8767-3feaa5e98d86 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.8.0-59-lowlatency
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-fed80f39-139e-4fc2-8767-3feaa5e98d86' {
    menuentry 'Ubuntu, with Linux 4.8.0-59-lowlatency' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-59-lowlatency-advanced-fed80f39-139e-4fc2-8767-3feaa5e98d86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd1,msdos5'  fed80f39-139e-4fc2-8767-3feaa5e98d86
        else
          search --no-floppy --fs-uuid --set=root fed80f39-139e-4fc2-8767-3feaa5e98d86
        fi
        echo    'Loading Linux 4.8.0-59-lowlatency ...'
        linux    /boot/vmlinuz-4.8.0-59-lowlatency root=UUID=fed80f39-139e-4fc2-8767-3feaa5e98d86 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-59-lowlatency
    }
    menuentry 'Ubuntu, with Linux 4.8.0-59-lowlatency (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-59-lowlatency-recovery-fed80f39-139e-4fc2-8767-3feaa5e98d86' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd1,msdos5'  fed80f39-139e-4fc2-8767-3feaa5e98d86
        else
          search --no-floppy --fs-uuid --set=root fed80f39-139e-4fc2-8767-3feaa5e98d86
        fi
        echo    'Loading Linux 4.8.0-59-lowlatency ...'
        linux    /boot/vmlinuz-4.8.0-59-lowlatency root=UUID=fed80f39-139e-4fc2-8767-3feaa5e98d86 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-59-lowlatency
    }
    menuentry 'Ubuntu, with Linux 4.8.0-59-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-59-generic-advanced-fed80f39-139e-4fc2-8767-3feaa5e98d86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd1,msdos5'  fed80f39-139e-4fc2-8767-3feaa5e98d86
        else
          search --no-floppy --fs-uuid --set=root fed80f39-139e-4fc2-8767-3feaa5e98d86
        fi
        echo    'Loading Linux 4.8.0-59-generic ...'
        linux    /boot/vmlinuz-4.8.0-59-generic root=UUID=fed80f39-139e-4fc2-8767-3feaa5e98d86 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-59-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-59-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-59-generic-recovery-fed80f39-139e-4fc2-8767-3feaa5e98d86' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd1,msdos5'  fed80f39-139e-4fc2-8767-3feaa5e98d86
        else
          search --no-floppy --fs-uuid --set=root fed80f39-139e-4fc2-8767-3feaa5e98d86
        fi
        echo    'Loading Linux 4.8.0-59-generic ...'
        linux    /boot/vmlinuz-4.8.0-59-generic root=UUID=fed80f39-139e-4fc2-8767-3feaa5e98d86 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-59-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-58-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-58-generic-advanced-fed80f39-139e-4fc2-8767-3feaa5e98d86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd1,msdos5'  fed80f39-139e-4fc2-8767-3feaa5e98d86
        else
          search --no-floppy --fs-uuid --set=root fed80f39-139e-4fc2-8767-3feaa5e98d86
        fi
        echo    'Loading Linux 4.8.0-58-generic ...'
        linux    /boot/vmlinuz-4.8.0-58-generic root=UUID=fed80f39-139e-4fc2-8767-3feaa5e98d86 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-58-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-58-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-58-generic-recovery-fed80f39-139e-4fc2-8767-3feaa5e98d86' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd1,msdos5'  fed80f39-139e-4fc2-8767-3feaa5e98d86
        else
          search --no-floppy --fs-uuid --set=root fed80f39-139e-4fc2-8767-3feaa5e98d86
        fi
        echo    'Loading Linux 4.8.0-58-generic ...'
        linux    /boot/vmlinuz-4.8.0-58-generic root=UUID=fed80f39-139e-4fc2-8767-3feaa5e98d86 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-58-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-56-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-56-generic-advanced-fed80f39-139e-4fc2-8767-3feaa5e98d86' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd1,msdos5'  fed80f39-139e-4fc2-8767-3feaa5e98d86
        else
          search --no-floppy --fs-uuid --set=root fed80f39-139e-4fc2-8767-3feaa5e98d86
        fi
        echo    'Loading Linux 4.8.0-56-generic ...'
        linux    /boot/vmlinuz-4.8.0-56-generic root=UUID=fed80f39-139e-4fc2-8767-3feaa5e98d86 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-56-generic
    }
    menuentry 'Ubuntu, with Linux 4.8.0-56-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-56-generic-recovery-fed80f39-139e-4fc2-8767-3feaa5e98d86' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos5'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd1,msdos5'  fed80f39-139e-4fc2-8767-3feaa5e98d86
        else
          search --no-floppy --fs-uuid --set=root fed80f39-139e-4fc2-8767-3feaa5e98d86
        fi
        echo    'Loading Linux 4.8.0-56-generic ...'
        linux    /boot/vmlinuz-4.8.0-56-generic root=UUID=fed80f39-139e-4fc2-8767-3feaa5e98d86 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-56-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd1,msdos5'  fed80f39-139e-4fc2-8767-3feaa5e98d86
    else
      search --no-floppy --fs-uuid --set=root fed80f39-139e-4fc2-8767-3feaa5e98d86
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos5'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos5 --hint-efi=hd0,msdos5 --hint-baremetal=ahci0,msdos5 --hint='hd1,msdos5'  fed80f39-139e-4fc2-8767-3feaa5e98d86
    else
      search --no-floppy --fs-uuid --set=root fed80f39-139e-4fc2-8767-3feaa5e98d86
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Debian GNU/Linux (7.11) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-32730290-3726-43d4-b7c0-0d0fe62946c8' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd1,msdos1'  32730290-3726-43d4-b7c0-0d0fe62946c8
    else
      search --no-floppy --fs-uuid --set=root 32730290-3726-43d4-b7c0-0d0fe62946c8
    fi
    linux /boot/vmlinuz-3.4-9-rtai-686-pae root=UUID=32730290-3726-43d4-b7c0-0d0fe62946c8 ro initrd=/install/gtk/initrd.gz lapic quiet rootdelay=5
    initrd /boot/initrd.img-3.4-9-rtai-686-pae
}
submenu 'Advanced options for Debian GNU/Linux (7.11) (on /dev/sda1)' $menuentry_id_option 'osprober-gnulinux-advanced-32730290-3726-43d4-b7c0-0d0fe62946c8' {
    menuentry 'Debian GNU/Linux, with Linux 3.4-9-rtai-686-pae (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.4-9-rtai-686-pae--32730290-3726-43d4-b7c0-0d0fe62946c8' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd1,msdos1'  32730290-3726-43d4-b7c0-0d0fe62946c8
        else
          search --no-floppy --fs-uuid --set=root 32730290-3726-43d4-b7c0-0d0fe62946c8
        fi
        linux /boot/vmlinuz-3.4-9-rtai-686-pae root=UUID=32730290-3726-43d4-b7c0-0d0fe62946c8 ro initrd=/install/gtk/initrd.gz lapic quiet rootdelay=5
        initrd /boot/initrd.img-3.4-9-rtai-686-pae
    }
    menuentry 'Debian GNU/Linux, with Linux 3.4-9-rtai-686-pae (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.4-9-rtai-686-pae-root=UUID=32730290-3726-43d4-b7c0-0d0fe62946c8 ro single initrd=/install/gtk/initrd.gz-32730290-3726-43d4-b7c0-0d0fe62946c8' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd1,msdos1'  32730290-3726-43d4-b7c0-0d0fe62946c8
        else
          search --no-floppy --fs-uuid --set=root 32730290-3726-43d4-b7c0-0d0fe62946c8
        fi
        linux /boot/vmlinuz-3.4-9-rtai-686-pae root=UUID=32730290-3726-43d4-b7c0-0d0fe62946c8 ro single initrd=/install/gtk/initrd.gz
        initrd /boot/initrd.img-3.4-9-rtai-686-pae
    }
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=fed80f39-139e-4fc2-8767-3feaa5e98d86 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=32730290-3726-43d4-b7c0-0d0fe62946c8 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=4241ce6d-a454-48ac-8e60-a6cba2023f05 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  fe fe fe fe fe fe fe fe  fe fe fe fe fe fe fe fe  |................|
*
000001b0  fe fe fe fe fe fe fe fe  fe fe fe fe fe fe 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 43 04 54 02 00 fe  |..........C.T...|
000001d0  ff ff 05 fe ff ff 45 04  54 02 bd 53 53 06 00 00  |......E.T..SS...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-TArFpb0S/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-TArFpb0S/Tmp_Log: No such file or directory


```

---

### Post by webmanoffesto on 2017-12-05
Bump.

---

### Post by oldfred on 2017-12-05
The * is only used by Windows to know which is boot partition. It is not used by grub. But a few BIOS require a boot flag (*), so we still suggest you have one.
Grub in MBR and sector after MBR determines boot partition.

You confused things by reusing sda1 as /home in second install without reformatting when it had the Debian(?) install still in it. So it has both /home from Ubuntu and full install of Debian. Not sure if then any conflicts, but not the normal way to do things.

---

### Post by webmanoffesto on 2017-12-05
Okay, I guess I have to reinstall, so I can get back to work.

I don't feel like resizing partitions, and I'm willing to keep the swap the same, even if it's not necessary.

I boot Ubuntu 16 Gnome from a Flash drive. I think I decline Ubuntu's  offer to unmount /dev/sdb, because I think that could put Grub on my  Flash drive, which I don't want.

Where do I put Grub? Do I put it in "/dev/sda5 Ubuntu 16.10"? 
[[IMG]http://i1232.photobucket.com/albums/ff365/webmanoffesto/th_Reinstall.Where.to.Put.Bootloader.png[/IMG]](http://s1232.photobucket.com/user/webmanoffesto/media/Reinstall.Where.to.Put.Bootloader.png.html)

---

### Post by oldfred on 2017-12-05
You never (almost) install grub to a partition.
Grub with BIOS must be in MBR to boot Ubuntu. Only if you have another install's grub in MBR may you install grub to partition as a throw away or just not install grub, but you have to use command line and ubiquity -bcommand.

Install grub to sda.

---

