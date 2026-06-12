---
title: "GRUB Question"
date: 2007-03-14
forum: General Help
---

### Post by royrules22 on 2007-03-14
Hope this is the right place. 

My GRUB loader has many different choices. One of memtest, one for edgy and the kernel from the CD, one for it's recovery, one for the latest kernel, one for it's recovery and lastly one for Win XP Pro.

My question is that can I do a clean up and get rid of the boot-up options for the old kernels? Also how do I reorder them? I want Win XP on top so that by default it boots to XP and if I want to it goes to Ubuntu?

Thanks

---

### Post by Irony on 2007-03-14
I think when you uninstall old kernels grub menu.lst is updated, anyway if not then just go;

[PHP]gksudo gedit /boot/grub/menu.lst[/PHP]

and edit the file from there by deleting old entries and moving others.

Alternatively for the graphical method do Alt + F2 and type;

[PHP]gksudo nautilus[/PHP]

and navigate to /boot/grub/menu.lst - you can also make a backup of the list by copying the file and pasting it.

---

### Post by confused57 on 2007-03-14
> **royrules22 said:**
> Hope this is the right place. 

My GRUB loader has many different choices. One of memtest, one for edgy and the kernel from the CD, one for it's recovery, one for the latest kernel, one for it's recovery and lastly one for Win XP Pro.

My question is that can I do a clean up and get rid of the boot-up options for the old kernels? Also how do I reorder them? I want Win XP on top so that by default it boots to XP and if I want to it goes to Ubuntu?

Thanks

See this thread for where to place your Window's entry, so that it is the top entry to boot in grub:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

It would probably be a good idea to keep the newest kernel entry and the next oldest, in case you have problems booting the new kernel...if there is another kernel update, then you might want to uninstall(using Synaptic) the oldest kernel.

---

### Post by cyberdork33 on 2007-03-14
there are also options in the menu.lst file to set how many kernels to keep, and what alternative boot options are available. This way when you upgrade the kernel in the future, it automatically removes a kernel if there are more than you specify, etc.

---

### Post by 16777216 on 2007-03-14
I will attempt to do a general step by step for editing the GRUB menu. 

You have a few options.[LIST=1]
[*]Use [GrubEd]("http://ubuntuforums.org/showthread.php?t=228104")
[*]Edit the menu.lst file manualy[/LIST]GrubEd is easy to install and use any questions to do with it should be posted in [this thread]("http://ubuntuforums.org/showthread.php?t=228104").

The next option is to manually edit the menu.lst file.
I am not going to cover all of the options but, I will answer your concerns. 

As for manually editing the GRUB menu the first thing you will want to do is backup the original file
To do that open a terminal and type or cut and paste ```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```This will make a copy of the menu.lst file and rename that copy menu.lst.backup this is a fail safe to restore the menu if it gets broken.

Next we need to open the menu.lst file as root to edit it.
In the same terminal type or paste. ```
sudo gedit /boot/grub/menu.lst
```This will open Gedit with the GRUB configuration file as root so that it can be edited and saved.

This is my menu.lst file ( Yours list of OSs and the value of some options will be different than mine. )
```
splashimage (hd1,1)/boot/grub/images/aa.xpm.gz
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
default        3

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color white/black yellow/blue

#A splash image for the menu
#splashimage=(hd1,1)${BOOTPREFIX}/grub/splashimages/KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=baa37e81-47be-4d07-bbda-2db4cf22e94e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
# defoptions=quiet vga=795 splash

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title        Ubuntu, kernel 2.6.17-11-386
root        (hd1,1)
kernel        /vmlinuz-2.6.17-11-386 root=UUID=baa37e81-47be-4d07-bbda-2db4cf22e94e ro quiet vga=795 splash
initrd        /initrd.img-2.6.17-11-386
savedefault
boot

title        Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root        (hd1,1)
kernel        /vmlinuz-2.6.17-11-386 root=UUID=baa37e81-47be-4d07-bbda-2db4cf22e94e ro single
initrd        /initrd.img-2.6.17-11-386
boot

title        Ubuntu, memtest86+
root        (hd1,1)
kernel        /memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows XP Home sp2
root        (hd0,0)
makeactive
chainloader    +1

```The first option you should see is. ```
default        0
```This line tells GRUB which OS to load by default.
Numbering starts at 0 so the first OS in the list gets loaded/highlighted.
You can change this number to what ever you want as long as their that many OSs  in the list. ( Remember to start counting at 0 not 1. )

To change the order that an OS appears in the GRUB menu simply change the order that they appear in the menu.lst file.

For example here is the order I have in my file.
```
title        Ubuntu, kernel 2.6.17-11-386
root        (hd1,1)
kernel        /vmlinuz-2.6.17-11-386 root=UUID=baa37e81-47be-4d07-bbda-2db4cf22e94e ro quiet vga=795 splash
initrd        /initrd.img-2.6.17-11-386
savedefault
boot

title        Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root        (hd1,1)
kernel        /vmlinuz-2.6.17-11-386 root=UUID=baa37e81-47be-4d07-bbda-2db4cf22e94e ro single
initrd        /initrd.img-2.6.17-11-386
boot

title        Ubuntu, memtest86+
root        (hd1,1)
kernel        /memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows XP Home sp2
root        (hd0,0)
makeactive
chainloader    +1
```To make Windows first in the list simply move it to the top of the list.

