---
title: "help with ugly partitions"
date: 2007-01-23
forum: General Help
---

### Post by biker-dude on 2007-01-23
Ok, I have always been scared of partitioning, I guess because a). I'm too lazy to back-up regularly and b). it confuses the hell out of me. Anyway, when I first tried to install Ubuntu, the installation froze up on me, so I went with Kubuntu, and instead of just putting it on the entire hdd, I used only existing free space (around 30G). Anyway, I had an old debian partion prior to ubu/kubu installs, and my partition table is ugly, and I'd like resize my existing Kubuntu. Could someone help me out with this, please?? Here is my existing partion table:


# fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks          Id  System
/dev/hda1   *           1         851     6835626          83  Linux
/dev/hda4             852       19457   149452695    5   Extended
/dev/hda5           14858       19266    35415261   83  Linux
/dev/hda6           19267       19457     1534176    82  Linux swap / Solaris
/dev/hda7           14253       14857     4859599+  82  Linux swap / Solaris
/dev/hda8             852        1409     4482072        82  Linux swap / Solaris
/dev/hda9            1410       14252   103161366   83  Linux

Guess what I really need to know is which swap I need to keep, hda5, btw, is my active, current partition that I work out of. I know people are going to tell me to boot Knoppix or some other live cd - got that burned already. But what are the specific commands I'm going to want to use with gparted?

---

### Post by indytim on 2007-01-23
Whew,  

What a grouping of partitions.

You only need 1 /swap across Linux.  The general rule-of thumb is 2x RAM.

If you have old distro's you're not using anymore, you may want to use something like GParted Live and "ace" them out.

If you're starting from scratch (in other words haven't got a real resident ops and have just performed the initial load of Kubunut, you may want to consider wiping the drive altogether and then using GParted Live to pre-configure your essential partitions.

Wait a few minutes for other members of the collective to "chime in" on this one.

Good Luck,

IndyTim

---

### Post by bodhi.zazen on 2007-01-23
Well that is not so bad ....

Here is what I would do ..

First, yes you need to boot to a live CD for partition management. You can not move/resize a mounted partition ....

I use GParted:

	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

	Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

OK boot to gparted and delete all your partitions EXCEPT hda5 (your root partition). You can delete your swap partition as well, it will just get in the way ...

Next move hda5 to the front of the disk hda1

Next delete hda5

Next resize hda1 to all but a small swap partition at the end of the disk ....

Make a swap partition at hda2, size = ram X2, max 1 Gb

Now the fun part.

[color=red]**BEFORE YOU CAN REBOOT YOU NEED TO EDIT menu.lst and fstab on hda1 FROM THE LIVE CD[/color]**

```
sduo mount /dev/hda1 /mnt
sudo nano /mnt/etc/fstab
```

In fstab change the root partition line, the one with / in the second column to:
> /dev/hda1 / .....
You need only change the /dev/hda1
And swap:
> /dev/hda2 swap ...
Again you need only change /dev/hda2

Save and exit nano

Now ```
sudo nano /mnt/boot/grub/menu.lst
```

In the Ubuntu stanza change:

root **(hd0,0)**

and on the kernel line:

kernel /boot/vmlinuxz-xyz **root=/dev/hda1** ro ....

Save and exit menu.lst

Reboot ....

You could use a more complex partitioning scheme if you like ....

indytim's advice is good, but you will not learn as much ...

---

### Post by biker-dude on 2007-01-23
Yeah, I really don't know anyway to determine which swap partition i'm actually using, so I can't really delete any swap. does anyone know how to figure out which swap I might be using??

---

### Post by bodhi.zazen on 2007-01-23
Look up ...

It does not matter

---

### Post by biker-dude on 2007-01-23
sorry bodhi.zazen - posted before i saw your post. :D

---

### Post by bodhi.zazen on 2007-01-23
> **biker-dude said:**
> sorry bodhi.zazen - posted before i saw your post. :D

LOL no problem, my reply was quite pedantic and I did not want you to miss it as you had posted while I was typing ...

Please let me (us) know if there is a step or part you do not understand.

---

### Post by biker-dude on 2007-01-23
I don't know if this matters, but vi /boot/grub/menu.lst has commented out the "root"  as well as the "kernel" line:

