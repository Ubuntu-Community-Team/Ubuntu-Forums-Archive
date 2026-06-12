---
title: "Error loading operating system"
date: 2008-05-19
forum: General Help
---

### Post by BlueToast on 2008-05-19
When I try to boot off of my 40GB Maxtor (IDE) Harddrive, it gives me the following error message; that is all it gives. This harddrive has Ubuntu installed on it.

[img]http://www.hlrse.net/Qwerty/snapshot0000.gif[/img]

I also have a 500GB Seagate Barracuda (SATA-II) Harddrive with Windows XP on it. I also have VMWare setup so that I can work with Ubuntu while I use Windows. A simple step by step, question-answer help would be very much appreciated. :) I sort of need to use Ubuntu right now, and I don't want to reinstall it and lose my configurations, settings and programs. :(

My Ubuntu 7.1 CD is in one of my DVD drives, so I am prepared to boot of the CD if needed.

---

### Post by cubeist on 2008-05-19
Is this before or after you have selected your linux OS from the Grub menu?

---

### Post by BlueToast on 2008-05-19
Well there isn't anything to select. No signs or text of grub. Basically, I just turn on my computer, shows that BIOS loading screen or the CPU, harddrive, memory, and temperature information, then the next screen is simply "Error loading operating system."

Extremely vague.

---

### Post by roe_polak on 2008-05-19
Weee, I tried this once. Maybe there's something useful here:

[http://ubuntuforums.org/showthread.php?t=353495](http://ubuntuforums.org/showthread.php?t=353495)

If it's the same problem, then your partition table have been messed up. I noticed it by stating Gparted from the livecd.

---

### Post by koenn on 2008-05-19
It's not that vague. It's the BIOS looking for boot instructions on your hard drive and telling you it couldn't find any (or can't execute them).

Are you 100% sure youre booting of the right disk, i.e that your BIOS isn't looking to boot from that spare drive (that doesn't have a boot loader) ?
Does your BIOS detect / list all disks ? in the right order ? Is that 40GB drive selected as first boot device ? Did you remove any removable media (floppy, USB, CD, ...) that could be mistaken for a boot device ? ... ... 

If you're absolutely sure you're BIOS is trying to boot the right disk, this message probably means grub can't be executed, and reinstalling / fixing grub  is probably your next step.

---

### Post by BlueToast on 2008-05-19
> Are you 100% sure youre booting of the right disk, i.e that your BIOS isn't looking to boot from that spare drive (that doesn't have a boot loader) ?100% positive. My 500GB boots just fine, but the 40GB is the one that gives the error. Remember that the "500GB" is a "Windows HDD" (just consider it this way by the setup I have here) and the "40GB" is a "Linux/Ubuntu HDD." It's the 40GB or Linux/Ubuntu HDD that gives this error.

I use an ePox 8RDA3+ Pro, and one of the nice features about its BIOS is that I can select whether it first tries to boot off of Harddrives, Removable Storage devices, or CD/DVD-ROM Drives. Then I can set the order of boot priority for devices under each category. Also, when booting I can hit ESC (same area where I hit DEL or F1 to get into the BIOS menu) to get a boot menu that allows me to boot off of any specific device or harddrive that I want to. Very handy and nice feature.

> Does your BIOS detect / list all disks ?Yes.
> in the right order ?Yes.
> Is that 40GB drive selected as first boot device ?Yes. It was actually in this setup for several days now, because I did notice this error several days ago and always got it when I turned on my computer in the morning. It wasn't until today that I tried to boot Ubuntu off my 40GB that I found out that the error was originating from my 40GB and my motherboard had placed the 40GB as the 1st Harddrive in boot priority. I have no idea how this problem started.

> Did you remove any removable media (floppy, USB, CD, ...) that could be mistaken for a boot device ?No.
> If you're absolutely sure you're BIOS is trying to boot the right disk, this message probably means grub can't be executed, and reinstalling / fixing grub is probably your next step.Instructions would be useful then. A buddy of mine had me boot into the Ubuntu Live (CD), which I did so through VMWare on the 40GB Harddrive (I have VMWare setup to boot the 40GB), and he had me do **gksudo gedit /media/disk/boot/grub/menu.lst** (40GB Harddrive mounted) in terminal; had nothing about XP but just the regular Ubuntu, Recovery, and Memtest. He checked the configurations (I gave him the information of what was in there), and he found it to be perfectly normal and nothing wrong. He also had me check what files were in **/media/disk/boot/** and I had all the files that are needed; normal and perfectly fine. He thinks that Grub itself might be screwed up, otherwise he has no clue.

---

### Post by koenn on 2008-05-19
> **BlueToast said:**
> 
Instructions would be useful then. 
You wanted it step by step, right ? 

If you have an alternate install CD or a server CD : the installer has a rescue uption that allows you to reinstall and re-configure grub. 
You can also do this by running the installer in expert mode, carefully skip formatting the disks (just assign mountpounts), select "install GRUB" from the menu, and abort the installation afterwards. 

There's also a GRUB bootable CD (forgot the exact name) that can be used to fix grub.

---

### Post by imakerux on 2008-05-19
Go to [http://supergrubdisk.org/](http://supergrubdisk.org/) download a copy of their super disk.  Read, Read, Read their site. The disk will take care of boot trouble, but you must follow instructions and make the right choices.  I hope this helps.

---

### Post by BlueToast on 2008-05-27
Hey guys. With the help of almost everyone who replied to this thread and some people in IRC (GameSurge), I was able to reinstall Grub. I must also thank the users and author of the Ubuntu Forums thread at [http://ubuntuforums.org/showpost.php?p=1308395&postcount=1](http://ubuntuforums.org/showpost.php?p=1308395&postcount=1). :D

Grub loaded and finally goes through the loading process...

EDIT :: The aftermath of this thread can be found at [http://ubuntuforums.org/showthread.php?p=5055616](http://ubuntuforums.org/showthread.php?p=5055616).

---

