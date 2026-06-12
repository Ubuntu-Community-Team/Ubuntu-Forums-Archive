---
title: "multiple ubuntu listings in GRUB?"
date: 2008-05-03
forum: General Help
---

### Post by eheyl on 2008-05-03
I am noticing something odd. Ever since I upped to Hardy, when I start my cpu there is always more than one listing in GRUB for it, seems to get more after I do an update. And I'm not talking about the regular, test and safe options but just listings of the same entry (regular) I was wondering if anyone else is experiencing this and if so, how can I fix it? Its not hurting anything but is weird??

Thanks
Erik

---

### Post by ghost_ryder35 on 2008-05-03
> **eheyl said:**
> I am noticing something odd. Ever since I upped to Hardy, when I start my cpu there is always more than one listing in GRUB for it, seems to get more after I do an update. And I'm not talking about the regular, test and safe options but just listings of the same entry (regular) I was wondering if anyone else is experiencing this and if so, how can I fix it? Its not hurting anything but is weird??
 
Thanks
Erik
when you update to a new kernel, there is a new entry in grub for that kernel. in case that kernel does not boot they leave the old entry there so the system is still usable.  
If you would like to edit the kernels available to boot into edit
```

sudo cp /boot/grub/menu.lst /home/yourusername/menu_backup.lst   #### makes a backup incase you delete something you shouldnt have
sudo gedit /boot/grub/menu.lst  #### the file you want to edit to change the bootable kernels

```

---

