---
title: "problems installing XP on Linux pc"
date: 2022-08-05
forum: General Help
---

### Post by david87150 on 2022-08-05
Hello
I have been very happy with my Linux 64bit PCs and now the but! one PC which I converted to Linux will not except a XP fresh installation.
So I thought I would change the hard drive thinking the problem was with the partions of the old installation of linux, I swapped the hard drive with from one from a Hitachi backup HD stand alone unit, then tried again but same problem copies xp installation files gets to point of installing and produces blue screen with error codes say check disk etc the discs are good. 
A question is does Linux change anything in the mother boards operation? does anyone have an idea please

---

### Post by TheFu on 2022-08-05
Lots of newer hardware isn't supported by WinXP.  XP is a dead OS.  I keep a virtual machine around with it to play old games, but would never install it directly onto hardware or give it access to any network.

---

### Post by crip720 on 2022-08-05
How old is your Linux PC?  Unless it is as old as XP, there is a good chance(100%) that XP will not have the hardware drivers for it, XP cannot work the computer.  I have a Ubuntu 4.10 disk.  Can only install and have it work(kind of) one  very old laptop(a P4), it will not run on laptops that are newer than the P4.

---

### Post by yancek on 2022-08-05
Suppor for XP ended in 2009 and even the Extended support ended 8 years ago so if your hardware is newer than that, it is very unlikely to work.t 

>  I swapped the hard drive with from one from a Hitachi backup HD stand alone unit

Not sure what you mean here but if that is an external drive, it will never work with any windows.

---

### Post by david87150 on 2022-08-06
Thanks for the response, I was not clear enough it is also an old machine an Dell Optiflex 755 that originally came with Vista those were the days :)
The hard drive is now a bare 2T hard drive no with links in place taken from the hitachi xl2000 from the same era

---

### Post by yancek on 2022-08-06
It isn't clear to me how old the hardware you have is.  If it is newer than the dates I posted in post 4, it won't likely work.  There would be nothing that Linux would do to prevent your installing another OS on the machine.
It also isn't clear to me if you are tryiig to install to an external hard drive connected by a usb port.  That won't work for windows.

---

### Post by TheFu on 2022-08-06
SATA and GPT aren't supported by WinXP.  Neither are most GigE NICs  or any current generation wifi adapters.  See the issue?

OTOH, if you create a virtual machine, then create the proper virtual hardware - IDE drives, 10/100 NICs, and a smaller HDD that uses MBR/MSDOS partitioning, I bet it can be loaded, unless the WinXP license is tied to specific hardware and not a retail license.

---

### Post by aug7744 on 2022-08-07
Perhaps the better and simple solution is install VirtualBox in your host system. VirtualBox GPU driver has good performance.
Install that OS and share files between host and guest OS.

---

### Post by david87150 on 2022-08-08
> **TheFu said:**
> SATA and GPT aren't supported by WinXP.  Neither are most GigE NICs  or any current generation wifi adapters.  See the issue?

OTOH, if you create a virtual machine, then create the proper virtual hardware - IDE drives, 10/100 NICs, and a smaller HDD that uses MBR/MSDOS partitioning, I bet it can be loaded, unless the WinXP license is tied to specific hardware and not a retail license.

Yes thats the reason, disk is SATA so xp install could not do anything and crashed, change to ATA then problem resolved
Many thanks everyone for your help!

---

### Post by HermanAB on 2022-08-08
+10 for installing XP in a virtual machine.  XP  actually runs much faster in a Linux VM than natively (since the Linux device drivers are better).

---

### Post by TheFu on 2022-08-08
> **david87150 said:**
> Yes thats the reason, disk is SATA so xp install could not do anything and crashed, change to ATA then problem resolved
Many thanks everyone for your help!

There are some SATA/SCSI drivers and some GigE NIC drivers for XP, but those need to be added using an install floppy - "Load Additional Drivers" - on the installation blue screen. It has been over a decade since I've seen an XP install, but I think that's the added driver option.  For most people, it is a much better idea to use a VM and select older virtual-hardware.  If the OS doesn't boot later, remembering where the added drivers are that need to be installed BEFORE getting into XP "safe mode" isn't common. I always forgot - I was stupid and installed GigE NIC drivers which meant that before I could restore backups, I needed to remember to get those NIC drivers installed.

---

### Post by aug7744 on 2022-08-08
Which software you wait run in "xp" ? You need access external hardware ?
Have several softwares running very well using WINE.

---

