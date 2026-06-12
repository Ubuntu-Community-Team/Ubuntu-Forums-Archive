---
title: "startup issues/not syncing"
date: 2008-02-14
forum: General Help
---

### Post by billybag on 2008-02-14
i went to start up my computer yesterday and when i try to load ubuntu linux, i get the following message: 

```
kernel panic-not syncing: VFS: unable to mount root fs on unknown-block (0,0)
```

what happened in between the time i shut my computer down after its last use and before i started it up hours later?

---

### Post by chrisccoulson on 2008-02-14
What other information do you get?

---

### Post by Thyme on 2008-02-14
Did you update your kernel? Check that you're mounting the correct partition at 0,0 and that you have the ext3 filesystem kernel drivers installed. Play around with the grub entry, that usually works !

---

### Post by billybag on 2008-02-14
that is all the info i get and no i didnt update anything. i ran a check using gparted and i got nothing. i guess i will try playing around with grub...

---

### Post by chrisccoulson on 2008-02-14
Were there not any messages above the one that you posted? Could you post the contents of your /boot/grub/menu.lst and /etc/fstab from the live CD.

Also, from the live CD, could you post the output of the following 2 commands:
```
fdisk -l
ls -l /dev/disk/by-uuid
```

---

### Post by billybag on 2008-02-14
when  i start up in recovery mode i get a more full error

```
VFS: Cannot open root device "UUID= b u n c h o f r a n d o m n u m b e r s a n d l e t t e r s" or unknown-block (0,0)

Please append correct "root=" boot option; here are the avaliable partitions:

Kernel panic-not syncing: VFS: unable to mount root fs on unknown-block (0,0)
```

i am going to put the live disk in now and do what chrisccoulson suggested.

---

### Post by billybag on 2008-02-14
```
ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-02-14 12:45 24536ff8-3083-47aa-90f5-4c9b554d0235 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2008-02-14 12:45 5f4a6f00-409c-4e53-9bd1-928eabba21dc -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-02-14 12:45 6050E8CA50E8A84C -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-02-14 12:45 71738259-4af0-40cd-8618-e9ef9b2e4b36 -> ../../sda2
ubuntu@ubuntu:~$ 

```

FSTAB
```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0
```

and menu.lst doesnt exist...

---

### Post by billybag on 2008-02-14
also tried this:

```
ubuntu@ubuntu:~$ sudo  mount -t ntfs-3g /dev/sda1 /media/disk-2 -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/disk-2: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sda1 ()
ubuntu@ubuntu:~$ 

```

and menu.lst is:
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color dark-gray/black light-gray/black

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=5f4a6f00-409c-4e53-9bd1-928eabba21dc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=5f4a6f00-409c-4e53-9bd1-928eabba21dc ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=5f4a6f00-409c-4e53-9bd1-928eabba21dc ro single
initrd		/boot/initrd.img-2.6.22-14-386

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		****
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

sorry

---

