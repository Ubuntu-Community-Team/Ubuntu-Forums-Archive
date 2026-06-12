---
title: "booting/grub problems"
date: 2007-05-18
forum: General Help
---

### Post by Westerberg on 2007-05-18
when I try to boot into ubuntu from grub, the screen goes black, the words "Starting up . . . " appear, and then . .. nothing.  I get dumped out at my comp's splash screen and then back into the grub options menu.  I basically go in a loop.

The same thing happens when I try to boot to ubuntu recovery mode.  There's some possibly relevant information outputted to the screen, but how can I capture it before it disappears into ether? 

Something similar happens when I try to reinstall Feisty from CD.  I get to the install menu and select "Install."  The words "loading kernel . . ." appear, the CD drive starts whirring, the screen goes black and then I get dumped out at the splash screen and back to the install menu.

Using Ext2IFS in Windows  I was able to check the /var/log/message and /var/log/dmesg files, but they're empty.  Are there any other files that might contain relevant information?

Here's the content of my /boot/grub/menu.lst
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=UUID=2f3c5011-2c5b-4367-be6a-45ad480139b4 ro

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
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2f3c5011-2c5b-4367-be6a-45ad480139b4 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=2f3c5011-2c5b-4367-be6a-45ad480139b4 ro single
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



Any ideas?

---

### Post by mbradlcu on 2007-05-19
I just had the same problem but the cause may be totally unrelated,, this was on a ibm 335 server (I think) anyway it had a bios boot system, I had to disable it and grub worked fine.
if you haven't already edit the boot loader parameters, if you don't know, hit "e" at the grub prompt, select the second line using the arrows, and remove "splash" and "quiet", hit enter and then the "B" key. hopefully it will display some useful info.

---

### Post by snazzed on 2007-05-19
Same issue:

I'll see if I can disable the "BIOS Boot" as pointed out in the post above.


1999 IBM Aptiva
AMD K6-2 500Mhz
192MB RAM
HD 10G
Kbd: US:international, PS2 / USB
Mouse: Logitech USB
Video: Voodoo 3 something or other
Ubuntu Server is the only install. No other OS

Was booting Win98 just fine. Wiped it, installed Ubuntu Server. POST ok, Grub lets me choose which Kernel to load, then very quickly flashes "Starting up" and then reboots.

Attempted Solutions:
- Using a Live CD, and re-installing GRUB
- replacing hard drives
- Install XUbuntu instead
- Use LiveCD, poke around the file system...
- couldn't find a grub.conf in /etc/
- /initrd/ was empty?!

Thanks
Snazzed

---

### Post by daschmidty on 2007-05-21
If the machine is older then i686 equivalent, you will need to "downgrade" the kernel to make it work. To do this, pop in a server cd or alternate install cd and go into rescue mode. Execute a shell on your root parition and use the following commands
```
apt-get install linux-386
apt-get remove linux-server
```
this will take awhile but will leave you a working system.

---

### Post by ghell on 2007-05-21
When I tried to put Edgy on a Compaq Deskpro (500mhz, 64mb ram, es1869 sound chip, just about capable of windows 98 ) I had similar problems, it would get stuck at detecting cd drive in the alternate installer and the live cd just wouldn't run. I could install breezy and upgrade up to edgy (feisty wasn't final at the time) so you may be able to do this if daschmidty's suggestion does not work.

---

### Post by snazzed on 2007-05-22
Props!  That did it.  Thanks daschmidty!  I can't believe it was such a simple problem but I guess you have to KNOW the kernels capabilities to know what it won't do.

Thanks again

Snazzed

> **daschmidty said:**
> If the machine is older then i686 equivalent, you will need to "downgrade" the kernel to make it work. To do this, pop in a server cd or alternate install cd and go into rescue mode. Execute a shell on your root parition and use the following commands
```
apt-get install linux-386
apt-get remove linux-server
```
this will take awhile but will leave you a working system.

---

