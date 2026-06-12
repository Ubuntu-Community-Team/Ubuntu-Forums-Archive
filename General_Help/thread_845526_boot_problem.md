---
title: "boot problem"
date: 2008-06-30
forum: General Help
---

### Post by kattou22 on 2008-06-30
Hi, i tried to boot up my pc and at the grub command i choose to boot normally.
Unfortunately it tells me that there are errors with sd2 and a whole bunch of other errors. Then finally it says cannot start x. contact admin and then restart gdm.
When i boot with recovery mode trough root i finally do get to the command line but being a newbie, i have no clue what to do
Help. I do not have an install cd as i have no cd burner, i installed trhough windows . thanks you

---

### Post by VMC on 2008-06-30
Is this Wubi installed? If so we have a forum for that installation.

Open a Terminal from here "Applications-Accessories-Terminal", and type the following:

```
sudo fdisk -l
```

copy the info back here.

---

### Post by kattou22 on 2008-06-30
Sorry it took me so long, but i had to relog into Linux.  attempt to get to the command prompt.  Finally get to it. Copy what i see, and retype it in windows!!!  


Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 *512=8225280 bytes
Disk identifier: 0xde93de93

Device      Boot     Start    end   Blocks    Id    system
/dev/sda1    *         1     1217   9775048+   7    HPFS/NTFS
Partition 1 does not end on cylinder boundary
/dev/sda2            1218    2376   9309667+   83    Linux
/dev/sda3            2377    2434   465885      5    Extended
/dev/sda5            2377    2434   465853+ 82 linux swap/solaris

Disk /dev/sdb: 1026 MB, 1026555904 bytes
16 heads, 32 sectors/ track, 3916 cylinders
Unist= cylinders of 512 * 512 = 262144 bytes
Disk identifier : 0xxxxxxxxx

Device      Boot     Start    end    Blocks   Id     system
/dev/sdb1    *        1      3916    1002480   e  w95 fat16 (LBA)

---

### Post by VMC on 2008-06-30
I'm still confused as to how you installed this using Windows. Can you explain?
That might answer some questions.

I'm guessing that you hand copy the output and then use Windows to relay the info.
Your ubuntu is on /dev/sda2, so that's where the errors are coming from.

Can you somehow copy & paste the output of this:

```
cat /boot/grub/menu.lst
```

By the way, when you turn on your computer, do you get a Grub prompt with the OS listings. In other words how do you boot up Windows?

---

### Post by kattou22 on 2008-06-30
Oki, i finally managed to get in x  but unfortunately every time i boot it always does the same thing, it tells me there are errors and that it cant go in gdm..   to run fsck manually, i do that and every single time it finds inods that are empty have errors in them or are lost!!  I have been redoing this over 9 times and everty time it is different files.  But always the same thing .    No matter how i boot. At least now i can boot with out recovery mode though.   Do i keep booting and correcting errors!!  here i pasted what you asked me to paste


nikita@Nikita:~$ cat /boot/grub/menu.lst
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=ac157fa2-b79d-4fe8-8065-760f2bd6af2c ro

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ac157fa2-b79d-4fe8-8065-760f2bd6af2c ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ac157fa2-b79d-4fe8-8065-760f2bd6af2c ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=ac157fa2-b79d-4fe8-8065-760f2bd6af2c ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=ac157fa2-b79d-4fe8-8065-760f2bd6af2c ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ac157fa2-b79d-4fe8-8065-760f2bd6af2c ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ac157fa2-b79d-4fe8-8065-760f2bd6af2c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ac157fa2-b79d-4fe8-8065-760f2bd6af2c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ac157fa2-b79d-4fe8-8065-760f2bd6af2c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by kattou22 on 2008-06-30
by the way i also installed through windows a while back, everything worked wonderfully for about 3 months now. This error some how happened when my son turned off pc via power bar!!!    he does this often. the next time i booted this is what has been happening.  

I use grub.  and the option to install via windows is a file you download in windows that forces boot to download via the site and install UBUNTU. its neat when you dont have a cd burner!!

---

### Post by kattou22 on 2008-06-30
oops forgot one more thing. 

When i finally managed to start x session, this is an error that constantly appears..

xsession: warning: xrdb commandnot found: xressources not merged

Any one what that means

---

