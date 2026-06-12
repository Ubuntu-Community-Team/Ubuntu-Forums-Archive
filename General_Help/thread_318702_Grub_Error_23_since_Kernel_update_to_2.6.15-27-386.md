---
title: "Grub Error 23 since Kernel update to 2.6.15-27-386"
date: 2006-12-14
forum: General Help
---

### Post by ubu-for on 2006-12-14
Since the last Kernel update to 2.6.15-27-386 I get the following Grub error.

"Error 23: Error while parsing number"

I've never had a problem before!

device.map
```

(hd0)	/dev/sda
(hd1)	/dev/sdb # added this line because of error 23, but nothing changed

```

menu.lst
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
# kopt=root=/dev/sda1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Windows XP # added because d***f******kernelupdate deleted my old menu.lst
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
rootnoverify	(hd1,0) # SATA-II Disk 2, Partition 1 = sdb1
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.15-22-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-22-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-22-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-22-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-22-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-22-386
boot

title		Ubuntu, kernel 2.6.15-21-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-21-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-21-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-21-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-21-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-21-386
boot

title		Ubuntu, kernel 2.6.15-20-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-20-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-20-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-20-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-20-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-20-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

THX for your HELP!

---

### Post by ubu-for on 2006-12-14
Edit 1
```

title		Windows XP
#savedefault
#map		(hd0) (hd1)
#map		(hd1) (hd0)
root		(hd1,0) # noverify
makeactive
chainloader	+1

```

Grub Error: "filesystem type unknown, partition type 0x7"

Edit 2
```

title		Windows XP
#savedefault
#map		(hd0) (hd1)
#map		(hd1) (hd0)
rootnoverify	(hd1,0)
makeactive
chainloader	+1

```

No Grub Error message but nothing happens and Grub crashes.

Edit 3
```

title		Windows XP
savedefault
#map		(hd0) (hd1)
#map		(hd1) (hd0)
rootnoverify	(hd1,0)
makeactive
chainloader	+1

```

No Grub Error message but nothing happens and Grub crashes.

---

### Post by Sqwishy on 2006-12-14
try commenting out 
makeactive
under the windows xp section?

---

### Post by Smaskens on 2006-12-14
I got exactly same error after Kernel update.

Grub Error: "filesystem type unknown, partition type 0x7"

Error 17: Cannot mount selected partition.

Even trying with the old kernel version doesn't help. ](*,)

---

### Post by Sqwishy on 2006-12-14
> **Smaskens said:**
> I got exactly same error after Kernel update.

Grub Error: "filesystem type unknown, partition type 0x7"

Error 17: Cannot mount selected partition.

Even trying with the old kernel version doesn't help. ](*,)

can you post your grub.conf? :-D

---

### Post by ubu-for on 2006-12-14
> **Sqwishy said:**
> try commenting out 
makeactive
under the windows xp section?

Thank you very much! That's it! :D

```

title		Windows XP
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
rootnoverify		(hd1,0)
#makeactive
chainloader	+1

```

---

### Post by Sqwishy on 2006-12-14
> **ubu-for said:**
> Thank you very much! That's it! :D :biggrin:  i'm very happy i could help \\:D/

---

### Post by ubu-for on 2006-12-14
> **Smaskens said:**
> 
Even trying with the old kernel version doesn't help. ](*,)

Maybe it's a problem with Grub and not with the Kernel.

---

### Post by mcduck on 2006-12-14
Why do you have so many entries in your Grub? Do you really need all those different kernels?

Also, you shouldn't have the Windows entry between "### BEGIN AUTOMAGIC KERNELS LIST" and "### END DEBIAN AUTOMAGIC KERNELS LIST", as everything between those lines is automatically configured during kernel updates.. You should have all your own entries either before or after this area.

---

