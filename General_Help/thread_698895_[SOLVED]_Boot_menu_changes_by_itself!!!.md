---
title: "[SOLVED] Boot menu changes by itself?!!!"
date: 2008-02-16
forum: General Help
---

### Post by Victormd on 2008-02-16
This has happened to me twice now and I have no idea what's going on. I dual boot between XP and Ubuntu and have my menu.lst set to "savedefault" so that it will automatically boot to the last used OS. However, the menu.lst seems to be changing on its own because two times now the savedefault option disappeared... Any thoughts???

---

### Post by yabbadabbadont on 2008-02-16
It probably is happening after a kernel update.  After a kernel update is installed, the update-grub script is run to regenerate your menu.lst file.  It is probably what is changing it on you.

---

### Post by bilge.tutak on 2008-02-16
Do you see additions to the list or only change of elements in the list? If it is new elements in the list, then it is most probably because of kernel update. You can go in to the grub file and change (add/remove) items.

---

### Post by johnnyb1726 on 2008-02-16
I recommend creating a backup of your menu.lst so that when it overwrites the original you can just use your backup.

--cheers

---

### Post by Victormd on 2008-02-17
Well, now I'm even more confused... if it is due to a kernel update, then the whole file should change, or at least,all  the modifications I've made to it (please correct me if I'm wrong). So here's the deal, these lines didn't change:

# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		saved  (I MODIFIED THIS LINE)

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2   (I MODIFIED THIS LINE)
:
:
:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault  (DON'T REMEMBER IF THIS IS DEFAULT OR NOT)
makeactive
chainloader +1


And these lines were the only ones that changed (as far as I noticed):


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7bb753d0-6fd4-4e2b-ba2d-7479d38b93e5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
makeactive
quiet

The "savedefault" and "makeactive" disapeared...

Is this normal???

---

### Post by yabbadabbadont on 2008-02-17
Those are the lines that update-grub replaces after a kernel update...  ;)

Please post the entire menu.lst file.  There may be somewhere else in there where you can specify to include the "savedefault" option with all generated entries.

If not, you'll either need to edit your menu.lst after every kernel update, or edit the update-grub script (it's just a bash script) to always include the savedefault option.  In which case, I would file a bug against the grub package at launchpad.net.

---

### Post by Shazaam on 2008-02-17
One or two drives? Is the Windows drive/partition listed in fstab?

---

### Post by Victormd on 2008-02-18
Here's the full menu.lst

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
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

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
# kopt=root=UUID=7bb753d0-6fd4-4e2b-ba2d-7479d38b93e5 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7bb753d0-6fd4-4e2b-ba2d-7479d38b93e5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
makeactive
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7bb753d0-6fd4-4e2b-ba2d-7479d38b93e5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# 
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader +1


I have 2HDs but Windows and Ubuntu are on the same partitioned drive

what's fstab?

---

### Post by yabbadabbadont on 2008-02-18
```
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

```

Uncomment that line and edit it and your trouble should go away.  It should look like this:
```
## should update-grub add savedefault to the default options
## can be true or false
savedefault=true

```

---

### Post by Victormd on 2008-02-19
Ok, I though about that, but what about this:

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

So I wasn't sure about what would happen on the next kernel update...

---

### Post by yabbadabbadont on 2008-02-19
Good point.  Just change 'false' to 'true' and don't uncomment it.

---

### Post by Victormd on 2008-02-19
Let's wait and see what happens at the next update...
Thanks for the help!

---

### Post by yabbadabbadont on 2008-02-19
You don't have to wait.  Just run ```
sudo update-grub
``` and see what happens.

---

### Post by Victormd on 2008-02-20
The savedefault is still there so I guess that did the trick!

Thanks!

---

