---
title: "The dual boot problem to end all dual boot problems!"
date: 2004-10-31
forum: General Help
---

### Post by conchobar on 2004-10-31
I have what seems to be a very common problem: Had Windows XP installed on the primary drive, by itself, and installed Ubuntu on some free space on the secondary drive, by itself. But, grub doesn't see Windows. I added into menu.lst the four lines of code as posted elsewhere on these forums, and that didn't change anything. Then, I tried a trick from a Fedora 2 posting: 
sfdisk -d /dev/hdc | sfdisk --no-reread -H255 /dev/hdc
That, too, had no effect. For kicks I went into BIOS and set the primary drive from auto to LBA, as that had solved it on a previous system after installing Fedora Core 2 after XP.

Those tricks seemed to solve the problem for everyone else, but made no impact on mine. Anyone have any more?? :)  The files are still there, as I could see them while trying to mount the NTFS disk in linux. As far as hardware goes, I'm running an AMD 64 (and using the 64 bit ubuntu), MSN K8N Neo mobo, two IDE optical disk drives and two hard drives, a gig of RAM, and a Radeon 9800 video card. Everything works fine except I can't get into Windows! :( 

Help please!

---

### Post by cacofonix on 2004-10-31
Can you post a copy of your grub.conf please?

---

### Post by conchobar on 2004-10-31
I don't seem to have a grub.conf, but instead this menu.lst:

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
timeout		3

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdd2 ro console=tty0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option contols options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## ## End Default Options ##

Title Windows
root (hd0,0)
makeactive
chainloader +1

title		Ubuntu, kernel  
root		(hd1,1)
kernel		/boot/vmlinuz root=/dev/hdd2 ro console=tty0 quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel  (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz root=/dev/hdd2 ro console=tty0 single
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-amd64-generic 
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.8.1-3-amd64-generic root=/dev/hdd2 ro console=tty0 quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-amd64-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.8.1-3-amd64-generic root=/dev/hdd2 ro console=tty0 single
initrd		/boot/initrd.img-2.6.8.1-3-amd64-generic
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by cacofonix on 2004-10-31
It looks in order, what is the windows partition refered to in /etc/fstab?

---

### Post by conchobar on 2004-10-31
Here's fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

That looks like it only has the secondary drive with linux on it. Hmm. The Windows drive is hdc.

---

### Post by cacofonix on 2004-10-31
Can you try this change the menu.lst windows option to this see if that helps

```

title=windows
rootnoverify(hd0,0)
makeactive
chainloader +1

```

---

### Post by conchobar on 2004-10-31
Ok, that got Windows into the grub menu. But, this error occurs after selecting it:
Booting Windows
makeactive
chainloader +1

Error 13: Invalid or unsupported executable format

Yikes, that sounds scary. Any ideas?

---

### Post by cacofonix on 2004-10-31
Thats good I guess :P at least it showed up now we got to get it to boot  try the same option again just remove chainloader +1 and see how that goes

cacofonix

---

### Post by wallijonn on 2004-10-31
Are those IDE drives?

what does your /boot/grub/menu.lst look like?

At the end of mine it says:

> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.8.1-3-686 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.8.1-3-686 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-686
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1


obviously yours should say:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Razvan on 2004-11-06
since your windows is on hdc, your windows entry in menu.lst should be changed from 

root (hd0,0)

to  root (hd2,0)

try that...

---

### Post by CapKrugers on 2004-11-06
I had a similar problem when trying to dual-boot, only nothing would happen after I selected the Windows entry from GRUB. I fixed it by changing the hard drive mode from "Auto" in my BIOS to "Large". I'm not sure if in my BIOS "Large" means "LBA" but hey, it worked. 

My Windows partition was on /dev/hda1 and my Ubuntu on /dev/hda2.

---

