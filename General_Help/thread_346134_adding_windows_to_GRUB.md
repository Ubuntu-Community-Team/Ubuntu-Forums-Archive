---
title: "adding windows to GRUB"
date: 2007-01-25
forum: General Help
---

### Post by amoore on 2007-01-25
I need help adding windows to GRUB. My drives in the computer are in this order.

Primary Master---> Ubuntu 60GB
Primary Slave----> Storeage for Ubuntu EXT3 200GB

Secondary Master----> Wiindows XP 40GB
Secondary Slave----> DVD ROM

How should my Grub look for the Windows Xp section?:confused: 

I hate windows:x But I need to install it for school (Im taking a .NET class)

---

### Post by agustin.g on 2007-01-26
i've heard Windblows erases the MBR, but i don't know if it's the one on the harddisk it's being installed to or the primary hard disk. I belive it's the primary one though. My suggestion is to backup your ubuntu stuff on the 200Gb drive, install windows in its respective partition/hard disk drive and then install ubuntu again. Grub should detect Windows XP and add an entry in the boot menu.

---

### Post by wraithe on 2007-01-26
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
chainloader	+1



Just like that, but if you are install win-xp after linux, then u will have to boot with an install disk and type rescue, then reinstall bootloader, then you may have to add that to the file /boot/grub/menu.lst ...after that, its all plain sailing...oh and save your file when you exit from it...if using vi, or vim  use the command  :x or you may not save nil....

---

