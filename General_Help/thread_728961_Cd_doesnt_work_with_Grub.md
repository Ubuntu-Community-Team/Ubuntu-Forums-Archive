---
title: "Cd doesnt work with Grub"
date: 2008-03-19
forum: General Help
---

### Post by Creole on 2008-03-19
My CD-drive doesn't work due to grub, it doesn't work in in Windows XP or Ubuntu.
I know the reason is grub, because the first time i reinstalled everything (xp and ubuntu).
And after installing ubuntu (and grub) my cd-rom was not recognised. I tried to fix grub with an ms dos cd, just to fix the /mbr and after that my cd-rom worked again. Anyone an idea?

Ow yeah, i get this error when I click on the CD, mount: 'special device /dev/scd0 does not exist'

---

### Post by Creole on 2008-03-19
Anyone? It really sucks that. I can't use ubuntu cause of grub

---

### Post by danwood76 on 2008-03-19
What motherboard, CD-ROM drive etc do you have? (or what PC if your unsure)

---

### Post by peedeeramone on 2008-03-19
ive never heard of grub being the reason for a cd rom not working... but then again theres alot of things i havent heard of

specs would be useful along with maybe your grub conf

btw where are you hailing from creole?

---

### Post by Creole on 2008-03-21
My laptop is a Zepto Znote 6625 wd.
I have made a printscreen of my hardware control:

[http://cmdstud.khlim.be/~gnijs/Printscreens/HardwareControl.png](http://cmdstud.khlim.be/~gnijs/Printscreens/HardwareControl.png)
[http://cmdstud.khlim.be/~gnijs/Printscreens/HardwareControl2.png](http://cmdstud.khlim.be/~gnijs/Printscreens/HardwareControl2.png)

I hope this information is helpful. 

I don't know what drive i have, but i asked on the forum of my laptop, so i should no soon enough.

---

### Post by Creole on 2008-03-27
Up

---

### Post by Creole on 2008-03-31
Where can I check my grub config?

---

### Post by malfist on 2008-03-31
First off, your problem isn't very well explained. You state it's grub causing the issue and you know that but you don't state exactly how you know that. Second, grub doesn't deal with anything but finding the proper kernel to boot, nothing else. The kernel configurations may effect you though, but if your cd-rom isn't working in windows it's not grub. My guess is you have a bad CD-ROM or it's not plugged in good. Has the cables become loose? Pull the drive out and test it in another computer. Then post back. The default grub should work without a problem.

---

### Post by Creole on 2008-03-31
Well, I know grub is affecting my cd-rom in some kind of way, because when i fix my master boot record with a dos cd, my cd-rom works perfectly in XP.

---

### Post by danwood76 on 2008-04-01
It may be a funny option in your menu.lst?
could you post it please?
```

cat /boot/grub/menu.lst

```

---

### Post by Creole on 2008-04-06
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
# kopt=root=UUID=5a599ebc-102d-42fd-8022-73f168f9d4b4 ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=5a599ebc-102d-42fd-8022-73f168f9d4b4 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=5a599ebc-102d-42fd-8022-73f168f9d4b4 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

End's here

That's all.

---

### Post by ghost_ryder35 on 2008-04-06
u could install LILO and see if that has the same effects (damn I have bad advice today)

---

### Post by Creole on 2008-04-10
Well, ok is there a simple way of doing it, my searches haven't brought me far. If you can explain me how, i  will give it a try.

---

### Post by danwood76 on 2008-04-10
Here is a quick guide I just wrote:

```

sudo apt-get install lilo

```

will install it.
you then need to remove all UUIDs from your fstab as lilo dislikes them:
```

sudo gedit /etc/fstab

```
an example is mine:
```

# /dev/sda2
UUID=a0f4ddda-57c8-4f9e-967e-a4c710af909d /    ext3    defaults   0  1

```
you must replace each UUID with the drive reference above it so mine would then be:
```

# 
/dev/sda2    /    ext3    defaults   0  1

```
do this for each of the UUID partitions and save and exit.

then you then need to configure it:
```

sudo liloconfig

```
you want to install lilos boot record to your / partition (or your /boot if you have a seperate one) you can get that partition number from the fstab file.

you then want to install lilo to the MBR of the drive and boot linux by default.

then we need to add windows to the lilo config:
```

sudo gedit /etc/lilo.conf

```
at the bottom there are two lines to uncomment and change the /dev/hda2 to the partition your windows is on. (probably something like /dev/sda1)
You may want to tidy this bit up (ive just installed lilo to test and it looks messy to me) but I dont know what default stuff it will put in there for you.
It should auto find your linux image and set it up for you, I have several different kernels on my system so it got messy.

save that then run lilo to save the configuration:
```

sudo lilo

```

and you should be done.
restart to see what happens :)

You wont have a splash screen with lilo so you will see lots of text flying past ;)

---

