---
title: "Computer doesn't wake up"
date: 2007-04-09
forum: General Help
---

### Post by Error47 on 2007-04-09
When I choose to "suspend" my computer, it will not work when I try to turn it back on. I usually just see a black screen with a blinking " __ "  . I'd like to fix that.

---

### Post by hardyn on 2007-04-09
WAY more info required...

desktop / notebook? brand? model? video driver? 

with my experiece using both the nvidia and ATI binary drivers, you must add vga=791 (or 780) to the boot string in grub.

without any more info about your machine, i think this is all we can do for you at the moment.

---

### Post by Rui Pais on 2007-04-09
> **Error47 said:**
> When I choose to "suspend" my computer, it will not work when I try to turn it back on. I usually just see a black screen with a blinking " __ "  . I'd like to fix that.

hi,
have you tried to add 
> resume=/dev/xxxx 
to kernel line in your /boot/grub/menu.lst? 
(with resume=/dev/xxxx replaced by your swap partition reference)

---

### Post by Error47 on 2007-04-09
I think I should have posted this in absoulte beginner talk. 
I have a pentium 4 HP desktop, nvidia gforce 4 mx 4, 1gb ram. 

" resume=/dev/xxxx " What do I replace the xxxx with?
 
I am a beginner linux user in general, still learning the basics. For example I am still trying to figure out how to install Skype. So I need some easy instructions please.

Thanks.

---

### Post by altaaa on 2007-04-09
Also make sure you have a swap partition which is BIGGER than your amount of RAM.

---

### Post by Rui Pais on 2007-04-09
> **Error47 said:**
> I think I should have posted this in absoulte beginner talk. 
I have a pentium 4 HP desktop, nvidia gforce 4 mx 4, 1gb ram. 

" resume=/dev/xxxx " What do I replace the xxxx with?
 
I am a beginner linux user in general, still learning the basics. For example I am still trying to figure out how to install Skype. So I need some easy instructions please.

Thanks.

you can find what your swap is by typing:
```
cat /etc/fstab | grep swap
```

post for more help if you need

---

### Post by Error47 on 2007-04-11
This is what I get after " cat /etc/fstab | grep swap "


```
UUID=7980557e-91bc-4529-80e0-765a48c3fa29 none            swap    sw              0       0

```

I still have absolutely no clue what that means or what to do.

---

### Post by Rui Pais on 2007-04-11
hi,
i don't know if resume recognize new UUID format...

you can get the old typing:
```
ls -l /dev/disk/by-uuid |grep 7980557e-91bc-4529-80e0-765a48c3fa29
```
the last word, hdxx or sdxx, are the one that you need.

hth

---

### Post by Error47 on 2007-04-12
After typing that command in I get 

```
lrwxrwxrwx 1 root root 10 2007-04-12 14:21 7980557e-91bc-4529-80e0-765a48c3fa29 -> ../../hda5
```

What does it mean, and how do I get it fixed?

---

### Post by Rui Pais on 2007-04-12
Ok, 
 
do:
gksudo gedit /boot/grub/menu.lst

and then look for the line that starts with 'kernel' that points to your actual kernel and add at the end of the line:
resume=/dev/hda5

save and reboot (and pray, this is not, granted to work)

---

### Post by Error47 on 2007-04-12
there are a few lines that start with ' kernel ' . I know this file is very sensitive so I don't want to add it to the wrong place.

---

### Post by Rui Pais on 2007-04-12
ok, wise decision.

post the output of 
```
uname-a
```
and 
```
cat /boot/grub/menu.lst
```
and i tell you what to change exactly.

---

### Post by Error47 on 2007-04-12
Out put of the first command: 

```
Linux andrew-desktop 2.6.17-11-generic #2 SMP Tue Mar 13 23:32:38 UTC 2007 i686 GNU/Linux
```

Second:

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
default         0

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
# kopt=root=UUID=a879305e-ab9d-4e72-90e8-1b5c10f5c990 ro
# kopt_2_6=root=/dev/hda2 ro

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

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

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

```

---

### Post by Rui Pais on 2007-04-12
just change **line 119**, from
> kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash

to
> kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash resume=/dev/hda5


save and reboot.

good luck

---

### Post by Error47 on 2007-04-12
It didn't work. I restarted my system, then tried to ' suspend ' it. When I tried to resume what I was doing the screen came up black with nothing on it. Just a blank black screen.

---

### Post by Error47 on 2007-04-13
Does anyone at least have a similar problem?

---

### Post by Rui Pais on 2007-04-13
hi,
yours is one of the most common problem with Ubuntu, but regrettably one of the hardest to solve :(

You should check bios options. Mine only work when set to S3 (POS/S1 fails).

Another suggestion could be checking for another video driver (since it seems that it suspends but wake to a broken video state). In my case never have a problem with nvida original drivers but have read a lot of posts of people with problems with the one on restricted modules from ubuntu package...

Another way to try is suspend2. It's a little harder and yet experimental, but works very well for some people. [Here is a thread]("http://ubuntuforums.org/showthread.php?t=284994") on it, with debs available that make it easy.

Good luck.

---

