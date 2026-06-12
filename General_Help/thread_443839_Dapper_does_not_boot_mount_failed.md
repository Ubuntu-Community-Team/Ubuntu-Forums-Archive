---
title: "Dapper does not boot: mount failed"
date: 2007-05-14
forum: General Help
---

### Post by flix007 on 2007-05-14
Hi,

I did nothing with my Dapper (like update, install software, crash) but this morning it refused to boot. The error message is:
```
Booting 'Ubuntu, kernel 2.6.15-27-686
root (hd0,0)
    Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuy-2.6.15-27-686 root=/dev/hda1 ro quiet splash
    [Linux-by Image, setup=0x1c00, size=0x170444]
initrd /boot/initrd.img-2.6.15.27=686
    [Linux-initrd @ 0x1f8b9000, 0x6a67db bytes
savedefault
boot
Uncompressing Linux ... Ok, booting the kernel
mount: Mounting /dev/hda1 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such device
mount: Mounting /sys on /root/sys failed: No such device
mount: Mounting /proc on /root/proc failed: No such device
Target filesystem doesn't have /sbin/init 
```

Well, I booted my Dapper liveCD. There I run e2fsck on all harddrive-partitions: no errors.
There, I am able to mount the partitions and read from them, all Data is ok. (some of the outputs were created with a feisty liveCD, therefore the sda's)

```
ubuntu@ubuntu:/dev$ sudo fdisk -l sda

Disk sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
  sda1               1         765     6144831   83  Linux
  sda2             766        4870    32973412+   5  Extended
  sda5             766         841      610438+  82  Linux swap / Solaris
  sda6             842        4870    32362911   83  Linux
ubuntu@ubuntu:/dev$ 
```

When booting from the harddrive I am droped to a shell. There I can also mount the root partition with
```
# mount -t ext3 /dev/hda1 /root
```
I absolutely see no errors in my configuration and I changed nothing. But I need my system back again as fast as possible. Can I start booting my hard-drive dapper after mounting the root partition by hand?

I also attach my fstab and grub-menu.lst, but I don't think there is something wrong:

```
ubuntu@ubuntu:/media/hd1/boot/grub$ cat ../../etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
```
ubuntu@ubuntu:/media/hd1/boot/grub$ cat menu.lst
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
timeout         3

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
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-28-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-686 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-686 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-686 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-28-686
boot

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-27-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-27-686
boot

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-26-686
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, kernel 2.6.15-25-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-25-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by flix007 on 2007-05-14
After mounting the root partition in the busybox-shell I could return to boot by Strg+D.  My Laptop booted Dapper without further complains.
However I am still waiting for an explanation. And I am looking forward to the next boot ... what will happen?!

---

### Post by flix007 on 2007-05-15
My Laptop now starts without any problems. So this issue seems to be solved.

But for me it is really strange, I do not understand what happend to my Dapper. Any ideas?

---

### Post by flix007 on 2007-05-16
Well, I had the problem again. That time I plugged in the battery and removed then the power cord while the laptop was running.  The next reboot (running on battery) stoped again, with the same error and same solution.

---

### Post by flix007 on 2007-05-16
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/115139](https://bugs.launchpad.net/ubuntu/+bug/115139) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I reported this behavior as a bug.

---