```
title        Windows XP Home sp2
root        (hd0,0)
makeactive
chainloader    +1

title        Ubuntu, kernel 2.6.17-11-386
root        (hd1,1)
kernel        /vmlinuz-2.6.17-11-386 root=UUID=baa37e81-47be-4d07-bbda-2db4cf22e94e ro quiet vga=795 splash
initrd        /initrd.img-2.6.17-11-386
savedefault
boot

title        Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root        (hd1,1)
kernel        /vmlinuz-2.6.17-11-386 root=UUID=baa37e81-47be-4d07-bbda-2db4cf22e94e ro single
initrd        /initrd.img-2.6.17-11-386
boot

title        Ubuntu, memtest86+
root        (hd1,1)
kernel        /memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST <-- this can be safely removed too.
```Remember that ```
default        0
``` is the first item in the list which now is Windows so if you have changed this to any thing else you may wish to change it back.

The second thing you may want to change is the time out value, this is how long in seconds GRUB will wait at the default choice before automatically  booting your default OS.

It should look like this. ```
timeout        15
```The spaces are not important but you need at least one space between timeout and the value.

You can change this to what ever you want, for example to have a full minute to make up your mind on which OS to boot change it to, ```
timeout        60
``` this gives us a minute to decide.

As a warning do not make the value too low say 0 as this will not give you enough time to make a selection.

If you simply wish to not have a timer comment out the timeout line like this. ```
## timeout        60
```Now we have all the time in the world.

Although I don't recommend it you can delete any and all commented lines.
They start with ## or #.

The extra kernels that you don't need or use can be commented out or removed.

Example
```

title        Ubuntu, kernel 2.6.17-11-386
root        (hd1,1)
kernel        /vmlinuz-2.6.17-11-386 root=UUID=baa37e81-47be-4d07-bbda-2db4cf22e94e ro quiet vga=795 splash
initrd        /initrd.img-2.6.17-11-386
savedefault
boot

## title        Ubuntu, kernel 2.6.17-11-386 (recovery mode)
## root        (hd1,1)
## kernel        /vmlinuz-2.6.17-11-386
## root=UUID=baa37e81-47be-4d07-bbda-2db4cf22e94e ro single
## initrd        /initrd.img-2.6.17-11-386
## boot

## memtest used to be here.

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows XP Home sp2
root        (hd0,0)
makeactive
chainloader    +1
```After you have made your changes save the file, close Gedit, and reboot.

If any of the changes you have made break GRUB simply follow the instructions that I found in [**this**]("http://www.ubuntuforums.org/showpost.php?p=2295386&postcount=7") post.

---

### Post by cyberdork33 on 2007-03-14
> **16777216 said:**
> To make Windows first in the list simply move it to the top of the list.

```
title        Windows XP Home sp2
root        (hd0,0)
makeactive
chainloader    +1

title        Ubuntu, kernel 2.6.17-11-386
root        (hd1,1)
kernel        /vmlinuz-2.6.17-11-386 root=UUID=baa37e81-47be-4d07-bbda-2db4cf22e94e ro quiet vga=795 splash
initrd        /initrd.img-2.6.17-11-386
savedefault
boot

title        Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root        (hd1,1)
kernel        /vmlinuz-2.6.17-11-386 root=UUID=baa37e81-47be-4d07-bbda-2db4cf22e94e ro single
initrd        /initrd.img-2.6.17-11-386
boot

title        Ubuntu, memtest86+
root        (hd1,1)
kernel        /memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I would put your Windows entry ABOVE the DEBIAN AUTOMAGIC KERNELS LIST portion as it would be removed everytime you automagically update the menu.lst file... and don't remove the "### BEGIN AUTOMAGIC KERNELS LIST" and "### END AUTOMAGIC KERNELS LIST" otherwise when a new kernel comes out, it will not correctly update your file.

Following the advice of the file itself:
```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```

As such, the best place for your DEFAULT boot option is ABOVE the "### BEGIN AUTOMAGIC KERNELS LIST"  and set default = 0. This way, when the list is automagically updated, kernels can be removed / added, and it will not change the fact that your windows boot line is the default.

---

### Post by 16777216 on 2007-03-14
Thank you for that correction I am glad you caught that.
I am sorry for the mistake.

---

### Post by JohnPhys on 2007-03-14
Also, if he wants to reduce the number of automagic kernels, he can change the "howmany" line in the menu.lst file (don't uncomment!), and then update-grub.

I keep mine at 2, so that when a new kernel is installed, I still have the previous one in case something goes wrong with the new one.

---

### Post by cyberdork33 on 2007-03-14
> **JohnPhys said:**
> Also, if he wants to reduce the number of automagic kernels, he can change the "howmany" line in the menu.lst file (don't uncomment!), and then update-grub.

I keep mine at 2, so that when a new kernel is installed, I still have the previous one in case something goes wrong with the new one.

Exactly what I do... I turn the alt boot lines off too, but that's because I can edit the grub lines if I really needed to...

---

