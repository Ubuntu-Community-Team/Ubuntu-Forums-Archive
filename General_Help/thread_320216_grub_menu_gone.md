---
title: "grub menu gone"
date: 2006-12-16
forum: General Help
---

### Post by dbbolton on 2006-12-16
is it possible to boot ubuntu from the grub command line ?

i played around with it for awhile but couldn't figure out how.

my /boot/grub/menu.lst was accidentally deleted.

---

### Post by dbbolton on 2006-12-16
...will use the sabayon live cd for now

---

### Post by dbbolton on 2006-12-17
bump.

---

### Post by bulldog on 2006-12-17
Just reinstall grub from the live cd.
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

---

### Post by dorcssa on 2006-12-17
And you didn' have a backup file? That's why you always have to create one when playing around. ;) Here's mine, but you have to figure out your partition and kernel number of corse. HOpe it helps.
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
# kopt=root=/dev/hdb1 ro

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
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

```

Well, the other one is a better way. :mrgreen: That's shows I'm still a newbie. :D

---

### Post by dbbolton on 2006-12-17
actually, found a backup file. but i think installing sabayon messed up the drive. i remember on the installer it said "you have not defined a mount point '/' on partition hda4." so, i selected that partition and typed "/" in "mount point", and it installed fine.

i moved the contents of folder /boot on hda2 (which is where ubuntu is) to /boot on hda4 (which is where sabayon is). i copied the old grub file too, but added an entry for sabayon by copying the entry in sabayon's menu.lst , and i got error 15: file not found.



but who knows, i still might need that file soon. thank you both

---

### Post by Hossie on 2006-12-17
Just boot Ubuntu from the Grub Commandline (press c). There you can enter the commands for booting Ubuntu (they are the same as in your menu.lst, except the title-entry).

---

### Post by shane2peru on 2006-12-17
I would use your Live CD to get in.  Then in a terminal you should be able to ```
sudo chroot (the mount point)
```  After that you should be able to run ```
sudo grub-install hda4
```  or which ever drive number would be appropriate.  That should re-install grub for you.  Any more questions just post back.

Shane

---

### Post by Hossie on 2006-12-17
> **shane2peru said:**
> I would use your Live CD to get in.  Then in a terminal you should be able to ```
sudo chroot (the mount point)
```  After that you should be able to run ```
sudo grub-install hda4
```  or which ever drive number would be appropriate.  That should re-install grub for you.  Any more questions just post back.

Shane

You should mount /dev first, though.

```
sudo mount -o bind /dev /mnt/xxx/dev
```

---

### Post by dbbolton on 2006-12-17
bulldog, is this correct ?

```
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,1)
 (hd0,3)

grub> root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub>

```


i put hd0,1 because ubuntu is on hda2.

---

### Post by dbbolton on 2006-12-17
it's working perfectly now. 

sincere thanks to everyone who took the time to respond :)

---