### Post by Herman on 2006-12-14
Hello ubu-for,
I agree with mc duck. I noticed also that you have your Windows boot entry pasted in your automagic kernels list, :-k
```
 ## ## End Default Options ##

title        Ubuntu, kernel 2.6.15-27-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-27-386
savedefault
boot

title        Windows XP # added because d***f******kernelupdate deleted my old menu.lst
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
rootnoverify    (hd1,0) # SATA-II Disk 2, Partition 1 = sdb1
makeactive
chainloader    +1
```You should cut your Windows entry from out of there, otherwise of course your Debian Automagic Kernels list will automagically delete it every time you receive a kernel update, which will drive you crazy! 

The best thing to do is to put your Windows and other Linux entries *underneath* the bottom of the automagic kernels list. Then you won't have the same problem again next time.:D

Like this,
  ```
### END DEBIAN AUTOMAGIC KERNELS LIST
                                                       
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root
                                                       
                                                       
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows XP 
savedefault
map       (hd0) (hd1)
map       (hd1) (hd0)
rootnoverify        (hd1,0)
#makeactive
chainloader    +1
```It doesn't make any sense to me why you need the makeactive command commented out, but if it works that way and it didn't work otherwise, then I guess it's okay. It's interesting, it must be something new that I haven't learned yet. :D

If you want to avoid having a big long list of old Ubuntu kernels,  (that you'll never use), in the way again, (after deleting the excess kernel entires like mcduck suggested), you can edit your 'howmany=all' line from 'all' to '1' as explained in this link, 
howmany=......................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#_howmanyall")
That will fix that problem too, so that won't happen again either.

Regards, Herman :D

---

### Post by ubu-for on 2006-12-14
> **mcduck said:**
> Why do you have so many entries in your Grub? Do you really need all those different kernels?

No, just the default settings.

> **mcduck said:**
> 
Also, you shouldn't have the Windows entry between "### BEGIN AUTOMAGIC KERNELS LIST" and "### END DEBIAN AUTOMAGIC KERNELS LIST", as everything between those lines is automatically configured during kernel updates.. You should have all your own entries either before or after this area.

Thank you for this hint mcduck and for your guide Herman! That's why I LOVE Ubuntu!

---

### Post by mcduck on 2006-12-14
> **ubu-for said:**
> No, just the default settings.Then you could uninstall the older kernels with Synaptic.. That will also remove them from Grub menu. But you'd better move that Windows entry first.

Anyway, I'm happy if was any help :)

---

### Post by Herman on 2006-12-14
Okay, good! :D That's what I LOVE about Ubuntu too, it's rewarding and fun to be able to help as well as to receive help, so everyone's a winner. :D

About your original post, > Since the last Kernel update to 2.6.15-27-386 I get the following Grub error.
"Error 23: Error while parsing number"
I've never had a problem before!
I'm not certain if this is exactly your problem still, or not, but just recheck your menu.lst grub entry and make sure that wherever you have '(hd0)', that the '0' is really a number zero and not a capital letter 'O', as that is one way I can reproduce the error 23 in my computer.
-Just in case it helps-
Regards, Herman :D

---

### Post by ubu-for on 2006-12-14
> **Herman said:**
> 
About your original post, 
I'm not certain if this is exactly your problem still, or not, but just recheck your menu.lst grub entry and make sure that wherever you have '(hd0)', that the '0' is really a number zero and not a capital letter 'O', as that is one way I can reproduce the error 23 in my computer.
-Just in case it helps-
Regards, Herman :D

I'm sorry to disappoint you but that's why I posted the whole menu.lst with copy and paste.

---

### Post by Herman on 2006-12-14
Oh, okay, that's all good then, the main thing is it's working okay now anyway. 
All the best,
Regards, Herman :D

---

### Post by Smaskens on 2006-12-15
> **Sqwishy said:**
> can you post your grub.conf? :-D

Sure :D! I have still the same error, I already tried following menu.lst:

```

title		Ubuntu, kernel 2.6.15-27-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

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
#makeactive
chainloader	+1
map (hd1) (hd0)
map (hd0) (hd1)


```

---

### Post by mcduck on 2006-12-15
> **Smaskens said:**
> Sure :D! I have still the same error, I already tried following menu.lst:
```

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
#makeactive
chainloader	+1
map (hd1) (hd0)
map (hd0) (hd1)

```

If you want to remap your drives in grub you have to do it before the root line, after that it's too late ;)

```

title		Microsoft Windows XP Professional
map (hd1) (hd0)
map (hd0) (hd1)
root		(hd1,0)
savedefault
#makeactive
chainloader	+1

```

---

### Post by Smaskens on 2006-12-15
> **mcduck said:**
> If you want to remap your drives in grub you have to do it before the root line, after that it's too late ;)

```

title		Microsoft Windows XP Professional
map (hd1) (hd0)
map (hd0) (hd1)
root		(hd1,0)
savedefault
#makeactive
chainloader	+1

```

Well, so far previous solution worked fine. One month ago my 200gb hard disk which included only files crashed. Because my old windows installation was on this hd, naturally the grub menu was on it.

After that I had to do numerous fixes for the Ubuntu configuration files before grub was able to boot from 40gb Ubuntu hard disk (Ubuntu was on 2nd hard disk and it was now 1st and the only one hd). So the ubuntu thought it was on 2nd disk, even it was on 1st disk now. A bit complicated to explain, but I just don't want to reinstall Ubuntu before I must do it.

But lets get back to this issue, I changed mapping before the root as adviced. However I still cannot boot Ubuntu because the same error message is displayed. 

Grub Error: "filesystem type unknown, partition type 0x7"

Windows is booting fine, but Ubuntu not.  The problem came up after the recent kernel update. ](*,)

