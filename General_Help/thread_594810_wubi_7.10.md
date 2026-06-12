---
title: "wubi 7.10"
date: 2007-10-28
forum: General Help
---

### Post by krehbester on 2007-10-28
I installed Wubi-7.10-alpha-rev377 with Ubuntu 7.10-desktop-amd64 on my E drive  and rebooted my computer. I selected Ubuntu it went through the installation process just fine but when it rebooted it tells me that the partition doesn't exist.  I installed Wubi in Vista. help please

---

### Post by ago on 2007-10-28
> **krehbester said:**
> I installed Wubi-7.10-alpha-rev377 with Ubuntu 7.10-desktop-amd64 on my E drive  and rebooted my computer. I selected Ubuntu it went through the installation process just fine but when it rebooted it tells me that the partition doesn't exist.  I installed Wubi in Vista. help please

What is the exact error?
can you also post the content of /ubuntu/disks/boot/grub/menu.lst
and a description of your disks/ partitions 
+ which partition was wubi installed on

---

### Post by krehbester on 2007-10-28
error 27 no such Partition 
I have 3 hard drives, a 200 gb, 80 gb, and a 250 gb the 200 gb has windows xp the 250 gb has vista, and the 80 gb is just extra space.  the 80 gb is always the E Drive. the 200 and 250 change drive letter depending on which operating system I'm in. If in vista the 250 is c can the 200 is D, if in xp the 200 is c and the 250 is d.  Disk 0 is the 200 gb, disk 1 is the 80 gb, and disk 2 is the 250.    The contents of /ubuntu/disks/boot/grub/menu.lst:


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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout 3
# Set a timeout 3
# (normally the first entry defined).
timeout 3

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
# kopt=root=UUID=C454590A5459009A loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)/ubuntu/disks

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

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd1,4)/ubuntu/disks
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=C454590A5459009A loop=/ubuntu/disks/root.disk ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd1,4)/ubuntu/disks
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=C454590A5459009A loop=/ubuntu/disks/root.disk ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd1,4)/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LISTwubi is installed on the e drive,  the 80 gb drive

---

### Post by ago on 2007-10-28
try changing

root (hd1,4)/ubuntu/disks => root (hd0,4)/ubuntu/disks

everywhere

---

### Post by krehbester on 2007-10-28
Thanks, I changed it too 0 and it still didn't work so i tried 2 and it seems to work just fine.

---

### Post by ago on 2007-10-28
Can you post here your /boot/grub/device.map? Does it look correct?

---

### Post by krehbester on 2007-10-28
heres the device.map contents
> 
(fd0)    /dev/fd0
(hd0)    /dev/hda
(hd1)    /dev/hdb
(hd2)    /dev/sda


---

### Post by ago on 2007-10-28
also please: 

cat   /proc/mounts

and

ls /dev/(s|h)d*

---

### Post by krehbester on 2007-10-28
Sorry I'm kinda of new at this you are going to have explain how I get you what you want.

---

### Post by ago on 2007-10-28
In linux open a terminal, then cut and paste:

cat /proc/mounts
ls /dev/(s|h)d* 

Then select the output, right click, copy

Open firefox and paste it here

---

### Post by krehbester on 2007-10-28
here it is
> 
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
/dev/disk/by-uuid/C454590A5459009A /host fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
/dev/loop0 / ext3 rw,data=ordered 0 0
/dev/loop0 /dev/.static/dev ext3 rw,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/loop1 /home ext3 rw,data=ordered 0 0
/dev/disk/by-uuid/C454590A5459009A /boot fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
securityfs /sys/kernel/security securityfs rw 0 0
keenin@keenin-desktop:~$ ls /dev/(s|h)d*
bash: syntax error near unexpected token `('


---

### Post by ago on 2007-10-28
ls /dev/sd*
ls /dev/hd*
ls -al /dev/disk/by-uuid/

---

### Post by krehbester on 2007-10-28
Heres whats in the Dev/disk/by-uuid   

/dev/disk/by-uuid/6688F87E88F84E55
/dev/disk/by-uuid/A630E6E330E6BA07
/dev/disk/by-uuid/C454590A545900

I can't find dev/sd* or dev/hd* or anything that is even close to either one.
Sorry you are going to have to treat me like I know nothing at all.

---

### Post by ago on 2007-10-28
need the output of 
ls **-al **/dev/disk/by-uuid

---

### Post by krehbester on 2007-10-28
Heres it is
> 
total 0
drwxr-xr-x 2 root root 100 2007-10-28 07:04 .
drwxr-xr-x 6 root root 120 2007-10-28 07:04 ..
lrwxrwxrwx 1 root root  10 2007-10-28 07:04 6688F87E88F84E55 -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-10-28 07:04 A630E6E330E6BA07 -> ../../hda1
lrwxrwxrwx 1 root root  10 2007-10-28 07:04 C454590A5459009A -> ../../hdb5


and the other ones you asked for
keenin@keenin-desktop:~$ ls /dev/sd*
/dev/sda  /dev/sda1
keenin@keenin-desktop:~$ ls /dev/hd*
/dev/hda  /dev/hda1  /dev/hdb  /dev/hdb1  /dev/hdb5  /dev/hdc  /dev/hdd

---

