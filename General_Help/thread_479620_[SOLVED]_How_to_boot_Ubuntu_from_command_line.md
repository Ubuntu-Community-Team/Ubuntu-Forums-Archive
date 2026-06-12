---
title: "[SOLVED] How to boot Ubuntu from command line?"
date: 2007-06-20
forum: General Help
---

### Post by Spaceman9 on 2007-06-20
I installed the Ubuntu Alternate CD with Wubi and everything went perfectively. I rebooted my computer and got the screen that that says 1. Windows, 2. Grub. I chose Grub and got a prompt that says grub. 

What do I do now? What do I have to type to boot Ubuntu?

I installed Ubuntu on my C: hard drive where I have a full install of Windows 98SE.

---

### Post by CrazyGuy123 on 2007-06-20
What version did you use?  It should say "Ubuntu" in the boot menu, not grub.

If you didn't use the latest version, try uninstalling and reinstalling with the latest one from [www.wubi-installer.org](www.wubi-installer.org) .  You can save the downloaded iso do you don't have to download it again if you like.


EDIT:  hang on - I didn't read you had Win98SE - the above probably doesn't apply there.

---

### Post by Spaceman9 on 2007-06-20
Hey CrazyGuy123 thanks for the help.

These are the versions I'm using. Wubi-7.04-test3.exe and ubuntu-7.04-alternate-i386.iso. 

You're right the menu says 2. ubuntu not grub.

---

### Post by ago on 2007-06-20
Can you please try the latest installer from the website?

---

### Post by Spaceman9 on 2007-06-20
Hey ago thanks for the help.

I D/L'ed the wubi file from the link supplied by CrazyGuy123. I uninstalled the wubi/ubuntu install on C then I defraged my hard drive and rebooted my computer.

On boot up i got the same screen asking about 1. windows, 2. ubuntu. I thought that would be gone after I uninstalled wubi/ubuntu on my hard drive.

I got back into Windows, ran Wubi-7.04.01.exe and everything went perfectly. The little window popped up, I clicked on reboot, the 1.windows, 2.ubuntu menu came up, I chose 1 for windows and as soon as the screen where the curser comes on in the middle of the screen my computer locks up.

I did a warm reboot, chose 1. windows again and it booted without problems. I did a reboot from the Start menu in windows then 2.ubuntu and got a message saying grub.exe could not be found or was corrupt and there was an error in line 8 in my config.sys file. So that's as far as I got. Still can't boot Ubuntu.


This is what's in my config.sys file.
 [menu] 
 menucolor=15,0 
 menuitem=windows,Windows 
 menuitem=grub,Ubuntu 
 menudefault=windows,30 
 [grub] 
 device=grub.exe 
 [windows] 
  
 [menu] 
 menucolor=15,0 
 menuitem=windows,Windows 
 menuitem=wubildr,Ubuntu 
 menudefault=windows,30 
 [wubildr] 
 device=wubildr.exe 
 [windows] 
 
This is what's in my autoexe.bat file.
SET PATH=%PATH%;c:\progra~1\common~1\gtk\2.0\bin

This is what's in the menu.lst from the wubi/boot/grub folder.
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
timeout		1

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
# kopt=find=/wubi/boot/linux ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=find --set-root --ignore-floppies /wubi/boot/linux

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

title Ubuntu
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux quiet ro
initrd /wubi/boot/initrd
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso quiet splash ro
initrd /wubi/boot/initrd
boot

This is what's in the menu.lst from the wubi/boot/winboot folder.
hiddenmenu
default 0
timeout 0
fallback 1

title find /wubi/boot/grub/menu.lst
find --set-root --ignore-floppies /wubi/boot/grub/menu.lst
configfile /wubi/boot/grub/menu.lst

---

### Post by ago on 2007-06-21
Do you have grub.exe and menu.lst under c:\ ?

The menu.lst under C:\ should read something like:

find ...
title ...
configfile /wubi/boot/grub/menu.lst

---

### Post by Spaceman9 on 2007-06-21
I couldn't find grub.exe in C:\ but I did have menu.lst in C:\. and this is what what's in it

hiddenmenu
default 0
timeout 0
fallback 1

