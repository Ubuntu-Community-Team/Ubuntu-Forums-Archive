---
title: "Vista/Ubuntu/XP Triple Boot Issues"
date: 2008-05-23
forum: General Help
---

### Post by SlalomMan on 2008-05-23
I bought a Toshiba laptop with Vista pre-installed...I soon switched to ubuntu in a dual boot setup. It was simply enough to set up; the installer detected my vista partition and set up GRUB accordingly. However, I want to install XP as well because Vista is slowing down and I don't feel like reinstalling, and I like XP better. So I installed XP to another partition, and then I reinstalled GRUB. Ubuntu boots fine, and I have the menu.lst set to boot to XP right, but when I select XP, it tells me that "NTLDR is missing." I assume this has something to do with the fact that GRUB is the bootloader instead of the windows one, but I'm not sure what to do. Any advice?

---

### Post by housam on 2008-05-23
You have to edit the menu.lst file and in win-xp section point the to partition that has grub.
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by SlalomMan on 2008-05-23
I'm quite new to the inner workings of linux...how exactly would I go about that?

---

### Post by housam on 2008-05-23
OK , Just open a terminal ( applications >> accessories >> terminal ) and copy past the command I gave you . then post the results.

---

### Post by SlalomMan on 2008-05-23
Alright. I know menu.lst, and I put XP in there, but there is probably an option that I am missing to get it to work.

My guess is that it has to have different settings than Vista?

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
# kopt=root=UUID=fbdb4ba0-54db-4e61-9230-5c85c1bf1e5f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fbdb4ba0-54db-4e61-9230-5c85c1bf1e5f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fbdb4ba0-54db-4e61-9230-5c85c1bf1e5f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		Windows XP
root		(hd0,3)
savedefault	
makeactive	
chainloader	+1

```

---

### Post by meierfra. on 2008-05-23
What happens when you choose Vista at the grub menu?

---

### Post by housam on 2008-05-23
change the following section 
```
title		Windows XP
root		[COLOR="Red"](hd0,3)[/COLOR]
savedefault	
makeactive	
chainloader	+1
```

to 
```
title		Windows XP
root		[COLOR="Red"](hd0,0)[/COLOR]
savedefault	
makeactive	
chainloader	+1
```

because Windows does not install it's boot loader to the partition it is installed on, but normally to the first partition of the first hard disk

---

### Post by ExSuSEusr on 2008-05-23
Buy and install VMware. 

Not trying to be a smart*** but to heck with multi-booting.

---

### Post by lswest on 2008-05-23
you made the common mistake of assuming that GRUB replaces all the bootloaders, it doesn't.  it forwards the requests to the respective bootloaders, in this case, to the ntldr in XP, which (sadly) cannot boot Vista.  The correct way to dual boot would have been (and still is) to restore the Vista bootloader, make sure it can boot XP, and then install GRUB over top, so that from the GRUB menu you can access a bootloader that boots both Vista and XP.

```
Grub --> Ubuntu
     -->NTLDR-->XP
             -->Vista
```

the third line of my sig (link to a how-to i wrote) should help you set up your system to boot into Vista (after you get it booting to XP)**

about the ntldr error (if the above solutions did not resolve it) have a look at these:
[http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)
[http://support.microsoft.com/kb/320397](http://support.microsoft.com/kb/320397)

** XP must be working before replacing that bootloader with Vista's, as it again uses the ntldr and boot.ini files from the respective XP partition**

---

### Post by SlalomMan on 2008-05-23
It boots to XP....
Maybe the problem is that XP installed the bootloader to the Vista partition; now should i have to configure that bootloader to allow vista? I'm so confused right now.

---

### Post by meierfra. on 2008-05-23
> It boots to XP....

That's what I thought.


> Maybe the problem is that XP installed the bootloader to the Vista partition; 

Yes. I recommend EasyBCD  to restore you Vista Boot Loader and add XP to the Vista Boot menu.  Just follow the instruction in this link

[http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista]("http://neosmart.net/wiki/display/EBCD/Installing+XP+After+Vista")

---

### Post by housam on 2008-05-23
Did the changes you've made to the menu.lst made win-xp bootable ? If so,make the same change to vista.

---

### Post by SlalomMan on 2008-05-23
Alright. So what I'm going to do is:
1)Boot to XP and Launch EasyBSD
2)Restore Vista Bootloader and add XP to the list
3)Reinstall Grub, which will hopefully be able to point to the Vista Bootloader and from there XP and Vista.

Sound like a plan?

---

### Post by meierfra. on 2008-05-23
Sounds good to me.

---

