---
title: "Grub error 21 on ASUS P5B-E Plus"
date: 2007-01-18
forum: General Help
---

### Post by Aurdal on 2007-01-18
Hi, I just built a new computer with the ASUS P5B-E Plus motherboard, strange thing though is that after installing Ubuntu (and thereby GRUB) I get "Error 21" when ever I try to boot. I get this for both my IDE disk and my SATA disk, and it doesn't seem to matter which OS I try to boot (So far I've tried Windows XP and Ubuntu). I can however boot Windows XP with the Windows boot loader.

I've been searching for a solution to this for about 5 hours now, and I've yet to find anything that will solve my problem, so I turn to the community.

I hope someone will be able to help me with this. Thanks in advance.

-Kristoffer Aurdal

---

### Post by JamieC on 2007-01-18
Error 21 relates to non-existent disk. 

When the grub menu appears (press ESC if it does not automatically), press 'e' to edit the first boot option.

Paste the value of the root line, it will read something like (hd0,0).

---

### Post by GeraldR63 on 2007-01-21
> **JamieC said:**
> Error 21 relates to non-existent disk. 

When the grub menu appears (press ESC if it does not automatically), press 'e' to edit the first boot option.

Paste the value of the root line, it will read something like (hd0,0).

Error 21 means that it is not possible to load stage 1.5. If this is not possible  system hangs.

---

### Post by veliro on 2007-01-21
Same problem here...

I have just got a new computer (p5b deluxe wifi edition..)

I have tested with ide and sata disk's, no luck...

---

### Post by GeraldR63 on 2007-01-21
Hello Kristoffer,

there are two solutions. 

First: Remove your IDE drive and use just SATA drives only. 
Second: Add additional SATA controller. I've attached all IDE drives to a SIL680 Ultra ATA RAID controller. After correct BIOS and RAID controller setup everything runs perfect.

In my opinion Grub can not deal with IDE drives at this board. Mistake seems to be that stage 1 seems to search for stage 1.5 at a different drive (read funny story at the end of this message). No idea why.

OS works perfect with this board! This seems to be  a  problem of Grub (the boot loader, I don't believe that) and not the OS (Ubuntu) or ** a bug in ASUS BIOS ** (seems to be more likely). I figured out that first IDE drive is sometimes not /dev/sda but /dev/sde. No idea why...

At [ Image and complete description of an ASUS P5B server]("http://www.oraforecast.com/orawiki/index.php/Images_of_OraForecast.com_servers") you can find a complete list of products which makes Ubuntu 6.10 installable with ASUS P5B. 

Adding an Ultra ATA controller or removing IDE drive is  just a workaround. Nevertheless it's a fast workaround. Ultra ATA  controller cost 35 Euro/40 USD and debugging Grub will be time consuming and very expensive!

I tried all possible BIOS configurations  and after a dozen of reboots I gave up and bought an IDE controller.

I've done with this board something very funny:

I've installed Ubuntu 6.10 at a SCSI drive. Than I've installed Fedora Core 6 at the first IDE drive (I've no SATA drive attached) and whoopss Ubuntu booted from SCSI drive. It seems that stage 1 searches for stage 1.5 on a different drive if using this board! 

Than I tried to install with only one attached drive, only one SCSI drive. No chance. 

This seem to be something for a real Grub expert changing some lines of Grub's coding or for ASUS to fix their BIOS.

---

### Post by veliro on 2007-01-21
Ubuntu works fine here now :) Running from a harddrive on the board ide controller...

I used xubuntu-6.10-alternate-i386.iso. When the installation was done i pressed the go back button, installed lilo and the system hanged... Then i rebooted, used the recover system option from the cd and installed lilo again. Then i rebooted and ubuntu hanged, so i rebooted with the cd again and used the start from first harddisk option, and then it worked fine...

Super :)

---

### Post by Aurdal on 2007-01-23
I managed to get it working by installing LILO, as boot loader, would anyone know how I can do a dual boot with XP like this? I wouldn't mind editing the boot.ini file from the XP installation, but I don't know waht to put in it. :)

---

