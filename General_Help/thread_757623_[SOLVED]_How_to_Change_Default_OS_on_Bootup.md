---
title: "[SOLVED] How to Change Default O/S on Bootup"
date: 2008-04-17
forum: General Help
---

### Post by Wainui on 2008-04-17
Hi all,

I have **Vista **and** Ununtu **Dual Boot on the same HDD. Vista was installed first.
On Bootup, without selecting an O/S from the Menu, the system will boot the Ubuntu O/S, which I presume is set as the Default O/S. I would like to change this to** Vista **as the Default O/S on bootup.
I have tried the various options suggested on the Startup screen but Ubuntu still boots up
as the default O/S.

Any ideas.

Thanks.

---

### Post by TeoBigusGeekus on 2008-04-17
Please type 
```
sudo gedit /boot/grub/menu.lst
```
in a terminal and post us the content of the file.

---

### Post by zvacet on 2008-04-17
[Here]("http://louboldt.com/ilinuxgrub.htm#xp1st") or install startupmanager with synaptic and do it with it.

---

### Post by Wainui on 2008-04-17
Thanks guys,

I will try out your suggestions and get back to you.

Cheers.

---

### Post by Wainui on 2008-04-17
I opened **Application** >** Accessories **> **Termina**l
Could not find the word **Backup** so I typed it in and an error message said : **"Backup command not found"**

Where do I go from here ? :(

---

### Post by Wainui on 2008-04-17
Teo,

I typed what you suggested in the **Terminal**, it was blank. :(

---

### Post by forrestcupp on 2008-04-17
> **Wainui said:**
> Teo,

I typed what you suggested in the **Terminal**, it was blank. :(

if you get a grub menu at all when you start your computer, it couldn't be empty.  Try copy and pasting it instead of typing it.  To paste in the terminal, press Shift+Insert.
```
gksu gedit /boot/grub/menu.lst
```

You may have typed **menu.1st** with a number one instead of **menu.lst** with the letter 'l' which is what it should be.

Post the contents, and we'll tell you how to make it have Windows as your default.

---

### Post by zvacet on 2008-04-17
> Could not find the word Backup so I typed it in and an error message said : "Backup command not found"

You don´t suppose to type it.It is explanation of command below.Same for edit...
Why didn´t try to install startupmanager?

---

### Post by forrestcupp on 2008-04-17
> **zvacet said:**
> 
Why didn´t try to install startupmanager?
Awesome!  I didn't know about startup manager.  That's a great utility.  It should be included by default.

---

### Post by Wainui on 2008-04-18
OK, Here goes :

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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e638c778-f7cc-4a8b-ada4-73dba5bb3aa3 ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e638c778-f7cc-4a8b-ada4-73dba5bb3aa3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e638c778-f7cc-4a8b-ada4-73dba5bb3aa3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by TeoBigusGeekus on 2008-04-18
```

...
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0
....
```

Change the last line to

```
default 3
```

and save the file. 
Reboot and see what happens.

---

### Post by Wainui on 2008-04-18
Teo,

I did that, restarted and this time** "Other Operating System"** was highlighted on the **Startup Menu** -not Windows Vista.
And then I got this : 
[B]Error 11 unrecognised device.
Press any key to continue.[/B]

---

### Post by TeoBigusGeekus on 2008-04-18
Change the line to
```
default 4
```

---

### Post by Wainui on 2008-04-18
Yup, thats fixed it. 
Many Thanks Teo :guitar:

---

### Post by TeoBigusGeekus on 2008-04-18
Anytime...
Don't forget to mark the thread as solved.

---

### Post by forrestcupp on 2008-04-18
Well, that method works for a stable release, but if you ever use a beta version of Ubuntu, like Hardy is right now, you will end up having a lot of kernels added to the list.  So having a default of 4 will just end up being an old kernel, and the 1st time one is added, it will become the "Other Operating Systems" thing which will give an error.

It is a much better method to leave the default as 0 and move the lines for Windows to before the automagic kernel list starts.

In your text editor, you should **cut** these lines
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1
```
And **paste** them *before* these lines
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

```
That way you never have to worry about changing it again if a new kernel is added.

But honestly, I just found out about the Startup Manager from this thread, and it's amazing.  It's a GUI that lets you just select whatever OS you want to be default, and it does all of that for you.  You can set many other grub things with it too.  I'm sold on the startup manager
```
sudo apt-get install startupmanager
```

---

