---
title: "Bios upgrading from ubuntu?"
date: 2006-11-11
forum: General Help
---

### Post by Funzo22 on 2006-11-11
I own an acer aspire 5000 laptop, I have upgraded the ram to 2GB, and it shows up as 1.2GB installed. On acer's website, they have a bios upgrade that is suppose to fix this problem, but they only give windows instructions!

Winflash: [http://www.acerpanam.com/synapse/forms/portal20.cfm?recordid=2412&formid=3394&website=AcerPanAm.com/canada&siteid=7297&words=all&keywords=&areaid=17](http://www.acerpanam.com/synapse/forms/portal20.cfm?recordid=2412&formid=3394&website=AcerPanAm.com/canada&siteid=7297&words=all&keywords=&areaid=17)
Bios: [http://www.acerpanam.com/synapse/forms/portal20.cfm?recordid=2544&formid=3394&website=AcerPanAm.com/canada&siteid=7297&words=all&keywords=&areaid=17](http://www.acerpanam.com/synapse/forms/portal20.cfm?recordid=2544&formid=3394&website=AcerPanAm.com/canada&siteid=7297&words=all&keywords=&areaid=17)

I decided running it through wine was an awful idea, so I was looking for maybe a piece of open source software that could replace winflash...


Help is appreciated!!

Thank you

---

### Post by commonplace on 2006-12-26
Anyone have a solution to this? My wife's new laptop also uses the WinFlash utility to update the BIOS and HP/Compaq doesn't seem to make any BIOS updates available through another method. How can I update the BIOS on her laptop without Windows?

---

### Post by roger99 on 2006-12-26
I'm also looking for an answer to this question, my dell laptop's bios update runs in windows and I really don't want to have to repartition and install windows just to run a bios update.  It's not essential mind, I'd just rather keep up to date!

---

### Post by le_vainqueur on 2006-12-26
I'm also curious how to do bios updates in Ubuntu :)

---

### Post by roaldz on 2007-07-27
Iv'e also been looking on the web on this topic. There's no easy to use utility for ubuntu at this time.

I found that you could use the "nvram" module (non-volatile RAM) to read/write your bios. I didn't get any success at this.

I also found that the guys from LinuxBIOS have a utility called flashrom which you can use to flash your bios.
Available here: [http://linuxbios.org/Flashrom](http://linuxbios.org/Flashrom)

Tried this also, but I get this:

```

roald-laptop# flashrom -r backup.bin
Calibrating delay loop... ok
No LinuxBIOS table found.
Found chipset "ICH7M": Enabling flash write... OK.
No EEPROM/flash device found.

```

So no success there. Does anyone have this working? Or are you just forced to use (free)DOS on a bootdisk (what if you don't have a floppy drive?)

Roald

---

### Post by tombott on 2007-07-27
You could use a WinPE boot Cd like [Barts Boot CD]("http://www.nu2.nu/pebuilder/") for example.

You would need to save the bios update and flash util to USB Memory stick or CD as WinPE etc. won't be able to read your Linux partitions.

Not ideal I know but it will get around re-partitioning HD's and installing Windows.

By the way to use WinPE or Barts Boot Cd you should own a relevant Windows XP License!

[B][I]Licensing issues

In order to make a BartPE installation, your must have a properly licensed copy of the operating system. BartPE does not grant users who do not have a proper Windows XP/2003 license the right to use a BartPE installation.

Also, according to the Microsoft EULA for Windows XP/2003, a user may not simultaneously use more installations of these operating systems than the user has license(s) for. This also goes for BartPE. In practice this means that the user may not use, for instance, a single license installation on one computer while simultaneously using a BartPE installation (created using that license) on another computer.

More information:

    * Your local Microsoft Windows end-user license agreement (c:\WINDOWS\system32\eula.txt)[/I][/B]

---

### Post by Espreon on 2007-07-27
Yeah, but I wonder if the boot cd would be stable enough to do a dangerous (correct me if I am wrong) task like upgrading the BIOS (espically when something goes wrong). It would be nice if the OEMs would support Linux a bit more. Maybe we can expect a BIOS upgrading method for Ubuntu provided by Dell, since they are supporting Ubuntu alot more. I am sure we will be provided with such tools and (maybe) drivers for their Lexmark-based printers (unfourtanetly my Mom got one, but she uses the Winblows partion and I have another printer that works fine with Ubuntu).

---

### Post by tombott on 2007-07-27
> **Espreon said:**
> Yeah, but I wonder if the boot cd would be stable enough to do a dangerous (correct me if I am wrong) task like upgrading the BIOS (espically when something goes wrong). It would be nice if the OEMs would support Linux a bit more. Maybe we can expect a BIOS upgrading method for Ubuntu provided by Dell, since they are supporting Ubuntu alot more. I am sure we will be provided with such tools and (maybe) drivers for their Lexmark-based printers (unfourtanetly my Mom got one, but she uses the Winblows partion and I have another printer that works fine with Ubuntu).


I hear what your saying, but I find the WinPE boot Cd's very reliable.
We use them to test on PC's we have built before installing OS and shipping to client.
The tests we do are 'Burn-In' test's. These basically max out the PC CPU, RAM, HDD access etc, and this works without any problem.

In an ideal world they would right the app's for linux but there you go.

OP are you sure there isn't a boot disk version of the firmware you need?

All bios updates I have done in the past require you to boot from floppy and install bios updates.

Tom.

---

### Post by rbmorse on 2007-07-27
> **Espreon said:**
> Yeah, but I wonder if the boot cd would be stable enough to do a dangerous (correct me if I am wrong) task like upgrading the BIOS (espically when something goes wrong). 

Intel now distributes BIOS updates in .ISO form that produce self-booting cd's that contain both the new BIOS image file and a command-line installer. They don't seem to be worried about stability in a CD boot environment.

As long as your computer will boot from a CD, there should be no problem doing a BIOS update from a DOS boot cd.  The BIOS image and DOS installer file can either be placed on the CD when it's created. or you can use one of the other strategies outlined above.

---

