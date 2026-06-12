---
title: "I swapped my HDs and now XP doesn't boot"
date: 2007-06-06
forum: General Help
---

### Post by ticopelp on 2007-06-06
Hey all,

I have two HDs in my machine, one running Ubuntu and the other XP.  A couple weeks ago, I decided to make Ubuntu my primary boot drive because I thought the XP drive was going bad. Well, it turns out it was just a bad power supply and the drive is fine, so I want to make the XP disk bootable again, and I can't seem to get it working. 

The XP drive was initially the master and the Ubuntu a slave drive. I've since swapped them around and Ubuntu works fine. The XP option is still in the boot menu, but when I select it, it just says "Starting up..." and then nothing happens. 

Here is my disk info:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             144G  114G   24G  84% /
varrun                506M  120K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  140K  506M   1% /proc/bus/usb
udev                  506M  140K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/hdb1              84G   76G  8.4G  91% /media/CORE
/dev/hdb6              75G   50G   25G  67% /media/JUKEBOX
/dev/hdb5              75G   51G   25G  68% /media/VAULT

```

Here is my Grub menu.lst:

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
default		0

splashimage=(hd0,0)/boot/Ubuntusplash.xpm.gz  

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
# kopt=root=UUID=7cfb6c89-5463-438a-9711-78ac5e3759e4 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7cfb6c89-5463-438a-9711-78ac5e3759e4 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=7cfb6c89-5463-438a-9711-78ac5e3759e4 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7cfb6c89-5463-438a-9711-78ac5e3759e4 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=7cfb6c89-5463-438a-9711-78ac5e3759e4 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```

I've read many threads on the boards trying to get a handle on this, but I'm leery about making any further changes without a little bit of hand-holding.

Any help would be much appreciated. Thanks.

---

### Post by Yoooder on 2007-06-06
So just to verify some things:

hdb1 is your primary windows partition, correct?

When your WinXP drive was the primary, did it have GRUB installed to it?

Did you have to install GRUB to your Ubuntu drive?

What happens when you try to start WinXP from GRUB?

---

### Post by ticopelp on 2007-06-06
hdb1 is the primary Windows partition.

I'm not sure if Grub was installed to XP -- when I first set up my system, I had XP already installed, and I added a second HD and installed Ubuntu on that, and then did dual boot. 

I didn't manually install Grub on Ubuntu; I did, however, manually edit the menu.lst file when I moved the hard drives around.

When I try to start XP from Grub it gives me a black screen and says "Starting up..." and then does nothing.

---

### Post by hillbilly on 2007-06-06
Correct me if I'm wrong, but now you have XP as the primary drive right ? Else you can't run Windows. And How did you verify that you XP disk was working when you swapped it ?

---

### Post by confused57 on 2007-06-06
You might try adding mapping commands to your Window's entry:

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map     (hd0) (hd1)
map     (hd1) (hd0)
chainloader	+1

---

### Post by ticopelp on 2007-06-06
> **hillbilly said:**
> Correct me if I'm wrong, but now you have XP as the primary drive right ? Else you can't run Windows. 

Oh, see, I didn't know that.

> **hillbilly said:**
> And How did you verify that you XP disk was working when you swapped it ?

Well, I meant "working" in the sense that I can still mount the Windows volumes and get data from them fine. 

[quote="confused57"]You might try adding mapping commands to your Window's entry:[/quote]

Thanks, I'll see if this works.

---

### Post by ticopelp on 2007-06-06
Okay. confused57, your additions to the menu.lst totally worked. I was able to boot successfully into XP. 

And my Ubuntu drive is set to the primary boot device in the BIOS and is in the master position, so it appears the XP drive does not, in fact, have to be the primary to boot. 

Thanks a lot for the help, I appreciate it.

---

### Post by hillbilly on 2007-06-06
Oh, I'm sorry. I was under the impression that Windows must be the primary OS if it is to boot. My bad.

---

### Post by jerrylamos on 2007-06-06
XP expects to be on the first partition on the first hard drive.  That's best case......Ubuntu can be anywhere, but does not like for hard drives to be swapped without re-installing.

Cheers, Jerry

---

