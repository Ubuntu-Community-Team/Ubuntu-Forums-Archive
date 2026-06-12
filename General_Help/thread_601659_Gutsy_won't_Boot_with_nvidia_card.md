---
title: "Gutsy won't Boot with nvidia card"
date: 2007-11-03
forum: General Help
---

### Post by Arun985 on 2007-11-03
Hi,

I just recently got Ubuntu Gutsy installed and have since been trying to get it to work with my nvidia card. When I try to run it with my nvidia card (GeForce 6200) Ubuntu completely stops at the boot up screen (the one with the loading bar.) Heres a list of everything I have tried thus far, all of which have ended up with the same, previously stated result:

-I tried installing the nvidia drivers with Envy
-I tried downloading and installing the nvidia drivers directly from the nvidia website. 
-I tried installing the nvidia packages from Synaptic Package Manager
-I tried reconfiguring X with: sudo dpkg-reconfigure xserver-xorg
-I enabled the nvidia driver in the restrcted driver manager.
-I tried using the nviidia-glx-new package, and then the nvidia-glx package.

As you can see, I've tried a bunch of different ways to get Ubuntu Gutsy to work with my nvidia card, all of which were unsucessfull. Is there anything else I should try?

:confused:

---

### Post by Pumalite on 2007-11-03
It could be a bad burn.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Burn at 4x, do md5sum, etc
Check your CD in a different computer.

---

### Post by Arun985 on 2007-11-03
I don't think the CD has anything to do with it, cuz I got Ubuntu installed, and it runs well off my onbooard graphics. But what I don't get is why it won't boot the nvidia card after i installed it and re-installed the drivers multiple times in multiple ways. 

:confused:

---

### Post by Pumalite on 2007-11-03
Make sure in BIOS that your on board video is off and your new card is recognized and well configured.

---

### Post by Arun985 on 2007-11-03
When I try to boot into Ubuntu with my nvidia card, i make sure that my BIOS is set to run off my nvidia card, not my onboard graphics, so that isn't the problem. Then i go to Ubuntu, and proceed to be shocked when Ubuntu does a hell of a lot of nothing. 

I could really use some help here. Ubuntu has an amazing community, and I'd hope that at least some of them could figure out a solution to my problem. 

:confused:  :(  ](*,)

---

### Post by Pumalite on 2007-11-03
Do you have Windows installed? Does your card run well in Windows?

---

### Post by Arun985 on 2007-11-03
Yes, I have WinXP Pro installed on another partition and my card runs perfectly well with it.

---

### Post by Arun985 on 2007-11-03
umm....this is gettin pretty frustating. Can someone PLEASE tell me that my problem is completely, and always will be, absolutely unsolvable? If someone can tell me this, then I can finally say good by to Linux, which is really nothing more than the worlds most unstable piece of crap.

---

### Post by RebounD11 on 2007-11-03
I can't tell U the solution to your problem (although U could try pressing alt+f1 while booting and see where it stops maybe it's not the video card), but i can encourage U to give Linux another shot with another distro. Gutsy didn't work for me either (didn't even install, so I can't say if it would've booted) but openSuSE 10.3 works flawlessly so far.

---

### Post by mivo on 2007-11-03
How did you install the drivers? I mean, did you get into Ubuntu with the recovery mode?

Try this:

sudo nano /boot/grub/menu.lst

Look for the regular Ubuntu entry there (if you see "ro" in there, it is the right one). In this line, add *nosplash* and if it is there, remove *quiet*. Save the file and reboot.

---

### Post by Arun985 on 2007-11-03
Thanks for your reply. And sorry I sounded so pissed of in my last post. Working with this stuff jus gets frustrating when you try and try and try and try again and nothing seems to work, even though you know it should. I was just venting.

Anyways, I tried what you said, mivo, and have successfully added your suggestion to my huge list of unsucessfull attempts to get this thing to work. Maybe its just not supposed work?

---

### Post by mivo on 2007-11-03
Hmm, I have a 8800GTS and had the same problem, but nosplash fixed it for me. :( Does your screen just go black after the Grub countdown?

Could you please post your /boot/grub/menu.lst file here?

Oh, and I know everything about frustration. It took me three days to get Gutsy working on my new desktop. In retrospect, it would only have taken five minutes if I had possessed all of the information and lessons I learned over the course of three incredibly annoying days! ;)

---

### Post by Arun985 on 2007-11-03
My problem is that Ubuntu stops working at the loading screen (the loading bar doesn't even go through all the way.) I appreciate the time you're taking to try and solve my problem.I guess working with Linux is just a learning experience.

Here's the content of my menu.lst:

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
# kopt=root=UUID=4a92ca68-6f17-4872-b63e-187cefed0491 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4a92ca68-6f17-4872-b63e-187cefed0491 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
nosplash

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4a92ca68-6f17-4872-b63e-187cefed0491 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
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
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by mivo on 2007-11-03
You need to change this part:

```

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=4a92ca68-6f17-4872-b63e-187cefed0491 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
nosplash

```

to look like this:

```

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
**kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=4a92ca68-6f17-4872-b63e-187cefed0491 ro nosplash**
initrd /boot/initrd.img-2.6.22-14-generic
quiet

```

The "quiet" in its own line belongs there, but you need to change the line I bolded. I had done that incorrectly the first time as well. :)

---

### Post by Arun985 on 2007-11-03
I did what you said, and now there is no loading screen, and it still gets stuck. It gets by "Loading Hardware Drivers" and then a bunch of processes run up the screen. It then stops at the following line:

[    29.148691] [<c010432e>] work_notifysig+0x13/0x25
[    29.148834] =========================

That is where it always gets stuck, so this isn't a new problem.

---

### Post by mivo on 2007-11-03
That is one step closer to the solution, though. I looked a little around, but found nothing very specific. Do you have any USB devices connected to your computer? If so, could you try booting without them being connected? (If you have an USB mouse or keyboard, try to connect them per PS/2 if possible.)

---

### Post by Arun985 on 2007-11-03
I removed the USB devices I had connected (just a printer and ext. HDD) and tried booting again with no sucess. It got stuck at the same place again.

---

