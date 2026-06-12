---
title: "[SOLVED] Option to reboot into windows while logging off ubuntu"
date: 2006-12-01
forum: General Help
---

### Post by MiniMe on 2006-12-01
I currently have a dual boot Ubuntu/Windows system. To boot into windows I select it from the grub menu. Is there a way I add an option to reboot into windows from the log off manager within ubuntu. So that grub would do something like automatically choose windows during the next boot up. That way, from within ubuntu I could just select something like "reboot into windows", go get a coffee and when I return, the computer will have windows booted. Rather then me having to sit and wait for Ubuntu to shut down and select windows manually from grub. 

That would be neat wouldn't it?

I don't want to change the default in grub to windows because I usually boot up ubuntu. 

Cheers!

---

### Post by hxx4 on 2006-12-01
That would be pretty cool. I'm thinking that you would need to write a script that would execute upon clicking an icon named "Reboot to Windows". This script would edit /boot/grub/menu.lst to change the default boot OS to Windows and then call the reboot command. In Windows, you would need to create a program that loads on startup to change the default boot OS in /boot/grub/menu.lst on your ubuntu partition back to ubuntu. I'm not familiar with how to write the script or how to create a program in Windows that would be able to access and edit /boot/grub/menu.lst on your ubuntu partition. I'm also unsure how experienced you are (possibly more so than I) so I'll just leave it at that. I hope any ideas I provided could help.

---

### Post by dbott67 on 2006-12-01
It would be a nice option, however, you could hack together a little script that does it for you.

1. Backup your existing **menu.lst** file:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.orig
```

2. Make a 2nd copy of your **menu.lst** file called **menu.win**:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.win
```

3. Edit the **menu.win** file to boot into Windows (in my case I would have to change the default [COLOR="Red"]0[/COLOR] to an [COLOR="Red"]8[/COLOR]):
```
dbott@dapper:~$ cat /boot/grub/menu.lst
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
[COLOR="Red"]**default         0**[/COLOR] [COLOR="Blue"]<--- change this to the ordinal number of your Windows partition.
Count every instance of 'title' starting at zero.
Keep scrolling down to see all of my menu options[/COLOR]

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
# kopt=root=/dev/sda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

[COLOR="Red"]## This is ordinal 0 (the default boot item)[/COLOR]
title           Ubuntu, kernel 2.6.15-27-686
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/sda7 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-686
savedefault
boot

[COLOR="Red"]## This is ordinal 1[/COLOR]
title           Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/sda7 ro single
initrd          /boot/initrd.img-2.6.15-27-686
boot

[COLOR="Red"]## This is ordinal 2[/COLOR]
title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda7 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

[COLOR="Red"]## This is ordinal 3[/COLOR]
title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda7 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

[COLOR="Red"]## This is ordinal 4[/COLOR]
title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda7 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

[COLOR="Red"]## This is ordinal 5[/COLOR]
title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/sda7 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

[COLOR="Red"]## This is ordinal 6[/COLOR]
title           Ubuntu, memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
[COLOR="Red"]## This is ordinal 7[/COLOR]
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
[COLOR="Red"]## This is ordinal 8[/COLOR]
title           Windows NT/2000/XP (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```

4. Write a little shell script to replace the current **menu.lst** file with the **menu.win** file:
```
#!/bin/bash
sudo mv /boot/grub/menu.lst /boot/grub/menu.bak
sudo cp /boot/grub/menu.win /boot/grub/menu.lst
```

Of course, I have not tested this and I'm sure that there are much more elegant and efficient ways of doing it, but I think you get the idea.

5. You could then write a script that 'reverses' the 2 files upon startup into Ubuntu.

-Dave

---

### Post by MiniMe on 2006-12-02
Thanks for the replies! I might just try my hand at this.

---

### Post by airtonix on 2007-12-21
even simplier way is this : 

> sudo grub-reboot <num>

where <num> is the number of the grub entry item that describes the windows bootsector.

---

### Post by lvleph on 2007-12-21
The next thing would be to create a button in the shudown menu of both Ubuntu and Windows. Good luck doing it in Windows.

---

