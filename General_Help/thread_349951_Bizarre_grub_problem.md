---
title: "Bizarre grub problem"
date: 2007-01-30
forum: General Help
---

### Post by noisymime on 2007-01-30
I'm having a bizarre issue with GRUB and an Edgy install at the moment that I'm hoping someone might be able to help with.

It all started when I decided to get rid of a couple of partitions I wasn't using. The original partition setup was:
/dev/sda1 - Windows NTFS drive (C:\ on Windows install)
/dev/sda2 - FAT32 data
/dev/sda5 - Swap
/dev/sda6 - Reiser4 mounting to /home
/dev/sda7 - Ext3 mounting to / (Contains main Edgy install)
/dev/sda8 - NTFS data

This drive had survived a number of OS installs, hence all the partitions and my desire to clean the whole thing up. I moved everything from /dev/sda2 and /dev/sda8 to other places and blew them both away, leaving free space in their wake. I rebooted after this and received the following error when grub tried to load:
```
"Error 17 : Cannot mount selected partition"
```
After a little reading around I booted with a liveCD, chroot'd into /dev/sda7 and performed:
```
grub-install /dev/sda
```
Restarted again and this time the grub menu loaded normally. 
When I selected the first option in the grub menu though, I get a message saying:
"Error 18: Selected cylinder exceeds maximum supported by BIOS"
The same error is received for every option in the grub list.

After playing around I discovered that the system would boot fine if I dropped into grub's console and entered the following:
```
kernel /boot/vmlinux-xxxxx root=/dev/sda7
initrd /boot/initrd-xxxxxx
boot
```

Which is basically what was in /boot/grub/menu.lst file anyway.
Then, completely by accident, I found that if I boot up with a usb memory key plugged in, that everything works perfectly and I'm not required to 'manually' boot through the grub console.

At this point I've hit the limit of what I know about grub. From what I've read the "Error 18" from grub represents a partition being outside the range of the bios, however prior to deleting the old partitions all this worked normally so this seems strange. 

Anyone out there got any ideas?

---

### Post by llamakc on 2007-01-30
Share your /boot/grub/menu.lst

---

### Post by po0f on 2007-01-30
noisymime,

And the output of `sudo fdisk -l /dev/sda`.

---

### Post by noisymime on 2007-01-30
Here's is the /boot/grub/menu.lst:

```
splashimage=(hd1,7)/boot/grub/splashimages/KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
##color cyan/blue white/blue

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
# kopt=root=UUID=67039720-ae01-4c75-99d1-accc851db7bd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,7)

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
# defoptions=quiet splash vga=normal

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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
title Ubuntu
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=67039720-ae01-4c75-99d1-accc851db7bd ro quiet splash vga=normal
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,7)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=67039720-ae01-4c75-99d1-accc851db7bd ro quiet splash vga=normal
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,7)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=67039720-ae01-4c75-99d1-accc851db7bd ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot



title           Ubuntu, memtest86+
root            (hd1,7)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

I should also point out that when booting up, grub gives an error for the first line (The splashimage one) saying that it cannot read the file, however the boot splash doesn't really bother me and the error goes away if I remove the line.

Thanks

---

### Post by po0f on 2007-01-30
noisymime,

If you can, boot the live CD and run `vol_id` on /dev/sda7 to make sure that the UUID in menu.lst matches the filesystem's actual UUID.  Moving partitions around may have changed it.

[EDIT]

Also, GRUB indexes from 0, meaning sda7 is (hd0,6).

---

### Post by noisymime on 2007-01-30
po0f,

I'll dig up the livecd and give it a shot. I think its still ok though as if I enter the following in the grub console then it'll boot ok:
```
kernel /boot/vmlinux-xxxxx root=UUID=67039720-ae01-4c75-99d1-accc851db7bd
initrd /boot/initrd-xxxxxx
boot
```

Typing that UUID by hand is a real pain, but it did boot ok with it.

---

### Post by llamakc on 2007-01-30
Questions for those in the know:

Doesnt `vol_id` exist on the system w/o running the LiveCD (if they get booted up by manually starting up via grub's console)?

Could not the OP run it and compare that with their menu.lst?

Thanks.

---

### Post by po0f on 2007-01-30
llamakc,

Yes it does, but when making changes like this, I think it's best to use a live CD.

---

### Post by llamakc on 2007-01-31
> **po0f said:**
> llamakc,

Yes it does, but when making changes like this, I think it's best to use a live CD.

Okay, but why? Not trying to troll, but curious. If the issue is that the /etc/fstab has bad UUID entries because of drives thave have been moved around, does `vol_id` correctly interpret the UUID regardless of being run from the LiveCD? Also, can one not go to an older-styled /etc/fstab?

Is the reason why because you have had success with that manner, or something else? Thanks.

---

