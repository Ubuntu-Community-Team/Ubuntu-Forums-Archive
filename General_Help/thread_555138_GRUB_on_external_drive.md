---
title: "GRUB on external drive"
date: 2007-09-19
forum: General Help
---

### Post by shingalated on 2007-09-19
My room mate installed linux on his laptop (a 20 GB partition on his 500 GB external drive).  He did it as a dual boot with his windows install (on the internal drive.) The problem is when he doesn't have his external drive plugged in, he can't boot.  What did we do wrong?

---

### Post by logos34 on 2007-09-19
Grub installs by default to the internal drive MBR.  You need to reinstall it to the external and restore windows bootloader using either the XP install cd (recovery console>**fixmbr**) or **Super Grub** disc.  Then use the bios to choose boot disk

---

### Post by shingalated on 2007-09-20
How can I change where grub is installed.  It did not ask me during the install.

---

### Post by logos34 on 2007-09-20
> **shingalated said:**
> How can I change where grub is installed.  It did not ask me during the install.

open a terminal in ubuntu and type:

[B]sudo grub 
find /boot/grub/stage1[/B]
(enter output 'hd1,x'  in next command, where x=root partition #)
[B]root (hd1,x)
setup (hd1) 
quit[/B]

You'll have to edit /boot/grub/menu.lst too, changing all instances of (hd1,x) to '(hd0,x)' because it will alter when you switch the bios to boot directly to the usb.  See post #502 in [this thread]("http://ubuntuforums.org/showthread.php?t=80811&highlight=dabrugo&page=51").

---

### Post by Taurich on 2008-01-22
Hi all!
First post ever, super new to linux in all forms, I installed it two and a haf days ago. I have the same problem which kind of cripples me if my laptop dies or reboots while I'm away from the drive

Ok, so I wanted to check with you guys before I started screwing with this. I don't have my vista disks with me. I left them at home apparently because I stopped using my brain. anyway, will super grub fix Vista bootloaders? also, this is from my grub/menu.list


## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5913736c-c283-4eac-a779-e464320b8983 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5913736c-c283-4eac-a779-e464320b8983 ro single
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
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1



I assume it meens that i would do this:

sudo grub
find /boot/grub/stage1

root **(hd1,1)**
setup (hd1)
quit

then edit the menu.list and replace (hd0,1)

do I need to remove the part about the vista loaders if I'm putting grub on the external drive and then just set the BIOS to boot from USB HDD? or do I have this entirely wrong and have no idea what I'm talking about? 

Thanks for helping!

---

### Post by logos34 on 2008-01-22
> **Taurich said:**
> ...I assume it meens that i would do this:

sudo grub
find /boot/grub/stage1

root **(hd1,1)**
setup (hd1)
quit

then edit the menu.list and replace (hd0,1)

do I need to remove the part about the vista loaders if I'm putting grub on the external drive and then just set the BIOS to boot from USB HDD? or do I have this entirely wrong and have no idea what I'm talking about? 



Yeah, you have it right. i.e. (hd0,1) is what you want.  (Because as soon as you change the usb to first boot disk, it becomes (hd0))

Remember to remove the 'map' lines for XP Home on the first partition/sdb1 and change root to (hd**0**,0) if you want to be able to boot it from grub. 

You don't need to remove the vista stanzas, but you can if you want.  Or just comment them out (#)

---

### Post by Taurich on 2008-01-22
> **logos34 said:**
> Yeah, you have it right. i.e. (hd0,1) is what you want.  (Because as soon as you change the usb to first boot disk, it becomes (hd0))

Remember to remove the 'map' lines for XP Home on the first partition/sdb1 and change root to (hd**0**,0) if you want to be able to boot it from grub. 

 (#)

so just comment the map lines out so that it doesn't map the home installation as (hd0,0) then? 

as per the Super Grub Disk, it can repair the vista boot loaders no problem? I haven't done much of this stuff and have a (likely unjustified) paranoia about boot loaders and the like.

---

### Post by logos34 on 2008-01-23
> **Taurich said:**
> so just comment the map lines out so that it doesn't map the home installation as (hd0,0) then?

yes, comment them out or just delete.

> as per the Super Grub Disk, it can repair the vista boot loaders no problem? I haven't done much of this stuff and have a (likely unjustified) paranoia about boot loaders and the like.

sorry, forgot that part.

Some claim it can, but to be honest I can't confirm this.  (I don't have vista either, only x64 XP pro, so I have no way of finding out).  Try it and let me know.  

If not, you can [download the Windows Vista recovery disc]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") (~120 MB) over at neosmart.com, which supposedly will allow you to boot into the repair environment just as you would on a regular vista disc to fix the mbr.

---

### Post by Taurich on 2008-01-24
> **logos34 said:**
> 

Some claim it can, but to be honest I can't confirm this.  (I don't have vista either, only x64 XP pro, so I have no way of finding out).  Try it and let me know.  



I'm quite happy that things went as planned. I had both Super Grub Disk and the Vista recovery Disk on hand. I did exactly as you said and all went well. 

Grub is now on the external drive and boots just fine. On the first attempt at booting Vista there was a grub error that I was expecting. so I popped in super grub and removed Grub entirely. rebooted to super grub and set (hd0,0) as the active partition. popped the disk out and rebooted a final time with success. I can now boot vista independently of the external HDD.

Thank you so much for all the help, it is greatly appreciated.

---

### Post by logos34 on 2008-01-24
Glad to hear.

Mark as 'solved'. (>thread tools)

have fun

---

