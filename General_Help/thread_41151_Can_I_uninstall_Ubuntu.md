---
title: "Can I uninstall Ubuntu?"
date: 2005-06-12
forum: General Help
---

### Post by gabrielpalomares on 2005-06-12
Hi,

I've been using Ubuntu for quite some time (1 month) but I am getting a bit sick of WINE. So now I want to uninstall Ubuntu so I can partition my system and dual-boot with XP & Ubuntu. (not saying Ubuntus bad, actually, it's great!) There is no uninstall feature with ubuntu, nor formatting the system helps. I've tried reformatting it, but when it boots it comes out as an error with GRUB. Any ideas?

(yes... i am a noob... ](*,) )

---

### Post by gabrielpalomares on 2005-06-12
Just more info:

I have bought a partitioner for Win.... i don't want to spend more money....
I have tried installing Linspire 5.0, does not work!
I use a IBM Netvista with a Intel Pentium 3 Processor with 300MBs of memory and 20gb of space.
Last resort: if i don't get Ubuntu to uninstall, then I will buy a new hdd.

---

### Post by X3N on 2005-06-12
simple answer is that, you don't uninstall operating systems.
you format the disk so that they are "erased" . If you want to dual boot with windows, install windows on a partition on your hard disk leaving some free space for ubuntu. Windows then writes it's MBR - master boot record, this will overwrite grub "loader-thingy" . Then install ubuntu, making sure you use the free space on your hard disk which has not been partitioned yet. When ubuntu installs it will install the boot loader, which sees the fact there is a windows partition and adds it to the loader's menu.

---

### Post by defkewl on 2005-06-12
Why don't you just format your harddrive?

---

### Post by gabrielpalomares on 2005-06-12
[QUOTE=X3N]simple answer is that, you don't uninstall operating systems.
you format the disk so that they are "erased" . If you want to dual boot with windows, install windows on a partition on your hard disk leaving some free space for ubuntu. Windows then writes it's MBR - master boot record, this will overwrite grub "loader-thingy" . Then install ubuntu, making sure you use the free space on your hard disk which has not been partitioned yet. When ubuntu installs it will install the boot loader, which sees the fact there is a windows partition and adds it to the loader's menu.[/QUOTE]

Tried to install Windows ME.... for some reason.... you know, when you're like asked to reset your computer to complete the installation blah blah blah.... it still loads up grub (the loader-thingy)  :mad: 

Oh well.... just have to stick with Ubuntu (cries)

---

### Post by gabrielpalomares on 2005-06-12
[QUOTE=defkewl]Why don't you just format your harddrive?[/QUOTE]

thats what i did....

---

### Post by kiddyfurby on 2005-06-12
have u tried erasing the mbr?
in dos: fdisk /mbr
in NT recovery console: fixmbr

---

### Post by trivialpackets on 2005-06-12
It sounds like the boot order on the bios is set to hard drive before disk for whatever reason.  If it's booting into grub, this would likely be the case.  alternatively, you may need a Window ME boot diskette.  I would suggest trying the former first.  Hitting F10 or F3 or something as the system restarts should bring up your BIOS menu.  If you can change it to boot first from CD before hard drive, then it sounds like you would be able to boot form ME disk.  If not then possibly the floppy boot disk would work.  If you want to try the latter let me know, it's just a boot disk and I'm sure I could find one for you and send the contents.  Good luck.  Also, if you don't have the boot disk, then any boot disk would work, but again, this would be dependent on the boot order.  

On a side note, a secure system is not set to boot to CD rom first, but is password protected on the bios and is set to boot hard drive first, so if these settings are important, make sure you change them back.  Good luck.

---

### Post by gabrielpalomares on 2005-06-12
[QUOTE=eric.proctor]It sounds like the boot order on the bios is set to hard drive before disk for whatever reason.  If it's booting into grub, this would likely be the case.  alternatively, you may need a Window ME boot diskette.  I would suggest trying the former first.  Hitting F10 or F3 or something as the system restarts should bring up your BIOS menu.  If you can change it to boot first from CD before hard drive, then it sounds like you would be able to boot form ME disk.  If not then possibly the floppy boot disk would work.  If you want to try the latter let me know, it's just a boot disk and I'm sure I could find one for you and send the contents.  Good luck.  Also, if you don't have the boot disk, then any boot disk would work, but again, this would be dependent on the boot order.  

On a side note, a secure system is not set to boot to CD rom first, but is password protected on the bios and is set to boot hard drive first, so if these settings are important, make sure you change them back.  Good luck.[/QUOTE]

thank you so much! this solved my prob and now im booting between xp and ubuntu  \\:D/

---

### Post by trivialpackets on 2005-06-12
Good to hear and glad I can help someone else, I get enough help around here.  Enjoy.

---

