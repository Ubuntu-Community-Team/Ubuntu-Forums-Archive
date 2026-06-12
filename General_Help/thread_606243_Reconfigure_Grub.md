---
title: "Reconfigure Grub"
date: 2007-11-07
forum: General Help
---

### Post by dismal_denizen on 2007-11-07
When I installed Ubuntu it was great at picking up my other OS (Windows XP). I have since installed Fedora 7, and I want this to be available in the boot menu. Is there a way to get Grub to reconfigure just as when it was first installed?

Disk Layout:

1st HD

Partition 1: XP
Partition 2: File Storage
Partition 3: Fedora

2nd HD

Partition 1: Ubuntu

---

### Post by mpierce on 2007-11-07
You haven't given any disk geometry for anyone to help you. You can reinstall grub by doing:
   mount /dev/sda2 /mnt grub-install --root-directory=/mnt '(hd0)' 
      see my example below for my old laptop

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
timeout		120

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

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

Hope this helps...

---

### Post by dismal_denizen on 2007-11-08
I get rather confused when it comes to the labels given to drives in Linux (I'm still pretty new). My main hard drive is SATA and contains XP on the first partition, files on the second, and Fedora on the third.
The other hard drive is IDE and only contains Ubuntu. I have no other hard drives.

---

### Post by kellemes on 2007-11-08
Edit /boot/grub/menu.lst with root-privileges.
And add the following line at the bottom.. and see what happens at boot.

```
title Windows
root (hd0,0)
savedefault
makeactive
chainloader +1
```

---

### Post by louieb on 2007-11-08
Quick question. When you boot which GRUB shows up Fedora or Ubuntu?

---

### Post by dismal_denizen on 2007-11-08
I think that you misunderstand. I can get Windows and Ubuntu in the bootloader, but not Fedora. I might not have been totally clear about this, sorry.

---

### Post by fjgaude on 2007-11-08
The grub bootloader, menu now shows windows and ubuntu. You wish to ask fedora to the menu?

Okay, edit /edt/boot/grub/menu.lst near the bottom to show the lines needed to point to fedora. You can get much of it from the grub.menu that comes up when you boot fedora.

I forget all the things that are different in fedora as I've been with ubuntu for so long.

Show us your fedora grub menu and then I think one of us will have an answer for you.

---

### Post by louieb on 2007-11-08
Ok you can do this.  What your going to do is put an entry in that will load the Fedora GRUB menu.
```

title  Fedoras GRUB menu    
configfile ([COLOR=Red]hd0,2[/COLOR])/boot/grub/menu.lst      
```The part in [COLOR=Red]red [COLOR=Black] is  just a guess based on what put in you first post
Put this code a the bottom of Ubuntus /boot/grub/menu.lst. 

If it doesn't work please open a terminal window and post the output of 
[/COLOR][/COLOR]```
sudo fdisk -l
```[COLOR=Red][COLOR=Black] (lowercase L)
 [/COLOR][/COLOR]

---

### Post by dismal_denizen on 2007-11-08
I told Fedora not to install Grub - does this stuff things up?

---

### Post by louieb on 2007-11-08
Yea it kinda puts a spin on it. When you boot multiple Linux distros you really want each to have its own grub. When you install  the second distro you tell it to install GRUB on the boot sector of its partition.   Then either use the configfile  statement or chainload  it.  

What I would probably do at this point is get the   [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") and use it to add grub to Fedora. Heres some good pointers on using it. as well as good stuff on multi booting in general.  [IDBS on SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

Or you could always reinstall Fedora just remember to put GRUB in its partitions boot sector (**not the hard drives MBR**).

---

### Post by dismal_denizen on 2007-11-11
Thanks for all your help, but I have found that Fedora is no where near as good as Ubuntu, so I'm sticking with it. Now of got the headache of Gutsy Gibbon's internet not working...

I think I'll stick with Feisty Fawn!

---

