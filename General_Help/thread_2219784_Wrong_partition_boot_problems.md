---
title: "Wrong partition boot problems"
date: 2014-04-25
forum: General Help
---

### Post by aeleonas on 2014-04-25
I'm reluctantly posting this as I havn't had any luck following solutions to others similar issues.
I'm on 12.04 lts and had to move and delete an old windows recovery partition. 
I was getting the "error: no such partition/ GRUB rescue>" prompt
I followed the "How to Repair, Restore, or Reinstall Grub 2 with a Ubuntu Live CD or USB" tutorial, 
but I ran into an error when trying ```
sudo grub-install /dev/sda
``` that referenced one of the now non-existant partitions sda5.
I ran the bootinfoscript I don't know if it helps, but here are my results.txt:
```


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 55114120 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive.
    Operating System:  Ubuntu 12.04.4 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120131
    Boot sector info:  Syslinux looks at sector 6936776 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    58,595,327    58,593,280  83 Linux
/dev/sda2          58,595,328    68,358,127     9,762,800  82 Linux swap / Solaris
/dev/sda3          68,358,144   625,141,759   556,783,616  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8032 MB, 8032092160 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    15,687,679    15,685,632   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       c0f80c87-7f27-40d7-a575-44387bd4f0ab   ext3       
/dev/sda1        e6b8a174-fa30-483a-9b81-26f51f314eb1   ext4       
/dev/sda2        b5a71846-a80e-4fc7-87e9-fcf6d97fdbe8   swap       
/dev/sda3        da84860c-f0a6-4db6-9490-2d809d90d8da   ext4       
/dev/sdb1        4A89-7753                              vfat       UUI

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=e6b8a174-fa30-483a-9b81-26f51f314eb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e6b8a174-fa30-483a-9b81-26f51f314eb1

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

title        Ubuntu 12.04.4 LTS, kernel 3.11.0-19-generic
uuid        e6b8a174-fa30-483a-9b81-26f51f314eb1
kernel        /boot/vmlinuz-3.11.0-19-generic root=UUID=e6b8a174-fa30-483a-9b81-26f51f314eb1 ro quiet splash 
initrd        /boot/initrd.img-3.11.0-19-generic

title        Ubuntu 12.04.4 LTS, kernel 3.11.0-19-generic (recovery mode)
uuid        e6b8a174-fa30-483a-9b81-26f51f314eb1
kernel        /boot/vmlinuz-3.11.0-19-generic root=UUID=e6b8a174-fa30-483a-9b81-26f51f314eb1 ro  single
initrd        /boot/initrd.img-3.11.0-19-generic

title        Ubuntu 12.04.4 LTS, kernel 3.11.0-18-generic
uuid        e6b8a174-fa30-483a-9b81-26f51f314eb1
kernel        /boot/vmlinuz-3.11.0-18-generic root=UUID=e6b8a174-fa30-483a-9b81-26f51f314eb1 ro quiet splash 
initrd        /boot/initrd.img-3.11.0-18-generic

title        Ubuntu 12.04.4 LTS, kernel 3.11.0-18-generic (recovery mode)
uuid        e6b8a174-fa30-483a-9b81-26f51f314eb1
kernel        /boot/vmlinuz-3.11.0-18-generic root=UUID=e6b8a174-fa30-483a-9b81-26f51f314eb1 ro  single
initrd        /boot/initrd.img-3.11.0-18-generic

title        Ubuntu 12.04.4 LTS, kernel 3.11.0-15-generic
uuid        e6b8a174-fa30-483a-9b81-26f51f314eb1
kernel        /boot/vmlinuz-3.11.0-15-generic root=UUID=e6b8a174-fa30-483a-9b81-26f51f314eb1 ro quiet splash 
initrd        /boot/initrd.img-3.11.0-15-generic

title        Ubuntu 12.04.4 LTS, kernel 3.11.0-15-generic (recovery mode)
uuid        e6b8a174-fa30-483a-9b81-26f51f314eb1
kernel        /boot/vmlinuz-3.11.0-15-generic root=UUID=e6b8a174-fa30-483a-9b81-26f51f314eb1 ro  single
initrd        /boot/initrd.img-3.11.0-15-generic

title        Ubuntu 12.04.4 LTS, memtest86+
uuid        e6b8a174-fa30-483a-9b81-26f51f314eb1
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=e6b8a174-fa30-483a-9b81-26f51f314eb1 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=da84860c-f0a6-4db6-9490-2d809d90d8da /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=b5a71846-a80e-4fc7-87e9-fcf6d97fdbe8 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
cat: /tmp/BootInfo-FjoufwAp/Tmp_Log: No such file or directory
/home/ubuntu/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-FjoufwAp/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-FjoufwAp/Tmp_Log: No such file or directory
  No volume groups found

```

Thanks in advance for the assistance... I AM pretty new to this...

---

### Post by jamesisin on 2014-04-25
What you want is boot-repair:

[http://jamesisin.com/a_high-tech_blech/index.php/2012/01/repairing-grub-after-windows-breaks-it/](http://jamesisin.com/a_high-tech_blech/index.php/2012/01/repairing-grub-after-windows-breaks-it/)

You can install it into a live session and run it from there, or you can install it into your installed Ubuntu if you can boot there.

---

### Post by oldfred on 2014-04-25
You show an old menu.lst which is from grub legacy. But not grub2 grub.cfg file.
I think using Boot-Repair and do the full purge & reinstall would be best.

You do not install grub to a PBR like you have in sda1, BIOS only boots from MBR. But grub does not use PBR, so having it in the PBR will not matter.

---