# root      (hd0,0)
# kernel    /vmlinuz root=/dev/hda2 ro
 
Do they need to be uncommented when I have the file /mnt/boot/grub/menu.lst opened in the live-cd?

Also, is it ok to use gparted from knoppix-live instead of burning the live-gparted cd?

---

### Post by bodhi.zazen on 2007-01-23
> **biker-dude said:**
> I don't know if this matters, but vi /boot/grub/menu.lst has commented out the "root"  as well as the "kernel" line:

# root      (hd0,0)
# kernel    /vmlinuz root=/dev/hda2 ro

These lines are a mis-match. Perhaps it is best if you post all of menu.lst ....
 
> Do they need to be uncommented when I have the file /mnt/boot/grub/menu.lst opened in the live-cd?

Well, yes you will need to have a working menu.lst

> Also, is it ok to use gparted from knoppix-live instead of burning the live-gparted cd?

gparted from knoppix will work AS LONG AS THE PARTITIONS ARE NOT MOUNTED. I am not sure but I am guessing knoppix will auto mount your partitions. If so, you will need to unmount them.

```
sudo umount /media/*
```

---

### Post by biker-dude on 2007-01-23
Here's my /boot/grub/menu.lst:
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-k7 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-k7
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-k7 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.12-10-k7
boot

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.10-6-k7 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-6-k7 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.10-6-k7
savedefault
boot

title		Ubuntu, kernel 2.6.10-6-k7 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-6-k7 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.10-6-k7
boot

title		Ubuntu, kernel 2.6.10-6-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-6-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.10-6-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-6-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-6-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.10-6-386
boot

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.10-5-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Linux (on /dev/hda3)
root		(hd0,2)
kernel		/vmlinuz root=/dev/hda3 ro 
savedefault
boot


```

---

### Post by bodhi.zazen on 2007-01-23
Thanks. boy you have a lot of old kernels :)

If you like you can remove them with synaptic and delete the stanzas from menu.lst

OK to boot after you move your root partition to /dev/hda1 you will need to change:> title		Ubuntu, kernel 2.6.12-10-k7 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-k7
savedefault
boot

To```
title		Ubuntu, kernel 2.6.12-10-k7 
root		**(hd0,0)**
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/**hda1** ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-k7
savedefault
boot
```

And if you do not understand fstab, post that as well ;)

(thats /etc/fstab)

---

### Post by biker-dude on 2007-01-23
ok - yes, I admit I'm a slob administrator.  

Will it be safe to remove all the old/not used kernels except:

```
# uname -a
Linux homeytop 2.6.12-10-k7 #1 Tue Dec 12 15:51:16 UTC 2006 i686 GNU/Linux

```

I think I understand your fstab instructions. Thanks for all your help!

---

### Post by bodhi.zazen on 2007-01-23
> **biker-dude said:**
> ok - yes, I admit I'm a slob administrator. > 

LOL

[quote]Will it be safe to remove all the old/not used kernels except:

```
# uname -a
Linux homeytop 2.6.12-10-k7 #1 Tue Dec 12 15:51:16 UTC 2006 i686 GNU/Linux

```

Yes. Use synaptic to remove the old kernels and then update menu.lst (remove the stanzas with old kernels)

[quote]I think I understand your fstab instructions. Thanks for all your help!

:)

No problem. Let us know how it turns out or if you run into problems ;)

---

### Post by biker-dude on 2007-01-24
OK - I have another question before I go and do something irreversible. If I go ahead with the instructions from bohdi.zazen, and delete my extended partition (hda4), won't that delete hda5, which is the only partition I want?? very confused here....

---

### Post by bodhi.zazen on 2007-01-24
> **biker-dude said:**
> OK - I have another question before I go and do something irreversible. If I go ahead with the instructions from bohdi.zazen, and delete my extended partition (hda4), won't that delete hda5, which is the only partition I want?? very confused here....

Yes, that is correct. Don't do that until after you move (**copy**) hda5 to hda1 and are able to boot hda1.

Only then delete hda4, hda5 .... and resize hda1 and re-create a swap ...

HTH

---

