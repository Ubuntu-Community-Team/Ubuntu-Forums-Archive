---
title: "Tried to fix MBR but now it's broke worse!"
date: 2008-04-13
forum: General Help
---

### Post by Tylazene on 2008-04-13
I'm still pretty new to Ubuntu and have 7.10 and xp dual boot system. Since I upgraded months ago to Gutsy my XP has never worked. It just gave me a "**starting up**" on a black screen. I'm pretty much independent of windows now but need access to the info on this xp partition. I searched through the forums and tried **ms-sys --mbr /dev/hda**. That didn't work and hosed GRUB too so couldn't boot to Ubuntu either. So I replaced GRUB with my live cd and got Ubuntu working again. XP is on the first partition so I figured I should place ms-sys in **hda1**. I did that and now I get "**invalid partition table**" trying to boot to XP and Ubuntu can't even read what's in xp now. Gparted sees hda1 but doesn't recognize the partition file system (it did before). I'm afraid to mess up Ubuntu because I have it tweaked out so nicely. I figured I'd ask you guys before going any further because I'm not sure I know what I'm doing yet. 


**fdisk -l** gets me this:

```
Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02cc02cb

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19414   155942923+   7  HPFS/NTFS
/dev/hda2           19415       38073   149878417+  83  Linux
/dev/hda4           38074       38633     4498200    5  Extended
/dev/hda5           38354       38633     2249037   82  Linux swap / Solaris
/dev/hda6           38074       38353     2249037   82  Linux swap / Solaris

Partition table entries are not in disk order


```

**cat /boot/grub/menu.lst** get's me this:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gHzne/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=3ada4bc1-0823-4e2e-bcef-8aacd6ddee6a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3ada4bc1-0823-4e2e-bcef-8aacd6ddee6a ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3ada4bc1-0823-4e2e-bcef-8aacd6ddee6a ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=3ada4bc1-0823-4e2e-bcef-8aacd6ddee6a ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=3ada4bc1-0823-4e2e-bcef-8aacd6ddee6a ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

Any suggestions?

---

### Post by Ptero-4 on 2008-04-13
Can you access your hda1 from the liveCD? From your fdisk it seems to be recognized as NTFS so it should be good.

---

### Post by Tylazene on 2008-04-13
Nope. Live CD doesn't see it either.

---

### Post by froy02 on 2008-04-13
Install ntfs-3g with synaptics package manager.  Start  the NTFS config tool by going  to Applications -> NTFS Configuration Tool.  Select your NTFS partition to mount and you'll be able to access your file in the windows drive.

---

### Post by Tylazene on 2008-04-13
Ok, installed ntfs-3g. I open the config tool and all I get is a small window to "enable write support for external device" there is another box to enable for internal too but is grayed out. I checked the box for external then rebooted but still nothing. 

I could read the xp files until I ran **ms-sys --mbr /dev/hda1**. So I assume that messed up partitions has something to do with it.

---

