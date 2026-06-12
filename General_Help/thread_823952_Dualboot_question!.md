---
title: "Dualboot question!"
date: 2008-06-09
forum: General Help
---

### Post by sale666 on 2008-06-09
Hello i want to dualboot xp and ubuntu and now i allready have xp instaled on my 500gb hdd and i want to install ubuntu on my second 200gb hdd ...

but the question is... will Grub give me the option to boot into xp? or do i need to do something first? thanks!

---

### Post by inportb on 2008-06-09
The GRUB installer should be able to detect and write an entry for Windows. I haven't tried two-disk systems with recent Ubuntus, so I can't tell you exactly how GRUB will be installed, but the stage 1 loader might be installed into the MBR of the first harddrive, and boot stage 1.5 off the second harddrive.

---

### Post by sale666 on 2008-06-09
Ok thanks! ill be back at ya! just finished burning the iso to dvd and off to installing =)... lets see what happens! if it does not show me xp ull help me make it work :D

---

### Post by whitey on 2008-06-09
What you looking to do should be completely automated in the install, the grub installer has become very intuitive the last couple years.  The only thing I've had an issue with lately is SATA, but usually its the motherboards fault, and all you have to do is set your boot preference.

---

### Post by sale666 on 2008-06-09
ok now this is the case:

2 sataII drives

SataII 1:Hdd seagate 500GB - windows xp Ntfs partition
SataII 2:Hdd seagate 200GB - Ubuntu 8.04 Ext3 partition

Problem:
Only linux boots... xp is not shown as choice! help?

---

### Post by tom66 on 2008-06-09
Can you navigate to /boot/grub and post menu.lst here please.

---

### Post by sale666 on 2008-06-09
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
# kopt=root=UUID=694edc3f-8963-4873-a1ec-d8d436af1e0f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=694edc3f-8963-4873-a1ec-d8d436af1e0f ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=694edc3f-8963-4873-a1ec-d8d436af1e0f ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=694edc3f-8963-4873-a1ec-d8d436af1e0f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=694edc3f-8963-4873-a1ec-d8d436af1e0f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by tom66 on 2008-06-09
Hmm it seems Windows hasn't been automatically detected. Try adding this:

```

title ---------------------
root

title Windows XP
root (hd0,0)
chainloader +1

```

---

### Post by sale666 on 2008-06-09
where do i add that? no matter or in secific line?

---

### Post by sale666 on 2008-06-09
ok the problem again... the thing i HATE the most on all linuxes... YOU DO NOT HAVE THE PERMISION TO SAVE THIS YOU ARE NOT THE OWNER! no im the Nasa guy hacking in my granmas pc and changing her boot loader...

How do i save this... i simply hate this stuff the permision crap...

---

### Post by nerd0795 on 2008-06-09
I know there is a code to edit it with terminal.  I can't remember when I find it out I will reply.

---

### Post by nerd0795 on 2008-06-09
```
sudo gedit /boot/grub/menu.lst
```

This is it.  I hope this gives u the permission.  Please do not blame me if something goes wrong.  This is my first time helping someone.  Please backup your menu.lst file or whatever it's called.

---

### Post by sale666 on 2008-06-09
ok done it and xp appeard but it broke my Ntloader...
tryed puting in xp and fixboot and fixmbr and still my ntldr is not working...

I must say ubuntu vs vista User Account Control ("uac") id say ubuntu is FAR more a pain in the *** when it comes to control... i cannot access my own stuff without a password! wtf! soon it will ask me for a password to open a folder and empty the recycle bin :lolflag:...

what do i do with this now? i got now the same menu but doubled with options like ubuntu ,ubntu safe than memtest than all same 3 options again
than ----------------- than xp that is not working... help :(

---

### Post by nerd0795 on 2008-06-09
I don't think this is correct but I heard that XP has a hard time booting if it's not on C: drive.  I don't know if this is correct.

Maybe ask another...  I don't know...

---

### Post by nerd0795 on 2008-06-09
> stuff without a password! wtf! soon it will ask me for a password to open a folder and empty the recycle bin

I know this is not on topic but actually I can't delete my trash... It's not giving me permission to delete a folder! (just a program I uninstalled >.<)

---

### Post by sale666 on 2008-06-09
> **nerd0795 said:**
> I know this is not on topic but actually I can't delete my trash... It's not giving me permission to delete a folder! (just a program I uninstalled >.<)
LMAO :lolflag:


so what do you suggest i try doing with this damn xp loader?

---

### Post by nerd0795 on 2008-06-09
I honestly don't know :(

I'm still a noob to linux so I don't know that much and i have never used XP only vista and me.

---

### Post by tom66 on 2008-06-10
It keeps your computer safe. Permissions stop rogue programs from taking over the computer, reducing any security risk. 

Ok, open a terminal, type gksudo nautilus /boot/grub then do what you need to do.

---

### Post by KeyserSoze93 on 2008-06-10
```
sudo gedit /boot/grub/menu.lst
```
(password)

Put a blank line and then this:

```

title Windows XP
root (hd0,0)
chainloader +1
makeactive
```

At the end...

The save.

Reboot and Win XP should be at the bottom of the list...

---

