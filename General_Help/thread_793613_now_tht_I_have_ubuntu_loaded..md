---
title: "now tht I have ubuntu loaded."
date: 2008-05-13
forum: General Help
---

### Post by Mr Pockets151 on 2008-05-13
I got ubuntu 7.1 loaded onto one of my hardrives.  Now I read one of the other threads on installing dual boot to seperate hdd.  My windows is on my sata and ubuntu is on my ide.  Now I need to figure out how to edit the GRUB to set my IDE as master and be able to choose which OS to load.  Right now I have to change BIOS boot sequence. 

I was able to mount my two other hard drives to ubuntu.  Everythhing shows up.  My question is how do I know what parameter to enter into the menu.lst.  Ubuntu see's my SATA drives as SCSI.  I need to remap the menu.lst "i know this" but when I tried it didn't allow me to save anything.  I got a message saying I had no permission.  

What command can I use to see all my available hdd and what numbers they are assigned???

---

### Post by pastalavista on 2008-05-14
```
sudo gedit /boot/grub/menu.lst
```

or to do it the GUI way install QGRUBEditor from the Add/Remove application or the Symantic Package Manager 

or from the terminal ```
sudo apt-get install qgrubeditor
```

---

### Post by pastalavista on 2008-05-14
Oh, and to see your drives:
```
sudo gparted
```

---

### Post by Mr Pockets151 on 2008-05-14
this is the drive i have my windows xp on.  This is from fdisk

Disk /dev/sda: 164.6 GB, 164696555520 bytes
16 heads, 63 sectors/track, 319120 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xaf64b773

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      319118   160835440+   7  HPFS/NTFS


I edited my grub to look like this....

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0db867b9-69ee-45ff-b8a4-0252e6c19902 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0db867b9-69ee-45ff-b8a4-0252e6c19902 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title           Windows XP (loader)
root            (sd1,0)
map             (sd1,0)
map             (sd1)(hd0)
savedefault
chainloder +1

The menu item is there but when I select it...i get "PRESS ANY KEY TO CONTINUE" message and it sends me back to grub menu choice.  I choose xp and it keeps saying press any key to continue.  What am I doing wrong?  I have also tried hd1 instead of sd1.

---

### Post by pastalavista on 2008-05-15
In my menu.lst file it says:

title Windows Vista/Longhorn (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive

so maybe you need to add the line "makeactive"

I'm pretty much of a noob at this too. 

I was wondering, in gparted, does it list the XP drive with a "boot" flag?

---

### Post by Mr Pockets151 on 2008-05-15
I tried makeactive.  But I will try again.  Does it matter which order it's in.  And does it matter if I have the correct spacing?

I don't have Gparted.  I guess I should install it.

---