### Post by TeoBigusGeekus on 2008-05-03
They are the older kernels...
```
gksu gedit /boot/grub/menu.lst
```
and comment out (don't delete them) the older entries.

---

### Post by eheyl on 2008-05-04
Ok I did so and it worked but now when I select windows xp personal it says file not found? I still have a few things that need windows, what did I do? Help!!

---

### Post by TeoBigusGeekus on 2008-05-04
Post us the content of your menu.lst file.

---

### Post by ghost_ryder35 on 2008-05-04
> **eheyl said:**
> Ok I did so and it worked but now when I select windows xp personal it says file not found? I still have a few things that need windows, what did I do? Help!!
remember the backup we made 
> **ghost_ryder35 said:**
> when you update to a new kernel, there is a new entry in grub for that kernel. in case that kernel does not boot they leave the old entry there so the system is still usable. 
If you would like to edit the kernels available to boot into edit
```

sudo cp /boot/grub/menu.lst /home/yourusername/menu_backup.lst   #### makes a backup incase you delete something you shouldnt have
sudo gedit /boot/grub/menu.lst  #### the file you want to edit to change the bootable kernels

```
(hopefully you did make it)
lets restore the original so you can get into windows
```

sudo cp /home/yourusername/menu_backup.lst /boot/grub/menu.lst 

```

---

### Post by eheyl on 2008-05-04
ack I missed the backup.

Here are the contents of the file:
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
# kopt=root=UUID=3dec53f7-3678-45e6-8e40-5d20cd90de51 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=3dec53f7-3678-45e6-8e40-5d20cd90de51 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=3dec53f7-3678-45e6-8e40-5d20cd90de51 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

## title		Ubuntu 8.04, kernel 2.6.24-16-generic
## root		(hd0,5)
## kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3dec53f7-3678-45e6-8e40-5d20cd90de51 ro quiet splash
## initrd		/boot/initrd.img-2.6.24-16-generic
quiet

## title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
## root		(hd0,5)
## kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3dec53f7-3678-45e6-8e40-5d20cd90de51 ro single
## initrd		/boot/initrd.img-2.6.24-16-generic

## title		Ubuntu 8.04, kernel 2.6.22-14-generic
## root		(hd0,5)
## kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3dec53f7-3678-45e6-8e40-5d20cd90de51 ro quiet splash
## initrd		/boot/initrd.img-2.6.22-14-generic quiet

## title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
## root		(hd0,5)
## kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3dec53f7-3678-45e6-8e40-5d20cd90de51 ro single
## initrd		/boot/initrd.img-2.6.22-14-generic

## title		Ubuntu 8.04, memtest86+
## root		(hd0,5)
## kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
 title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows Whistler Personal
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
## title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e75dff9c-eb05-42ea-b0d9-bdafd14c1190 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
## title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e75dff9c-eb05-42ea-b0d9-bdafd14c1190 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
## title		Ubuntu 7.10, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot



FYI for some reason, my applications menu is now empty??? I checked other users and they are fine. ....Getting frustrated. I did post a new thread. Could use the help.

---

### Post by ghost_ryder35 on 2008-05-04
you did not make the backup?  no good.....

---

### Post by TeoBigusGeekus on 2008-05-04
Was your only intervention the commenting of the extra kernels?

---

### Post by ghost_ryder35 on 2008-05-04
> 
## title Ubuntu 8.04, kernel 2.6.24-16-generic
## root (hd0,5)
## kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=3dec53f7-3678-45e6-8e40-5d20cd90de51 ro quiet splash
## initrd /boot/initrd.img-2.6.24-16-generic
[B][COLOR=red]quiet
[/COLOR][/B]
## title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
## root (hd0,5)
## kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=3dec53f7-3678-45e6-8e40-5d20cd90de51 ro single
## initrd /boot/initrd.img-2.6.24-16-generic

## title Ubuntu 8.04, kernel 2.6.22-14-generic
## root (hd0,5)
## kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=3dec53f7-3678-45e6-8e40-5d20cd90de51 ro quiet splash
## initrd /boot/initrd.img-2.6.22-14-generic quiet

## title Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
## root (hd0,5)
## kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=3dec53f7-3678-45e6-8e40-5d20cd90de51 ro single
## initrd /boot/initrd.img-2.6.22-14-generic

## title Ubuntu 8.04, memtest86+
## root (hd0,5)
## kernel /boot/memtest86+.bin
**[COLOR=red]quiet[/COLOR]**

those should be commented out also

---

### Post by eheyl on 2008-05-04
Yes the only thing i did was comment out., what is quiet?

---

### Post by TeoBigusGeekus on 2008-05-04
It supresses text messages during boot up. Comment them out as well...

---

### Post by lswest on 2008-05-04
can you post the output of ```
sudo fdisk -l
``` as well?

---

### Post by eheyl on 2008-05-04
Your wish is my my command line :)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x55054103

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         596     4505728+  12  Compaq diagnostics
/dev/sda2   *         597        6540    44936640    7  HPFS/NTFS
/dev/sda3            6541        9037    18877320   83  Linux
/dev/sda4            9038       10337     9828000    5  Extended
/dev/sda5           10175       10337     1232248+  82  Linux swap / Solaris
/dev/sda6   *        9038       10119     8179857   83  Linux
/dev/sda7           10120       10174      415768+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by TeoBigusGeekus on 2008-05-04
```
title Windows NT/2000/XP
root (hd0,0)
savedefault
makeactive
chainloader +1
```

Try to change this entry to 

```
title Windows NT/2000/XP
root (hd0,1)
savedefault
makeactive
chainloader +1
```

---

### Post by Senesence on 2008-05-04
Is there a specific reason as to why the GRUB listings need to be modified directly?

I mean can't you just go into synaptic and uninstall the kernels you don't want to keep?

---

### Post by ghost_ryder35 on 2008-05-04
> **Senesence said:**
> Is there a specific reason as to why the GRUB listings need to be modified directly?
 
I mean can't you just go into synaptic and uninstall the kernels you don't want to keep?
yep you can :)  but sometimes you want to keep the kernels incase you screw up the kernel your working on.  This way you still have a bootable system

---

### Post by jocko on 2008-05-04
> **Senesence said:**
> Is there a specific reason as to why the GRUB listings need to be modified directly?

I mean can't you just go into synaptic and uninstall the kernels you don't want to keep?

Exactly. If you just edit the boot menu all kernels will still be there, and will reappear in the boot menu when the kernel is updated. If the new kernel works, there is no point in keeping the old ones, especially if you remove the entries in the boot menu.

---

### Post by eheyl on 2008-05-04
Ok but isn't that the same as the whistler personal entry? that xp/2000 entry refers to the recovery option. whistler personal is the actual os. Thanks! I learn something new every day.

---

