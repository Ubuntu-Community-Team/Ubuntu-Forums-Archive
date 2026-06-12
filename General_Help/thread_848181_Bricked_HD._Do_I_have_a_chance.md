---
title: "Bricked HD. Do I have a chance?"
date: 2008-07-03
forum: General Help
---

### Post by addchild314 on 2008-07-03
Morning everyone,

I have an interesting problem. I have been running 8.04 on my Dell Inspiron 6400 for a few months now, without many problems. Recently, though, it has been giving me some interesting ones. 

Starting a few weeks ago, Compiz Fusion would just stop working, at seemingly random times. Reloading the window manager fixed that. Then x would go kaput, throwing me out of my session. A few days ago, my keyboard stopped working for a time. It would not respond to any keystrokes, but everything else still seemed to work fine. Rebooting generally fixed this. Until, one time I rebooted, and it booted to just before the login screen, and threw me an error:
```
ATA1.00: STAT [DRDY ERR]
ATA1.00: ERROR [UNC]
```

So I used my handy Magic Sysrq Key to reboot, and it threw me the same error, over and over. Unfortunately, now all it says is:

```
GRUB Loading stage1.5

GRUB loading, please wait...
```

and after a few minutes...

```
ERROR 18
```

It never actually gets to the grub loader. :(

I've been told this is a hardware error, but it isn't acting like a typical HD fail. gparted freezes when I try to scan/fix the primary partition, but I can still browse all my files on both partitions. 

Any help is greatly appreciated!


System: 
Dell Inspiron 6400
Intel Centrino Duo @ 1.8GHz
120GB SATA HDD
2 GB RAM
Ubuntu 8.04 AMD64 (Live CD for now, tho... :( )

---

### Post by gator64 on 2008-07-03
What do you have for these :

menu.lst

fdisk -l

---

### Post by addchild314 on 2008-07-03
Here is menu.lst


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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
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
# kopt=root=UUID=7f1958f2-e7da-4494-a331-cfbb1be6ba2b ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7f1958f2-e7da-4494-a331-cfbb1be6ba2b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7f1958f2-e7da-4494-a331-cfbb1be6ba2b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=7f1958f2-e7da-4494-a331-cfbb1be6ba2b ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=7f1958f2-e7da-4494-a331-cfbb1be6ba2b ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=7f1958f2-e7da-4494-a331-cfbb1be6ba2b ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=7f1958f2-e7da-4494-a331-cfbb1be6ba2b ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7f1958f2-e7da-4494-a331-cfbb1be6ba2b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7f1958f2-e7da-4494-a331-cfbb1be6ba2b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```


And the output from fdisk

```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12111    97281576   83  Linux
/dev/sda2           12112       14023    15358140   83  Linux
/dev/sda3           14024       14593     4578525   82  Linux swap / Solaris

```

---

### Post by ByteJuggler on 2008-07-03
Sounds like your hard drive is starting to fail.  You need to grab an image of it ASAP, get it replaced, then put the image onto a new working drive.  See ["Ubuntu Rescue Remix" ]("http://ubuntu-rescue-remix.org/")for more.

---

### Post by gator64 on 2008-07-03
Agreed

---

### Post by addchild314 on 2008-07-03
Thanks ByteJuggler, gator64
Dell is sending me out my 4th replacement hard drive... hopefully this one isn't too bad to image...

---

### Post by gator64 on 2008-07-03
That's a lot of hard drives.  Hopefully the next one from them won't fail -- good luck .

---

### Post by hyper_ch on 2008-07-03
how about firing up the Desktop cd and trying to mount the hd in the live session? do you get access?

---

### Post by addchild314 on 2008-07-03
Actually, yeah. I had full access and all my files seemed to be intact in the live session. That's what threw me off. It seemed like there were a lot of software problems leading up to this, especially since the last Kernel update

---

### Post by hyper_ch on 2008-07-03
well, if you have full access: **MAKE A BACKUP**

---

### Post by addchild314 on 2008-07-03
In the process right now

---

### Post by ByteJuggler on 2008-07-03
Just an added note: The fact that you can see/mount your filesystem probably juts means that the filesystem structures needed for the view you've seen does not reside on areas of the disk developing problems.  You should still backup your disk (preferably by binary imaging it) so that you can put it on another (healthy) disk without affecting your current install.  (That's assuming you can get a sufficiently intact/working copy off your current disk.  If you however have corruption in key system files, you may thus ultimately be forced to ultimately reinstall.)

Aside: To create an image of the entire disk, (/dev/sda in this example) to another file (/home/blah/sda_image.dat in this case), install GNU ddrescue (packagename is "gddrescue") and do:

```
ddrescue /dev/sda /home/blah/sda_image.dat /home/blah/sda1_image.log
```

With the logfile parameter which helps it track what it's done, you, you can IIRC stop and restart it and run it multiple times if needed.  Obviously you'd edit the names above as neccesary (and you would have to ensure /home/blah/... has enough space to take the resultant image, e.g. by mounting another disk there or whatever.)

You can then dump the image back to a new drive (taken to be /dev/sdb below) using plain "dd" as follows:

```
dd if=/home/blah/sda_image.dat of=/dev/sdb bs=16384
```

The bs=16384 sets the blocksize to speed copying.  The commands should be run from a liveCD (or a dedicated recovery CD like TRK) and obviously need to be run with root privileges.  So on Ubuntu you'd either "sudo -i" first,  or precede the commands by "sudo".  Most recovery CD's (like TRK) boot you into a root prompt by default.

**A word of warning: Please be very very very careful when using the above commands -- getting e.g. the input/output source/destinations wrong can easily cause you to overwrite your data.**

---

### Post by addchild314 on 2008-07-03
thanks again! Now I just need to free enough space on my external. Is there possibly any way to get it running again, even temporarily, you think? :neutral:

---

### Post by ByteJuggler on 2008-07-04
> **addchild314 said:**
> thanks again! Now I just need to free enough space on my external. Is there possibly any way to get it running again, even temporarily, you think? :neutral:

When you say, "get it running again", what do you mean?  (The above method I described will will basically rescue your entire install, and allow you to put it back on a new drive, after which it should run again, providing no key system files were damaged.)

If space is a big problem on your external, you can probably pipe the ddrescue output through a compressor to save space, but this will probably substantially increase the time required for copying the image.  Let me know if you want me to elaborate/show how to do that.

P.S. You can click on the blue ribbon thingy on a post to register thanks to a poster permanently.  :P

---

