---
title: "Simulate DVD-ROM"
date: 2007-10-22
forum: General Help
---

### Post by mariano.pelizzari on 2007-10-22
Hi everyone,

I was wandering if a can simulate a DVD-ROM in ubuntu much like deamond tools do in windows. I want to try ubuntu studio in VMware Server and I don't have a DVD-ROM/RAM. I tried mounting the iso file in the /media/cdrom/ directory but it didn't work.

Any sugestion?

Thks

---

### Post by UK-Wobbie on 2007-10-22
> **mariano.pelizzari said:**
> Hi everyone,

I was wandering if a can simulate a DVD-ROM in ubuntu much like deamond tools do in windows. I want to try ubuntu studio in VMware Server and I don't have a DVD-ROM/RAM. I tried mounting the iso file in the /media/cdrom/ directory but it didn't work.

Any sugestion?

Thks

The only simulate is Wine.. It can play Windows programs in Linux Ubuntu! [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
Or you can have a go on using AcetoneISO2 that as got a ISO mount tool in it!
It can play DVD ISO and play Data ISO. :)
[http://www.acetoneteam.org/central.html](http://www.acetoneteam.org/central.html)

You need to instill the "fuseiso" It will help it to load and to stop it crashing... And to help it to play the DVD and Data ISO Images.
[http://packages.debian.org/unstable/admin/fuseiso](http://packages.debian.org/unstable/admin/fuseiso)


Or if you no your linux you can use this in Terminal!

"sudo mount -o loop -t iso9660 YOUR FILE NAME.iso /mnt"

But for me and the best way is to use Wne or AcetoneISO2..


I hope that helps you. :mrgreen:

---

### Post by bulletxt on 2007-10-22
yes if you need to mount iso bin img nrg mdf images or other things just stick with AcetoneISO2 ;)

---

### Post by bliep on 2007-11-09
If I unterstand well, you just want to install Ubuntu Studio from ISO in a Virtual maching using VMware server? If this is correct, then you just have to attach the ISO file as a CD rom in your VMware machine in the CD configuration (in stead of using a device). So, right click on the machine you created, then select the CDrom device. There you will see the option to use an ISO file in stead of a real CDrom device.

---

