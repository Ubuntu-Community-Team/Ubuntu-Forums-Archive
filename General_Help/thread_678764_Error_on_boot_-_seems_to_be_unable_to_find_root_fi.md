---
title: "Error on boot - seems to be unable to find root filesystem"
date: 2008-01-26
forum: General Help
---

### Post by sharong on 2008-01-26
I have a Dell Laptop with Ubuntu 6.06 (Dapper Drake) installed.  When I tried to boot it today, it brought up the usual Ubuntu loading screen, with the progress bar, and it got as far as saying 'mounting root filesystem' (or something along those lines - it's the second piece of text that comes up) and then I got an error message and the command prompt.

The message says:

> mount: Mounting /dev/hda1 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

...blah blah blah...

/bin/sh: can't access tty; job control turned off

If I try to mount any of these manually, it says that it can't read /etc/fstab because it's not there, and when I looked, it's not.

Can anyone tell me how to resolve this?  Or even how to get my files off the hard disk, so I can just reinstall the OS?

I didn't do anything out of the ordinary the last time I used it; haven't installed anything new or anything like that.  The laptop only has Ubuntu on it, nothing else.

Thanks in advance for any help, I really appreciate it.

Let me know if you need more info.

---

### Post by taurus on 2008-01-26
Do you still have the LiveCD?  Can you boot from that?  If you can, boot your machine with it and then open a terminal and post the output of this command here.

```
sudo fdisk -l
```

---

### Post by sharong on 2008-01-26
Hi there, thanks for your reply!

I did that, and this is what I get:


> Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2339    18787986   83  Linux
/dev/hda2            2340        2432      747022+   5  Extended
/dev/hda5            2340        2432      746991   82  Linux swap / Solaris

---

### Post by taurus on 2008-01-26
Now do

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
cat /mnt/ubuntu/etc/fstab
```
Post the output of the last command here.

---

### Post by sharong on 2008-01-26
OK, I did all that.

Here's what I got:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2008-01-26
How about

```
cat /mnt/ubuntu/boot/grub/menu.lst
```

---

### Post by sharong on 2008-01-26
I get this:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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

---

### Post by taurus on 2008-01-26
Unmount your harddrive and then reboot without the CD again and see if you still get the same error message about can't mount /dev/hda1.

```
sudo umount /dev/hda1
```

---

### Post by sharong on 2008-01-26
Hi,

yes, I still get exactly the same error message as before.

I'm going to have to go offline for a few hours, so don't rush to reply to this.  Back in a few hours!

Thanks for your help.

---

### Post by taurus on 2008-01-26
If you need to backup your files on your harddrive, you can mount it from a LiveCD.

```

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu

```
Now, your harddrive is mounted to /mnt/ubuntu.

---

### Post by sharong on 2008-01-27
Thanks taurus,  being able to access my files is really all I need - I think I'll maybe upgrade from Dapper anyway, and I'm thinking of partitioning my hard drive, so I might as well reinstall from scratch (also, at some point months ago I banjaxxed my sound settings and various other things, so a reinstall might just be the easiest).

Thing is, though, when I go into the mounted drive in the way you said, I can see my files, but I can't access all the directories.  It's as if it doesn't recognise some of them as directories.  So I can get into, say 'Photos', but then where there should be a list of subdirectories like 'Family' and 'Home', there are just what look like files (with the same names), the icon being the Gnome footprint - and I can't get into them.  In the terminal it won't let me cd into them.  Any ideas what might be going on there?  Or what I can do about it?

I tried chmod-ing them, but that didn't make any difference.

---

