---
title: "Default OS boot help please."
date: 2007-05-14
forum: General Help
---

### Post by PerlMountain on 2007-05-14
I read a lot of info but I'm still not totally clear so I want to ask before I wreck what took a week to build.

I want to boot up Xp before Kubuntu.

(**BTW, I changed timeout to 60 from 10. I cannot save my changes. Can you help me with that? I was never asked for ROOT passwd in Konsole**).

[IMG]http://perlmountain.com/.linux/menu.jpg[/IMG]

[list]
[*]Here's the output of menu.lst:[/list]

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
timeout		60

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
#      password --xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
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
# kopt=root=UUID=0a798f59-04de-4221-9729-e377031348db ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0a798f59-04de-4221-9729-e377031348db ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0a798f59-04de-4221-9729-e377031348db ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

Thank you :)

---

### Post by phidia on 2007-05-14
Use > sudo gedit menu.lst to get a editor with read/write ability.
Sorry you're in kubunt so use kedit instead of gedit.
Generally the 1st os listed in menu.lst is the default os.

---

### Post by EndPerform on 2007-05-14
> **phidia said:**
> Use  to get a editor with read/write ability.
Generally the 1st os listed in menu.lst is the default os.

The default 0 line is what tells GRUB to boot the first OS.  In the example posted, there are 3 entries listed. If default 0 were changed to default 2, it should boot up XP.  I believe, though, that if a kernel upgrade or patch comes out, this change would need to be made again

---

### Post by ajgreeny on 2007-05-14
Don't use **sudo** for a gui application.  In kubuntu for a kde app use **kdesu,** and for a gnome app use **gksudo** instead.  If you look at:-
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
you'll see the possible problems that can occur if you use sudo.  It will be **kdesu kate** as well not **kedit.**

---

### Post by PerlMountain on 2007-05-14
> **phidia said:**
> Use  to get a editor with read/write ability.
Sorry you're in kubunt so use kedit instead of gedit.
Generally the 1st os listed in menu.lst is the default os.Thank you. I cannot load menu.lst with kedit. I will search more. ```
perl1-compaq@perl1-compaq:~$ sudo kedit /boot/grub/menu.lst
Password:
Sorry, try again.
Password:
sudo: kedit: command not found
perl1-compaq@perl1-compaq:~$ sudo kedit menu.lst
sudo: kedit: command not found
perl1-compaq@perl1-compaq:~$


```

[quote=EndPerform]If default 0 were changed to default 2, it should boot up XP. I believe, though, that if a kernel upgrade or patch comes out, this change would need to be made again[/quote]Very clear, thank you.

And if it _doesn't_ boot up for some reason, then I know it's just a bootloader problem and not an OS problem, so I'll just boot up with [**SuperGrub Bootloader**](http://supergrub.forjamari.linex.org), because that sounds like the correct thing to do, right?

I just need to be able to edit menu.lst. Yesterday, I edited it with Kate I believe, using [list][*]kdesu kate /boot/grub/menu.lst[/list] but today it will not open like that.

(This is a new install since yesterday).

Thank you,

---

### Post by PerlMountain on 2007-05-14
> **ajgreeny said:**
> It will be **kdesu kate** as well not **kedit.**

Thank you. I cannot open menu.lst using:```
kdesu kate /boot/grub/menu.lst
```
Result:```
perl1-compaq@perl1-compaq:~$ kdesu kate /boot/grub/menu.lst
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```
I will reboot and try again.

---

### Post by PerlMountain on 2007-05-14
> **EndPerform said:**
> The default 0 line is what tells GRUB to boot the first OS.  In the example posted, there are 3 entries listed. If default 0 were changed to default 2, it should boot up XP.  I believe, though, that if a kernel upgrade or patch comes out, this change would need to be made again

default 0 loads Kubuntu.
default 2 selects 'memtest86+'

So. I tried default 3 of course.

That selects 'Other operating systems:', which, I guess is Ok (for the laptop). There is no counter.

I would like to know how to boot right into Xp though, because I let my desktop warm up and do it's startup routine while I'm getting my coffee. (Today, I'm working on my slave laptop).

---

### Post by nikhilk on 2007-05-14
Just change the default to 4.

---

### Post by EndPerform on 2007-05-14
> **PerlMountain said:**
> default 0 loads Kubuntu.
default 2 selects 'memtest86+'

So. I tried default 3 of course.

That selects 'Other operating systems:', which, I guess is Ok (for the laptop). There is no counter.

I would like to know how to boot right into Xp though, because I let my desktop warm up and do it's startup routine while I'm getting my coffee. (Today, I'm working on my slave laptop).

My mistake.  I forgot about those other entries Ubuntu puts in there (I trim my list down).  As mentioned, change it to 4 and you should be set to go.

---

### Post by PerlMountain on 2007-05-14
Ah yea, perfect. Default 4 :)

Thank you guys! Actually, now I know 3 different ways to do it so that's *really* cool.

I will have my slave laptop 'hold' and ask me what to do and I will have my desktop boot to Xp if I don't tell it something else within 60 seconds.

Hey, thanks !

---