What is the problem, I cannot figure it out? 

```
title		Ubuntu, kernel 2.6.15-27-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd1) (hd0)
map (hd0) (hd1)
root		(hd1,0)
savedefault
#makeactive
chainloader	+1


```

---

### Post by mcduck on 2006-12-15
Ok, I'm sorry, I thought it was Windows you had troubles booting into.. 

Could you post results of 'sudo fdisk -l' also? The error is telling that Grub can't recognize the filesystem of the partition, so we'd better check that it's the right one you are trying to boot :)

---

### Post by ubu-for on 2006-12-15
Could this be a solution?

```

title		Ubuntu, kernel 2.6.15-27-386
rootnoverify		(hd1,0) # NOVERIFY added
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

```

P.S. Your Grub root drive for Windows and Ubuntu is the same (hd1,0).

---

### Post by mcduck on 2006-12-15
> **ubu-for said:**
> Could this be a solution?

```

title		Ubuntu, kernel 2.6.15-27-386
rootnoverify		(hd1,0) # NOVERIFY added
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

```

P.S. Your Grub root drive for Windows and Ubuntu is the same (hd1,0).

I've never seen Linux being booted with 'rootnoverify', but I guess it dosn't hurt to try.

And windows and Linux aren't set to same partition, notice the lines with map (hd1, hd0) and map (hd0, hd1). They remap disks to different order. In theory they could be removed and Windows booted with partition (hd0,0) but as Windows is weird it sometimes helps to remap it..

---

### Post by Smaskens on 2006-12-16
thanks for the quick reply :). I fixed this myself at last night after some experiments :), hd(1,0) are now replaced with hd(0,0) and root=/dev/hda1. 

Hopefully this is now in order, please let me know if something is still wrong and next kernel update will mess my config again.

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd1) (hd0)
map (hd0) (hd1)
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```

```

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4677    37567971   83  Linux
/dev/hda2            4678        4865     1510110    f  W95 Ext'd (LBA)
/dev/hda5            4678        4865     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hdb2            2551       38912   292077765    f  W95 Ext'd (LBA)
/dev/hdb5            2551       38912   292077733+   7  HPFS/NTFS


```

---

### Post by mcduck on 2006-12-16
Looks fine, only that now the Windows entry is pointing to the same partition where Linux is.. You should remove the map lines. (or change the root line for windows to (hd0,0) Also make sure you have right partitions on the default options section, before the actual boot options. Otherwise next kernel update will screw you again.

---