### Post by chrisccoulson on 2008-02-14
I think the fstab you posted is the fstab from the live environment. It would be better if you posted your fstab from your install using the live CD. To do this, you need to mount your root filesystem from the live CD. To do this:
```
sudo mkdir /media/target
sudo mount -t ext3 /dev/sdb1 /media/target
```
(I'm assuming your root filesystem is /dev/sdb1. If not, then substitute with the actual device)

Then post the contents of /media/target/etc/fstab and /media/target/boot/grub/menu.lst (assuming you have /boot on the root partition.

Anyhow, the error you're seeing suggests that you have the wrong root filesystem specified in your menu.lst

---

### Post by billybag on 2008-02-14
```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=5f4a6f00-409c-4e53-9bd1-928eabba21dc / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=24536ff8-3083-47aa-90f5-4c9b554d0235 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sda1 /media/named ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color dark-gray/black light-gray/black

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=5f4a6f00-409c-4e53-9bd1-928eabba21dc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=5f4a6f00-409c-4e53-9bd1-928eabba21dc ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=5f4a6f00-409c-4e53-9bd1-928eabba21dc ro single
initrd		/boot/initrd.img-2.6.22-14-386

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		****
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

and yeah gparted says that a mountpoint could not be found for sdb1. i am not sure how to fix this though

---

### Post by billybag on 2008-02-15
?

should i reinstall grub?

---

### Post by chrisccoulson on 2008-02-15
I can't see anything obviously wrong from your posts. Give us a little while, as I'm not sure how grub is normally configured when /boot isn't on the disk that you boot from. I'm going to try and set up a similar configuration in a virtual environment, and then I might be able to offer some more assistance. In the meantime, someone else may be able to offer some help.

You could try reinstalling grub. Thats what I would do, but I'm not sure how to go about it on your setup.

---

### Post by billybag on 2008-02-17
i tried reinstalling grub and now i doint have a grub at all and i cant seem to figure out how the hell to reinstall it.

---

### Post by manij on 2008-02-19
I had the same problem!

It appears that my initrd.img image file i was supposed to use went missing from by /boot.

fortunately i had couple of other kernel options i could boot from!

any one can tell me how this can happen? I did a upgrade which did not take. but the sytem was fine even aftera couple of hard reboots and then it crashed with the same error on startup as you have described?

Mani

Here is my Menu.lst

[B][I]MENU.LST

title Ubuntu, kernel 2.6.15-51-386
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-51-386 root=/dev/sdb1 ro quiet splash
savedefault
boot

title Ubuntu, kernel 2.6.15-51-386 (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-51-386 root=/dev/sdb1 ro single
boot

title Ubuntu, kernel 2.6.15-29-386
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-29-386 root=/dev/sdb1 ro quiet splash
initrd /boot/initrd.img-2.6.15-29-386
savedefault
boot

title Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-29-386 root=/dev/sdb1 ro single
initrd /boot/initrd.img-2.6.15-29-386
boot

title Ubuntu, kernel 2.6.15-26-386
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/sdb1 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

title Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/sdb1 ro single
initrd /boot/initrd.img-2.6.15-26-386
boot

title Ubuntu, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1[/I][/B]

Here is my /boot

[B][I] 4 drwxr-xr-x 3 root root 4096 2008-02-18 07:18 .
4 drwxr-xr-x 21 root root 4096 2008-01-01 07:26 ..
268 -rw-r--r-- 1 root root 266735 2006-09-08 21:51 abi-2.6.15-26-386
268 -rw-r--r-- 1 root root 266735 2007-09-24 17:58 abi-2.6.15-29-386
268 -rw-r--r-- 1 root root 266735 2008-02-12 17:32 abi-2.6.15-51-386
76 -rw-r--r-- 1 root root 69978 2006-09-08 19:52 config-2.6.15-26-386
76 -rw-r--r-- 1 root root 69967 2007-09-24 17:17 config-2.6.15-29-386
76 -rw-r--r-- 1 root root 69967 2008-02-12 16:51 config-2.6.15-51-386
4 drwxr-xr-x 2 root root 4096 2008-02-18 07:18 grub
6700 -rw-r--r-- 1 root root 6846850 2008-01-01 07:26 initrd.img-2.6.15-26-386
6700 -rw-r--r-- 1 root root 6847464 2008-01-01 07:26 initrd.img-2.6.15-29-386
100 -rw-r--r-- 1 root root 94760 2005-10-25 10:32 memtest86+.bin
716 -rw-r--r-- 1 root root 726461 2006-09-08 21:51 System.map-2.6.15-26-386
716 -rw-r--r-- 1 root root 727244 2007-09-24 17:58 System.map-2.6.15-29-386
716 -rw-r--r-- 1 root root 727244 2008-02-12 17:33 System.map-2.6.15-51-386
1388 -rw-r--r-- 1 root root 1414735 2006-09-08 21:51 vmlinuz-2.6.15-26-386
1388 -rw-r--r-- 1 root root 1415075 2007-09-24 17:58 vmlinuz-2.6.15-29-386
1388 -rw-r--r-- 1 root root 1415019 2008-02-12 17:32 vmlinuz-2.6.15-51-386[/I][/B]

As you can see

initrd.img--2.6.15-51-386 is missing. This the default kernel, i'm supposed to boot from according to the menu.lst. :confused::confused::confused::confused:

---

### Post by strabes on 2008-02-19
> **billybag said:**
> i tried reinstalling grub and now i doint have a grub at all and i cant seem to figure out how the hell to reinstall it.

See the GRUB link in my signature.

---

### Post by billybag on 2008-02-20
i got everything working fine.... for a day


now i am getting that pesky error 15: file not found. i have gotten this before a long time ago and forget how to fix it and none of the other 'fixes' i am finding are working

---

