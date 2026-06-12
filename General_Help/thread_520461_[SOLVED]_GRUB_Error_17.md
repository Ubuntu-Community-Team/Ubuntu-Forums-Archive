---
title: "[SOLVED] GRUB Error 17"
date: 2007-08-08
forum: General Help
---

### Post by dr.koljan on 2007-08-08
Here's the situation.

I used to have a bootable NTFS partition, an ext3 and an extended partition with a non-bootable NTFS and two swap partitions. It looked like something like this:

<NTFS(boot)>24.98GB</NTFS><ext3>~14GB</ext3>{extended}<swap>~0.5GB</swap><swap>0.6GB</swap><NTFS>36.5GB</NTFS>{/extended}

When I noticed that I had two swap partitions, I decided to erase one of it and add the free space to the either the Linux partition or the non-bootable NTFS. I deleted the second swap through Windows Vista (the first gave me an error), then loaded into the Ubuntu LiveCD. and launched GNOME Partition Editor. I noticed that both swaps were deleted and tried to add the free space to NTFS which failed:

<NTFS(boot)>24.98GB</NTFS><ext3>~14GB</ext3>{extended}<free>~1.1GB</free><NTFS>36.5GB</NTFS>{/extended}

 Therefore I created a 690MB swap in the free space:

<NTFS(boot)>24.98GB</NTFS><ext3>~14GB</ext3>{extended}<free>~0.5GB</free><swap>690.23MB</swap><NTFS>36.5GB</NTFS>{/extended}

..shrinked the extended partition...

<NTFS(boot)>24.98GB</NTFS><ext3>~14GB</ext3><free>~0.5GB</free>{extended}<swap>690.23MB</swap><NTFS>36.5GB</NTFS>{/extended}

...and added the free space to the ext3 partition:

<NTFS(boot)>24.98GB</NTFS><ext3>14.53GB</ext3>{extended}<swap>690.23MB</swap><NTFS>36.5GB</NTFS>{/extended}

Now GRUB fails to load giving me the 17th error, the grub-install doesn't help, and the Vista Repair stuff tells me that everything with my Vista installation is perfectly ok (though it does call that installation "Windows Vista (TM) Ultimate **(recovered)**)

Any ideas what to do now? I hope I haven't broken anything (the only thing i did to ext3 was expanding) and I don't really want to reinstall Ubuntu after I just installed and configured everything I needed :)

Any help would be greatly appreciated :)

---

### Post by dr.koljan on 2007-08-08
Bump :guitar:

---

### Post by confused57 on 2007-08-08
Boot the Ubuntu live cd, open a terminal, post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

I believe your problem may be that your UUID's have changed on the partition(s) that you made changes to, you can check the current UUID's with:
```
blkid
```

Then you need to mount your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

You'll then need to check the blkid UUID results with your /etc/fstab and /boot/grub/menu.lst(kernel line root UUID)...if they're different, you'll need to copy & paste the correct UUID from blkid into your fstab & menu.lst.  If you've deleted partitions that are mounted in fstab, you'll need to delete those entries.

Reinstalling may be easier, but this should give you something to try to recover your current setup.

---

### Post by psusi on 2007-08-08
UUIDs do not change from resizing, nor does grub know or care about UUIDs.  If you resized the partition where grub is installed ( your / partition if you don't have a /boot partition ) then you will need to reinstall grub after, but you said you tried that already so I don't know what to tell you.  

Maybe if you were more specific about exactly how you tried to reinstall grub?

---

### Post by dr.koljan on 2007-08-08
Thank you all for the help :) Indeed, there was a problem in the fstab, the UUID for the swap was wrong. I have changed it and now I can load GRUB but I get

>  Error 17: Couldn't mount selected partition

when I choose any Linux selection in the menu (but at least I can load Windows Vista now :guitar: )

I have tried reinstalling GRUB several times using [this](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) manual - still no work.

Here is the output of fdisk -l and of blkid as requested:

```
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3261    26193951    7  HPFS/NTFS
/dev/sda2            3262        5158    15237652+  83  Linux
/dev/sda3            5159       10011    38981722+   f  W95 Ext'd (LBA)
/dev/sda5            5247       10011    38274831    7  HPFS/NTFS
/dev/sda6            5159        5246      706797   82  Linux swap / Solaris

Partition table entries are not in disk order
root@ubuntu:/home/ubuntu# blkid
/dev/sda1: TYPE="ntfs" 
/dev/sda2: UUID="0ba29879-dc78-4033-b892-6eeed98b2b8c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="ntfs" 
/dev/sda6: UUID="3491cecd-63c5-4f6e-b9e9-52c2aa848786" TYPE="swap" 
root@ubuntu:/home/ubuntu# 
```

You might wish to see the contents of /etc/fstab and /boot/grub/menu.lst as well so I post them here:

[quote=boot/grub/menu.lst]# menu.lst - See: grub(8), info grub, update-grub(8)
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=0ba29879-dc78-4033-b892-6eeed98b2b8c ro

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
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0ba29879-dc78-4033-b892-6eeed98b2b8c ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0ba29879-dc78-4033-b892-6eeed98b2b8c ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/quote]

[quote=etc/fstab]# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=0ba29879-dc78-4033-b892-6eeed98b2b8c / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=3491cecd-63c5-4f6e-b9e9-52c2aa848786 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda5 /media/Downloads ntfs-3g defaults,locale=C 0 0
/dev/sda1 /media/disc ntfs-3g defaults,locale=C 0 0[/quote]

There must be a problem in one of these files but I can't find it, I hope you will. :)

---

### Post by confused57 on 2007-08-08
Your UUID's are correct, as I expected, didn't think it would hurt to check them.  I believe your problem is your root (hd0,2), for /dev/sda2 it should be (hd0,1)...you can check this by highlighting your Ubuntu entry in the boot grub menu, press "e", highlight the line with root, press "e" again, change root from (hd0,2) to (hd0,1), then press "enter, then press "b" to boot...if it works, this is temporary, but you can make it permanent in your /boot/grub/menu.lst...you would also need to change the line with #groot to (hd0,1), leave the # in front of groot(it's not actually commented out).

---

### Post by dr.koljan on 2007-08-08
YAY it worked thanks, I would never find out myself :guitar:

---

### Post by psusi on 2007-08-08
Yea, your root is on partition 1, not 2.  Change the # groot= line from 2 to 1 then run update-grub.

---

