---
title: "OH MY GOD - yet another Grub error 17"
date: 2007-11-24
forum: General Help
---

### Post by bigbob6383 on 2007-11-24
okay, i've been looking around for the past couple of hours on the web and have found multiple reasons and different occurrences of the Grub error 17. But the problem is that they do not apply to my problem!

Anyway... I just finally installed ubuntu 7.10 on my pc for the first time and was really excited to use it. so i reboot from the live cd i used to install it and Grub loads right up with no problem (YAY) and i go into ubuntu and do some stuff for like 10 minutes. Then (since i was planning on installing another linux distribution on my other unallocated space) i restarted and loaded up my other live-cd for backtrack2. i found out i needed to make my partition myself, so i go and reboot *again* - and this time grub starts up like it would usually but after its 2 lines of "Grub loading up" or whatever, it prints **"Error 17"** and just stops completely.

I can't do anything from here **at all** except boot into a live cd (which i'm on right now).

If anyone had this same issue and can help, by all means, feel free to share anything you did.

(i attached a pic of my partition setup if it'll help at all)

---

### Post by teryowen on 2007-11-24
view the file /media/disk/boot/grub/menu.lst

type this into terminal:
cat /media/disk/boot/grub/menu.lst

copy and paste the output here.

---

### Post by bigbob6383 on 2007-11-24
ubuntu@ubuntu:~$ cat /media/disk/boot/grub/menu.lst
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
# kopt=root=UUID=615b721a-4840-401f-8bef-fb1bfe770bc6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=615b721a-4840-401f-8bef-fb1bfe770bc6 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=615b721a-4840-401f-8bef-fb1bfe770bc6 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

:confused:

---

### Post by teryowen on 2007-11-24
where you have the following written:

```
## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=615b721a-4840-401f-8bef-fb1bfe770bc6 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet
```

edit the root line
so instead of
```
root (hd0,5)
```

change it to
```
root (hd0,4)
```

i think this should work to edit the file
type this into terminal
gedit /media/disk/boot/grub/menu.lst

---

### Post by bigbob6383 on 2007-11-24
okay, well now when i try to save it i get:

"Could not save the file /media/disk/boot/grub/menu.lst."
"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

](*,)

---

### Post by teryowen on 2007-11-24
then type the following in terminal
```
sudo gedit /media/disk/boot/grub/menu.lst
```

if that doesnt work
type the following into terminal and copy and paste the output
```
mount
```

---

### Post by bigbob6383 on 2007-11-24
thanks - the sudo worked :)

is that it? can i reboot now?
was it really only one number that threw Grub off??? wow

---

### Post by teryowen on 2007-11-24
reboot see what happens, i think it should work.

The way your grub was set up was that it was booting of a wrong partition, which i guess is why it gave the error.

---

### Post by bigbob6383 on 2007-11-24
:x:mad::x:mad::x:mad::x
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
i still get **"ERROR 17"**

I have this as the code:
```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=615b721a-4840-401f-8bef-fb1bfe770bc6 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=615b721a-4840-401f-8bef-fb1bfe770bc6 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet
```
but it still does not work :cry:

---

### Post by teryowen on 2007-11-24
try one more thing:

edit where it says:
root=UUID=615b721a-4840-401f-8bef-fb1bfe770bc6

to:
root=/dev/sda5

look here for some more help [http://justlinux.com/forum/showpost.php?p=869980&postcount=6](http://justlinux.com/forum/showpost.php?p=869980&postcount=6)

otherwise i think you might have to reinstall.

---

### Post by ronmarley1 on 2007-11-24
In looking at your screen capture, I don't see a root (/) partition?

---

### Post by teryowen on 2007-11-24
i think thats because he was booting off the live CD and posted the image while in QParted to show the structure.

---

### Post by bigbob6383 on 2007-11-24
.......okay well i tried this because the hard drive space for the /root partition was actually the third in line from the start of my entire drive:
```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```
but with no avail...

unless anyone has any other ideas, i guess i'll just have to reinstall all of ubuntu like you said - but my question is why would this make any difference than the 1st time i installed???

and to ronmarley1 - the screenshot was from GParted to just show how all my partitions were set up. i don't actually know why there's not a /root partition there, but i used the *"Guided: Use largest continuous space"* option when installing ubuntu so...i dunno

---

### Post by meierfra on 2007-11-24
>  Then (since i was planning on installing another linux distribution on my other unallocated space) i restarted and loaded up my other live-cd for backtrack2. i found out i needed to make my partition myself, so i go and reboot again -

After you had successfully booted into ubuntu: Did you attempt to install "backtrack2"? Did you do any partitioning?

---

### Post by bigbob6383 on 2007-11-24
after loading up the backtrack livecd all i did was go into "install" and looked to see what i had to do to install it - i did not actually edit anything

when i rebooted to go into windows and edit my unallocated space, i then came to the Grub error 17...

---

### Post by Diabolis on 2007-11-24
this might help:

[http://ubuntuforums.org/showthread.php?t=577721](http://ubuntuforums.org/showthread.php?t=577721)

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by meierfra on 2007-11-24
Change "root (hd0,3)" back to "root (hd0,4)".


Then reinstall grub via:

```
sudo grub
root (hd0,4)
setup (hd0)
quit

```

---

### Post by bigbob6383 on 2007-11-24
> **meierfra said:**
> Change "root (hd0,3)" back to "root (hd0,4)".


Then reinstall grub via:

```
sudo grub
root (hd0,4)
setup (hd0)
quit

```

this is exactly what i found searching on google like 20 minutes ago and it worked perfectly!!!!
I'M SO FRICKIN HAPPY!!!!!!!!:biggrin:\\:D/:biggrin:

Thanks for all the help everyone!!!

---

