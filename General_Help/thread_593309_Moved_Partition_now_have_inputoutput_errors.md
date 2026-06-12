---
title: "Moved Partition now have input/output errors"
date: 2007-10-27
forum: General Help
---

### Post by ndstate on 2007-10-27
Hello,

I did a search and could not find a solution so I hope someone can help.

**What happens:**  I start my computer and grub comes up, if I try to boot to the windows partition all I get is the text "starting up" and the screen will slowly fad in and out different colors (never seen anything like it before)... it will not load windows and does not seem to do anything.

**What caused it to happen:**  There was some space on my hard drive that was unallocated; so I moved it from the "left side" of my windows partition to the "right side" so I could merge the unallocated space with the the 7.04 installation I already had.

The process of moving the the unallocated space seems to have messed up the windows partition and I cannot access windows during bootup, and I cannot access the files through linux either.

I have attached the error log from the partition software (from the 7.10 live cd), I received the error when I tried to check/repair (I cant recall the exact name) the partition.
 I have also attached a screen shot that shows some of the warnings for the partition (errors.php) and a screen shot of what happens when I try to access the partition in Linux.

Any help as to what I can do to at least get the files or to fix it completely would be great.

Thank you very very much,

Brian


P.S. I saw some in some other support topics that the following info was posted:


```
 cat /boot/grub/menu.lst
```

[COLOR="Green"]Shows:[/COLOR]

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
default         6

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
#    [COLOR="Red"]  password --#################### -- I edited out what was here[/COLOR]
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
# kopt=root=UUID=f3ed46b4-7f4d-4173-aa69-a31cf38df459 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=f3ed46b4-7f4d-4173-aa69-a31cf38df459 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=f3ed46b4-7f4d-4173-aa69-a31cf38df459 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=f3ed46b4-7f4d-4173-aa69-a31cf38df459 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=f3ed46b4-7f4d-4173-aa69-a31cf38df459 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Windows NT/2000/XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1


I do see a part that says "# Pretty colours
#color cyan/blue white/blue"  

that is what appears to be happening when I try to boot into windows... I dont know what it means


```
cat /etc/fstab
```

[COLOR="Green"]Shows:[/COLOR]

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=f3ed46b4-7f4d-4173-aa69-a31cf38df459 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=5EDC8081DC8054E5 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=08C8-4599  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=4f181c36-f3a8-4f13-aceb-06109bb54ffd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

P.P.S Feel free to change the attachment hard drive.txt to hard drive,html as it actually is an html file.

Thank you for your time!

---

### Post by ndstate on 2007-10-27
Note:  The error log does say:

> NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.

However I cannot run chkdsk because I cannot get windows to load I dont even think I can get it to call up msdos or safe mode or anything.

Thanks :)

---

### Post by huwnet on 2007-10-27
From my experiences the partitioner can't handle Windows very well :(

You can try using the recovery mode on a windows install CD to run chkdsk

---

### Post by ndstate on 2007-10-27
Hello,

I tried your suggestion, however chkdsk does not seem to do anything.  I ran all of the options (IE: /r    etc.) and none of them seem to do anything.

I ran some other recovery console tools (from a windows cd)  and now I cannot even see the partition when booted into Linux.  Furthermore, gparted in 7.04 is now showing the partition as FAT, it was NTFS.

When I try to boot into windows via grub I get the following error:  "NTLDR is missing."

...Do I have a problem with my master boot rec
ord or something?

Anyone have any ideas how I can at the very least get the data from that partition? 

Thanks for any help,

Brian

---

### Post by ndstate on 2007-10-29
Can someone please provide any input?

Thanks,

Brian

---