title find /wubi/boot/grub/menu.lst
find --set-root --ignore-floppies /wubi/boot/grub/menu.lst
configfile /wubi/boot/grub/menu.lst

I decided to try everything all over again with the 1. windows, 2. ubuntu screen so I uninstalled wubi/ubuntu and deleted everything from my config.sys file (don't worry I know what I'm doing with that sucker from my days with Microsoft DOS. Have you ever tried to install a hand scanner in DOS without plug n play? I'm lucky to have survived it!) and I deleted the menu.lst file in C:\. 

Sometime tomorrow I'll defrag my hard drive again and run wubi to install ubuntu again.

 I have a question though before I do anything else. I saw your post about Wubi-7.04-minefield-214.59.exe. Should I try using minefield or should I just use Wubi-7.04.01.exe for now?

---

### Post by ago on 2007-06-21
> **Spaceman9 said:**
> I couldn't find grub.exe in C:\ but I did have menu.lst in C:\. and this is what what's in it

menu.lst is fine. See if you have grub.exe in c:\wubi\boot\winboot, otherwise you can get it here: 

[http://download.gna.org/grub4dos/grub4dos-0.4.3-2007-06-17.zip](http://download.gna.org/grub4dos/grub4dos-0.4.3-2007-06-17.zip)


> I have a question though before I do anything else. I saw your post about Wubi-7.04-minefield-214.59.exe. Should I try using minefield or should I just use Wubi-7.04.01.exe for now?
They are basically the same, when a minefield is "mature" enough and there are not many complaints we merge the code to the "stable" branch. We do have several minefields for each stable release, and keep adjusting them until we are happy and then they get "promoted", this is what happened to 214.59.

---

### Post by Spaceman9 on 2007-06-21
Okay I have grub4dos now. What do I do with it?

---

### Post by ago on 2007-06-21
Extract grub.exe into c:\, then try to reboot.

---

### Post by Spaceman9 on 2007-06-21
Okay thanks but right now I have to get sleep before I die from Linux over dose. Either way I'll let you know what happens tomorrow. Thanks for your help.

---

### Post by Spaceman9 on 2007-06-21
Okay I installed ubuntu again using wubi and this time i was able to start the boot process into ubuntu. It looks like it loaded the kernel and then put up this text.

boot
loading, please wait
no RAID disk

[  14.496000] hdc: error coad: 0x70 sense_key: 0x03 asc: 0x11 ascg: 0x00
[  14.496000] Buffer I/O error on device hdc, logical block 330548

There were 16 lines of text like that with each pair sharing the same first numberand each new pair had a higher number. About 2 minutes later it put up this text. 

	 Check root=bootarg cat /proc/cmdline
	or missing modulos, devices: cat /proc/modules ls /dev
ALERT! Does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debin 1:1.1.3) Built-in shell (ash)
Enter 'help' for a list of commands.

/bin/sh: can't acess tty; job control turned off
(initramfs) (this had a blinking curser after it)

About a minute later the screen went blank. I waited about 3 minutes but nothing else happened so I did a warm reboot, went back into Windows and made this post. At least It's starting to boot Ubuntu so we're making progress.

---

### Post by ago on 2007-06-22
Ok first issue was due to the fact that you had an old installation of wubi, and config.sys was not cleared properly upon uninstallation (which is a known bug), so when you tried it again, the old menu was in place which was pointing to files that did not exist anymore. Easy fixed by manually cleaning config.sys before reinstalling.

As fpr the second error looks like the ISO is bad (strange since it would not pass the md5 test otherwise...) or maybe it was copied over a HD block which was bad. I assume that hdc is your CD rom. Check zenigata.log and lupin.log, there should be some error message when trying to mount the ISO.

You can try download again.

---

### Post by Spaceman9 on 2007-06-24
I don't know what happened. I was trying different things to get the bootup menu to boot Ubuntu and then there was no menu. No nothing. I decided since I'd have to reinstall Windows to do a full disk install of Ubuntu from the live cd first. I found out Ubuntu works with all my hardware cept I don't have an Ethernet card so I couldn't use my dsl modem but I'm sure it will work once I do. In windows I use my usb port for my dsl modem. 

Thank you for your help. I'm sold on linux now. I just need to get an Ethernet card and reinstall Ubuntu.

---

