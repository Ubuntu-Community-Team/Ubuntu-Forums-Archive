---
title: "URGENT Help! Please Grub Configration"
date: 2008-07-08
forum: General Help
---

### Post by Rishabhsood on 2008-07-08
Well, I had uBuntu 7.10 and Vista multi boot installed, I heard of 8.06 and downloaded. I installed it on my USB drive and then When ever I had to start vista I had to plug the usb drive. 

I searched in google and found
and did a
grub-install /dev/sda2

on my uBuntu partition

It didnt help then I did the same on Vista partition

Now still problem is there BUT a major problem came in now

When I hit Enter in Grub confgiration on Vista It says Starting Grub configration Stage2
and There I see uBuntu 7.10 and Vista

I try to start Vista, again the same Stage2 screen comes

I am ready to donate $10 PayPal(Sorry if m going against rule of forum) to guy to help me start Vista without formating


I am also not able to access the Vista Drive from uBuntu
[IMG]http://img257.imageshack.us/img257/6518/screenshot1zz3.png[/IMG]

---

### Post by enchesss on 2008-07-08
have you tried booting the system with a live cd?

you say:

> and did a
grub-install /dev/sda2

on my uBuntu partition

It didnt help

does this mean that you can still boot into heron only if the usb drive is attached?

If this is true and you dont mind overwriting the usb heron you should try to reinstall grub by using the live cd to do another installation on the usb drive.

if you want to keep the usb drive files then you can (but i am not 100% sure how to becuase i have not done it) abort the installation after the grub has been set up.

you may then be able to again boot into vista with the usb attached and then properly back up your NTFS files to an external HD.

If you cant get your vista back this way then you can take out the hard drive and attach it to another windows computer. It should be able to read the contents of the NTFS partition. If it cant then you may have to use some file (NTFS) restoration software that should be available on the internet.

---

### Post by VMC on 2008-07-08
The reason you now have to use the usb drive is because the menu list is stored there.
How do you want this to look like in the end? Do you want both ubuntu's and Vista?

Let't start with this. It's best to plug in your usb drive also. From a Terminal type this:

```
sudo fdisk -l
```

Also we will need Grub's boot menu. So type this and post both outputs:

```
cat /boot/grub/menu.lst
```

Maybe even your fstab will help us:

```
cat /etc/fstab
```

Since you last installed ubuntu 8.04, these should come from your usb drive.

---

### Post by Rishabhsood on 2008-07-08
Sorry these are nt from usb drive as I formatted it and also I am not able to run it, It gives error after login, cant access desktop

I installed uBuntu on USB drive again but loaded bootloader on internal drive this time but now Vista option went away from boot Grub Config.

Here are output

fdisk -l

> rishabh@rishabh-laptop:~$ sudo fdisk -l
[sudo] password for rishabh:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04a64b5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16730   134379402    7  HPFS/NTFS
/dev/sda2           16731       17945     9759487+  83  Linux
/dev/sda3           18196       19457    10137015    7  HPFS/NTFS
/dev/sda4           17946       18195     2008125   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 4104 MB, 4104610304 bytes
255 heads, 63 sectors/track, 499 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000058e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         470     3775243+  83  Linux
/dev/sdc2             471         499      232942+   5  Extended
/dev/sdc5             471         499      232911   82  Linux swap / Solaris
rishabh@rishabh-laptop:~$ 
rishabh@rishabh-laptop:~$ 



cat /boot/grub/menu.lst

> rishabh@rishabh-laptop:~$ cat /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=a04c0921-72a8-442d-b54b-afd287ceecd5 ro

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

title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=a04c0921-72a8-442d-b54b-afd287ceecd5 ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=a04c0921-72a8-442d-b54b-afd287ceecd5 ro single
initrd          /boot/initrd.img-2.6.22-15-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a04c0921-72a8-442d-b54b-afd287ceecd5 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a04c0921-72a8-442d-b54b-afd287ceecd5 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

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
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Windows Vista/Longhorn (loader)
root            (hd0,2)
savedefault
makeactive
chainloader     +1

rishabh@rishabh-laptop:~$ 



cat /etc/fstab

> rishabh@rishabh-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=a04c0921-72a8-442d-b54b-afd287ceecd5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=CC5C26B55C269A6A /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=2C88743C8874071C /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=35952592-563d-4ed4-a4de-b1939fbc09a9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
rishabh@rishabh-laptop:~$ 


---

### Post by VMC on 2008-07-08
> Sorry these are nt from usb drive as I formatted it and also I am not able to run it, It gives error after login, cant access desktop

I installed uBuntu on USB drive again but loaded bootloader on internal drive this time but now Vista option went away from boot Grub Config.I'm at a lost as to what you want to do here. The Grub menu.lst is now on your usb drive. You need to re-install grub for the internet ubuntu, which is "/dev/sda2" or grub's root (hd0,1).

If the usb drive installed okay, then leave it alone, but plugged in. If you from a grub prompt > use the find grub it will point to the usb drive. That's not what you want, I'm guessing. I'm thinking you want the internal ubuntu to have control. By re-installing ubuntu from the usb drive, now it's in control.

I'll wait to see exactualy what you want this to look like.

---

### Post by Rishabhsood on 2008-07-08
I just want Vista to work

now the Vista got away from boot menu :( after I reinstalled uBuntu on USB drive and installed bootloader to sda2

---

