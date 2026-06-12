---
title: "Help making Grub recognize my XP partition?"
date: 2007-11-06
forum: General Help
---

### Post by nairanvac on 2007-11-06
I had Windows XP and Windows Vista installed prior to installing Ubuntu, and when I installed Ubuntu, the installer only put an option for Vista into the menu.lst.  I've tried adding it manually, but when I select the option for XP in the boot menu, I get an error saying "Invalid Device Requested."

For reference, here's my menu.lst, and the output of sudo fdisk -l.

                   

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
# kopt=root=UUID=66d2af28-cb2f-48ed-bb1c-7945b82d3afe ro

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

title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title           Windows XP
root            (hd0,4)
savedefault
makeactive
chainloader     +1


title		Ubuntu
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=66d2af28-cb2f-48ed-bb1c-7945b82d3afe ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet


And the fdisk output:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7944    63810148+   7  HPFS/NTFS
/dev/sda2            7945        8963     8185117+   f  W95 Ext'd (LBA)
/dev/sda3            8964        9694     5859375   83  Linux
/dev/sda4            9695        9729      281137+  82  Linux swap / Solaris
/dev/sda5            7945        8963     8185086    7  HPFS/NTFS

Any help is appreciated!

Edit:  The XP partition is /dev/sda2 and /dev/sda5.  I've tried both (hd0,1) and (hd0,4) when putting the entry into menu.lst.

---

### Post by dcstar on 2007-11-06
> **nairanvac said:**
> I had Windows XP and Windows Vista installed prior to installing Ubuntu, and when I installed Ubuntu, the installer only put an option for Vista into the menu.lst.  I've tried adding it manually, but when I select the option for XP in the boot menu, I get an error saying "Invalid Device Requested."

For reference, here's my menu.lst, and the output of sudo fdisk -l.
..........
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7944    63810148+   7  HPFS/NTFS
**/dev/sda2            7945        8963     8185117+   f  W95 Ext'd (LBA)**
/dev/sda3            8964        9694     5859375   83  Linux
/dev/sda4            9695        9729      281137+  82  Linux swap / Solaris
/dev/sda5            7945        8963     8185086    7  HPFS/NTFS

Any help is appreciated!

Edit:  The XP partition is /dev/sda2 and /dev/sda5.  I've tried both (hd0,1) and (hd0,4) when putting the entry into menu.lst.

AFAIK, given that /dev/sda2 should either be an "Extended" partition (ID type 5) or not exist at all, it's no wonder that there are problems, what changed it?

I would use **cfdisk** to change the type and then see what happens.

---

### Post by logos34 on 2007-11-06
> **dcstar said:**
> AFAIK, given that /dev/sda2 should either be an "Extended" partition (ID type 5) or not exist at all, it's no wonder that there are problems, what changed it?

I would use **cfdisk** to change the type and then see what happens.

fdisk looks normal to me--xp is on a logical partition.  

If you installed Vista after XP then you would have been booting to the latter through vista boot manager.  Can't you boot to  vista bootloader in grub, and from there select XP?

---

### Post by nairanvac on 2007-11-07
I actually installed XP after Vista.

Funny that you'd mention the Vista bootloader.  Do you think I could try adding an entry to Vista's boot.ini for my XP install, and then do like you said and boot into XP from there?

---

### Post by namanbagga on 2007-11-07
Look,You should mention the partition **containing** Windows XP and not the one **used** by windows XP.

---

### Post by nairanvac on 2007-11-07
> **namanbagga said:**
> Look,You should mention the partition **containing** Windows XP and not the one **used** by windows XP.

I'm not sure of it.  As far as I can tell, /dev/sda2 and /dev/sda5 are the same partition.

---

### Post by namanbagga on 2007-11-07
Install gparted,and tell me what the partition table shows
```

sudo apt-get install gparted
```

---

### Post by nairanvac on 2007-11-07
[http://img209.imageshack.us/img209/3999/gpartedscreenshotts8.png](http://img209.imageshack.us/img209/3999/gpartedscreenshotts8.png)

That's what it shows.

---

### Post by nairanvac on 2007-11-07
Bump.

---

### Post by logos34 on 2007-11-07
> **nairanvac said:**
> I actually installed XP after Vista.

Funny that you'd mention the Vista bootloader.  Do you think I could try adding an entry to Vista's boot.ini for my XP install, and then do like you said and boot into XP from there?

Usually it's the opposite--adding vista to system with xp already installed.  I'm still not clear on what you did or didn't do before adding grub/ubuntu.  But XP on a logical partition (by definition inside an extended)  shouldn't in and of itself be the problem.  (I've dual booted XP Pro on a primary partition and XP Home on a logical partition just fine).

[http://apcmag.com/5485/dualbooting_vista_and_xp](http://apcmag.com/5485/dualbooting_vista_and_xp)
(-->section below 'Download and install EasyBCD')

---

### Post by Computer Guru on 2007-11-09
Here're the revelent sections from the EasyBCD documentation:
[http://neosmart.net/wiki/display/EBCD/Windows+XP](http://neosmart.net/wiki/display/EBCD/Windows+XP)

---

