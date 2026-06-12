---
title: "unbuntu and windows dual boot problems"
date: 2013-04-10
forum: General Help
---

### Post by mark470 on 2013-04-10
Can't get windows 7 to show up on grub boot screen. Any help would be great!

See below for for some terminal commands I tried and boot info script results.

root@ophwks110:~# os-prober
/dev/sda1:Windows 7 (loader):Windows:chain
root@ophwks110:~# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-46-generic
Found kernel: /boot/vmlinuz-2.6.32-45-generic
Found kernel: /boot/vmlinuz-2.6.32-21-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done




```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on boot
    drive #1 in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdb and looks on the
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  NOTICE TO ALL USERS BLKID
                       Error_Log Log Log1 Mount_Error PT sda1 sda2 sda3 sdb1
                       Tmp_Log Trash Before using this network, users are to
                       read and agree to the Terms and Conditions of use, and
                       be aware of your obligations and restrictions as a
                       user as listed in the ISSPP's. This network is an
                       official Defence network and is to be used for
                       official Defence bussiness only. By selecting agree at
                       the bottom of this page and continuing to the login
                       screen, you agree to ALL terms and conditions set
                       forth in the ISSPP's.
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   488,488,959   488,282,112   7 NTFS / exFAT / HPFS
/dev/sda3         488,488,960   976,771,071   488,282,112   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   195,311,615   195,309,568  83 Linux
/dev/sdb2         195,318,270   976,768,064   781,449,795  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3812E08612E04B08                       ntfs       System Reserved
/dev/sda2        006486916486895C                       ntfs       
/dev/sda3        7E2A8DF52A8DAB2B                       ntfs       
/dev/sdb1        ad7df1a6-cf22-4027-9825-7c144841ac82   ext4       lindrive
/dev/sdb2        0f42555a-3597-4c0d-b130-62776c3ba2fb   ext4       lindrive2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


=========================== sdb1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=ad7df1a6-cf22-4027-9825-7c144841ac82 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ad7df1a6-cf22-4027-9825-7c144841ac82

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 10.04.4 LTS, kernel 2.6.32-46-generic
uuid        ad7df1a6-cf22-4027-9825-7c144841ac82
kernel        /boot/vmlinuz-2.6.32-46-generic root=UUID=ad7df1a6-cf22-4027-9825-7c144841ac82 ro quiet splash
initrd        /boot/initrd.img-2.6.32-46-generic
quiet

title        Ubuntu 10.04.4 LTS, kernel 2.6.32-46-generic (recovery mode)
uuid        ad7df1a6-cf22-4027-9825-7c144841ac82
kernel        /boot/vmlinuz-2.6.32-46-generic root=UUID=ad7df1a6-cf22-4027-9825-7c144841ac82 ro  single
initrd        /boot/initrd.img-2.6.32-46-generic

title        Ubuntu 10.04.4 LTS, kernel 2.6.32-45-generic
uuid        ad7df1a6-cf22-4027-9825-7c144841ac82
kernel        /boot/vmlinuz-2.6.32-45-generic root=UUID=ad7df1a6-cf22-4027-9825-7c144841ac82 ro quiet splash
initrd        /boot/initrd.img-2.6.32-45-generic
quiet

title        Ubuntu 10.04.4 LTS, kernel 2.6.32-45-generic (recovery mode)
uuid        ad7df1a6-cf22-4027-9825-7c144841ac82
kernel        /boot/vmlinuz-2.6.32-45-generic root=UUID=ad7df1a6-cf22-4027-9825-7c144841ac82 ro  single
initrd        /boot/initrd.img-2.6.32-45-generic

title        Ubuntu 10.04.4 LTS, kernel 2.6.32-21-generic
uuid        ad7df1a6-cf22-4027-9825-7c144841ac82
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=ad7df1a6-cf22-4027-9825-7c144841ac82 ro quiet splash
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        Ubuntu 10.04.4 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid        ad7df1a6-cf22-4027-9825-7c144841ac82
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=ad7df1a6-cf22-4027-9825-7c144841ac82 ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.04.4 LTS, memtest86+
uuid        ad7df1a6-cf22-4027-9825-7c144841ac82
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ad7df1a6-cf22-4027-9825-7c144841ac82
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ad7df1a6-cf22-4027-9825-7c144841ac82
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-45-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ad7df1a6-cf22-4027-9825-7c144841ac82
    linux    /boot/vmlinuz-2.6.32-45-generic root=UUID=ad7df1a6-cf22-4027-9825-7c144841ac82 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-45-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-45-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ad7df1a6-cf22-4027-9825-7c144841ac82
    echo    'Loading Linux 2.6.32-45-generic ...'
    linux    /boot/vmlinuz-2.6.32-45-generic root=UUID=ad7df1a6-cf22-4027-9825-7c144841ac82 ro single
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-45-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ad7df1a6-cf22-4027-9825-7c144841ac82
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ad7df1a6-cf22-4027-9825-7c144841ac82 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ad7df1a6-cf22-4027-9825-7c144841ac82
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ad7df1a6-cf22-4027-9825-7c144841ac82 ro single
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ad7df1a6-cf22-4027-9825-7c144841ac82
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ad7df1a6-cf22-4027-9825-7c144841ac82
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=ad7df1a6-cf22-4027-9825-7c144841ac82 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=86e6e3d2-5944-4b45-8038-ac4ff7d24b5f none            swap    sw              0       0
UUID=d7e5ae17-6825-43e4-aad7-4ed95b327bd0 /home/users/Store ext4 rw 0 0

//192.168.12.249/share /home/users/g_drive/ cifs credentials=/root/secret,rw 0 0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   6.149276733 = 6.602735616    boot/grub/grub.cfg                             2
  86.280426025 = 92.642902016   boot/grub/menu.lst                             1
  56.135856628 = 60.275417088   boot/grub/stage2                               1
  56.156913757 = 60.298027008   boot/initrd.img-2.6.32-21-generic              1
  56.164691925 = 60.306378752   boot/initrd.img-2.6.32-45-generic              1
  56.258441925 = 60.407042048   boot/initrd.img-2.6.32-46-generic              1
   0.135589600 = 0.145588224    boot/vmlinuz-2.6.32-21-generic                 1
   0.729362488 = 0.783147008    boot/vmlinuz-2.6.32-45-generic                 1
   3.383659363 = 3.633176576    boot/vmlinuz-2.6.32-46-generic                 2
  56.258441925 = 60.407042048   initrd.img                                     1
  56.164691925 = 60.306378752   initrd.img.old                                 1
   3.383659363 = 3.633176576    vmlinuz                                        2
   0.729362488 = 0.783147008    vmlinuz.old                                    1
```

---

### Post by oldfred on 2013-04-10
You have grub legacy (and grub2). But are booting with grub legacy in MBR. And os-prober is part of grub2. Grub legacy used to find XP, but rarely found Windows 7 and we had to manually edit menu.lst. One of the real advantages of grub2 is os-prober and how it finds just about any other installed system.

If you want to just add Windows 7 to menu.lst add this this before or after the auto magic area as that is the part that is always updated (like grub.cfg is in grub2).

       Your Win7 entry should be like this, note that partition numbering is different between grub legacy & grub2:

  ```
 title Windows 7 Ultimate, chainloader (on /dev/sda1)
rootnoverify (hd0,0)
savedefault
chainloader +1


```

But you should think about upgrading to grub2.

---

### Post by mark470 on 2013-04-11
Upgraded to grub2, can now dual boot. Thanks oldfred!

---

