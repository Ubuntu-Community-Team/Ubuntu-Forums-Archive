---
title: "Big problems."
date: 2008-04-28
forum: General Help
---

### Post by xdarkday on 2008-04-28
Background story: I just upgraded to the latest version of ubuntu. I havent used ubuntu in a while, but heard of the upgrade and booted, then upgraded. I dual boot ubuntu/windows xp

Let me start with the most important.

It doesnt show Windows xp on the dual boot loading screen. It has the option for "other operating systems" but I get an error when selecting that option. PLEASE!!!!! someone help me fix this. I mainly use my xp install. A lot of my work is on that! :( Very important I get help with that. 

Resolution on the login screen is way off. I cant see where to even log in and I just type my login/pass knowing those forms are already selected.

My mouse is all messed up. I tried two different mice that work on other machines. Its like it double clicking (on both left and right) and I have to hold down the mouse key to keep the menu open. I CANT OPEN ANY FILES/anything using an icon USING MY MOUSE. As I am not a linux expert, this is a huge problem.

Ubuntu will freeze.

When I try to shut down, everything locks up for about 5 minutes, then gives me the shut down options.

Thank you so much in advance.

---

### Post by bollix47 on 2008-04-28
Can you open a terminal (Applications > Accessories > Terminal) and copy/paste the output of the following two commands:

```
cat /boot/grub/menu.lst
sudo fdisk -l
```

That's a lower case L not the number one.

---

### Post by xdarkday on 2008-04-28
```

richard@richard-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=501edd34-0581-4517-829a-bddd8dd1f5e2 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=501edd34-0581-4517-829a-bddd8dd1f5e2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=501edd34-0581-4517-829a-bddd8dd1f5e2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-10-generic root=UUID=501edd34-0581-4517-829a-bddd8dd1f5e2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-10-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-10-generic root=UUID=501edd34-0581-4517-829a-bddd8dd1f5e2 ro single
initrd		/boot/initrd.img-2.6.24-10-generic

title		Ubuntu 8.04, kernel 2.6.24-8-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-8-generic root=UUID=501edd34-0581-4517-829a-bddd8dd1f5e2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-8-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-8-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-8-generic root=UUID=501edd34-0581-4517-829a-bddd8dd1f5e2 ro single
initrd		/boot/initrd.img-2.6.24-8-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=501edd34-0581-4517-829a-bddd8dd1f5e2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=501edd34-0581-4517-829a-bddd8dd1f5e2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=501edd34-0581-4517-829a-bddd8dd1f5e2 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=501edd34-0581-4517-829a-bddd8dd1f5e2 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by bollix47 on 2008-04-28
Your XP entry is there.  I suspect that it's not showing because of so many entries for ubuntu.  

Try pressing the down arrow past the Other Operating Systems entry to see if XP shows up.

You can get rid of the older .20 and .22 kernels using synaptic under Installed (local or obsolete).  This will shorten your menu.lst and allow grub to show all options.

---

### Post by njparton on 2008-04-28
Regarding your X server issues, tell us what sort of graphics hardware you have.

---

### Post by xdarkday on 2008-04-28
> **bollix47 said:**
> Your XP entry is there.  I suspect that it's not showing because of so many entries for ubuntu.  

Try pressing the down arrow past the Other Operating Systems entry to see if XP shows up.

You can get rid of the older .20 and .22 kernels using synaptic under Installed (local or obsolete).  This will shorten your menu.lst and allow grub to show all options.
I couldnt find them in the synaptic PM, but its probably because I am a newb.
> **njparton said:**
> Regarding your X server issues, tell us what sort of graphics hardware you have.
My graphics card is a nvidia gforce something.

---

### Post by njparton on 2008-04-29
I suggest you install envy (which can be done from the command line) which can be used to uninstall and reinstall the latest restricted nvidia drivers.
 
If you google 'envy ubuntu' you'll find the homepage for it.  Excellent tool.

---

### Post by xdarkday on 2008-04-29
> **njparton said:**
> I suggest you install envy (which can be done from the command line) which can be used to uninstall and reinstall the latest restricted nvidia drivers.
 
If you google 'envy ubuntu' you'll find the homepage for it.  Excellent tool.

Im really not sure if my video drivers are the problem with any of my issues. Ubuntu install the latest drivers for me. I just really want to load windows. Please. Its really important. 

PS thank you for your help thus far.:KS

---

### Post by tliotis on 2008-04-29
you can find your files from ubuntu if you search for them.Then make them a backup to cd/dvd or external HDD and after that insert the windows xp cd and try to fixmbr or make repair on winxp.

---

### Post by bollix47 on 2008-04-29
Re: Synaptic Package Manager


Open Synaptic.

Look to the left near the bottom and click on the "Status" button.

In the upper left you should see "Installed (local or obsolete)".  Click on that.

In the right window you should see a list.  

Right click on the ones that start with "linux-" and have the numbers 2.6.22 or 2.6.20 and select mark for removal.

After you have marked the appropriate items click on "Apply" in the upper toolbar.

Close Synaptic when it finishes.

Re-boot.

Does your Windows XP Professional now show as a choice when grub comes up?

---

### Post by xdarkday on 2008-04-29
> **bollix47 said:**
> Re: Synaptic Package Manager


Open Synaptic.

Look to the left near the bottom and click on the "Status" button.

In the upper left you should see "Installed (local or obsolete)".  Click on that.

In the right window you should see a list.  

Right click on the ones that start with "linux-" and have the numbers 2.6.22 or 2.6.20 and select mark for removal.

After you have marked the appropriate items click on "Apply" in the upper toolbar.

Close Synaptic when it finishes.

Re-boot.

Does your Windows XP Professional now show as a choice when grub comes up?
Thank you. This worked.

I got back on the forums just to thank everyone. I know what others suggestion before was basically the same, so thank you too.

Is there any way I can make a fresh install of ubuntu and not harm my XP partition and still able to dual boot?

---

