---
title: "A litle help for a proper ediy from grub menu.lst file"
date: 2008-01-01
forum: General Help
---

### Post by leftezi on 2008-01-01
In my Dual Boot system (Ubuntu 7.10 and XP) i want to make Windows load fist (by default) in the grub bootmanager but i don't know how to do this.
I have read in the forums that the only thing to do is to change the "**default x**" parameter  to zero but in my menu.lst there is not such "default x" entry.

My Menu.lst file (at the end from the whole text) is:

```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8f83d3b3-cd81-490a-a9d7-2efbf1e814da ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8f83d3b3-cd81-490a-a9d7-2efbf1e814da ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```


So i don't know what exactly should i change in this file.

---

### Post by taurus on 2008-01-01
Edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and change the default value from 0 to 4 (since your windows is the fifth entry).

```
default     4
```
Save it and reboot.  Now, windows will start after 3 or whatever seconds that you have specified in the timeout option.

---

### Post by geirha on 2008-01-01
Alternatively, let default be 0 and move the windows section above the line 
```
### BEGIN AUTOMAGIC KERNELS LIST
```

Then windows will also be the first option. It's important that any windows entries are either before the BEGIN AUTOMAGIC... comment or after then END AUTOMAGIC... comment

When you've edited /boot/grub/menu.lst run ```
sudo update-grub
``` and check that everything is ok.

---

### Post by leftezi on 2008-01-01
@Taurus. 
Thanks. But that' is my problem. Can you see a "default" parameter in my "menu.lst" file that i have posted above? I can not. Where is it?
Do you mean the "savedefault" line in Windows section?

@geirha. 
Thank you geirha. As you see  in my "menu.lst" file that i have posted above, there is no "### BEGIN AUTOMAGIC KERNELS LIST" line or entry. I assume you mean to copy the Windows section below the "## ## End Default Options ##" line and then input a new line "### BEGIN AUTOMAGIC KERNELS LIST" after this section. 
Like this :

```
## ## End Default Options ##

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

### BEGIN AUTOMAGIC KERNELS LIST

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8f83d3b3-cd81-490a-a9d7-2efbf1e814da ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8f83d3b3-cd81-490a-a9d7-2efbf1e814da ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
```


Is that correct? 

.

---

### Post by geirha on 2008-01-02
No, that's not correct. You're missing a lot of lines in your menu.lst if that's your entire file. Move away your menu.lst ```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
Then run ```
sudo update-grub
``` which will create a new menu.lst if it doesn't exist. The new menu.lst will only contain ubuntu entries, so copy/paste the windows entry from your backup. And you should now also have that ### BEGIN AUTOMAGIC ... comment I talked about.

EDIT: Also, make sure the ubuntu entries are identical to those in your backup, especially that root (hd?,?) is correct

---

### Post by il-luzhin on 2008-01-02
If I can get in on this 

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
**[color=red]default		0[/color]**

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
# kopt=root=UUID=bc8ee413-eb48-4441-b322-7dd3e317aa37 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=bc8ee413-eb48-4441-b322-7dd3e317aa37 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=bc8ee413-eb48-4441-b322-7dd3e317aa37 ro single
initrd		/boot/initrd.img-2.6.22-14-rt

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bc8ee413-eb48-4441-b322-7dd3e317aa37 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bc8ee413-eb48-4441-b322-7dd3e317aa37 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```
I need to change the highlighted area to 3 then run
```

sudo update-grub

```
In order to set the generic kernel as the default boot.  Is that correct?

---

### Post by geirha on 2008-01-03
@**il-luzhin**
That will work for the time being, well setting it to 2 anyway, since it starts counting at 0, but when a new kernel comes along in an update, all the kernels will be shifted. So you'll need to change the updatedefaultentry line to ```
# updatedefaultentry=true
``` as well (don't remove the #)

However you might find setting ```
default saved
``` more appropriate. That will set whatever option you booted last, as the default option next time you boot. You will need to change the savedefault line to true ```
# savedefault=true
```
The savedefault option will add a savedefault line to each kernel entry, so it should look like this after running sudo update-grub:```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bc8ee413-eb48-4441-b322-7dd3e317aa37 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
[color=blue]savedefault[/color]
quiet

```
Such a line may also be added to windows entries, so this might be a better option for **leftezi** as well

---

