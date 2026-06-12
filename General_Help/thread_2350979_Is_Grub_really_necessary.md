---
title: "Is Grub really necessary?"
date: 2017-01-29
forum: General Help
---

### Post by prairiepanda on 2017-01-29
I have my PC set up to dual boot with Windows 10 and Ubuntu 16.04, but the two operating systems each have their own dedicated drives so I have Win10 on the default boot drive and switch to Ubuntu using the MOBO's F12 boot menu. Grub is installed on the same drive as Ubuntu, so every time I boot the Ubuntu drive it takes me through Grub first, which just adds unnecessary time to the boot process. Is it possible to just remove Grub altogether and boot straight to Ubuntu, since it has its own dedicated drive anyway? It's not a big deal, but the Grub interface is ugly and booting my PC twice in a row seems like a waste of time.

---

### Post by efflandt on 2017-01-29
You don't give any clue what hardware you have. If it is an older computer and/or using BIOS mode instead of UEFI, you could simply set your Linux drive as the boot drive in BIOS and select Ubuntu or Windows from the grub menu. There is a way to configure grub to save/default the last system it booted, so you could simply hit Enter to boot whatever you booted last, instead of waiting for grub delay to time out, by setting the following in /etc/default/grub and running **sudo update-grub**```
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
```

---

### Post by Dennis N on 2017-01-29
> Is it possible to just remove Grub altogether and boot straight to Ubuntu, since it has its own dedicated drive anyway?

No. Linux and Windows OS both need a boot loader to load and start the OS. So you can't eliminate the boot loader. Other boot loaders besides GRUB exist for Linux - some are listed here:

[https://wiki.archlinux.org/index.php/Category:Boot_loaders](https://wiki.archlinux.org/index.php/Category:Boot_loaders)

GRUB = GRand Unified Bootloader



Use Google for details on how it works.

---

### Post by prairiepanda on 2017-01-29
I have both Windows and Ubuntu booting in BIOS mode. I'm not sure exactly what other hardware info is relevant; but I have a Gigabyte Z97-D3H with Intel i7-4790k, nVidia GTX 970, and 16GB DDR3 RAM. Windows is booting from a SATA3 SSD and also handles a separate HDD, while I have Ubuntu booting from an M.2 SATA SSD (configured with swap, root, and home partition) and no other drives.

I don't boot Windows from Grub; it goes through the default windows bootloader. I like to have Windows boot automatically on startup because I only use Linux for specific purposes, and mainly just use Windows. I just want to be able to boot Linux directly from the F12 boot menu without waiting around for Grub to do its thing.

Is there a bootloader for Linux that will ignore the other available systems and just boot straight to Ubuntu, just as the Windows bootloader does for Windows?

---

### Post by deadflowr on 2017-01-29
> Is there a bootloader for Linux that will ignore the other available systems and just boot straight to Ubuntu, just as the Windows bootloader does for Windows?
Yes, if doing BIOS mode boot switching then disable os-prober.
This will set it so Windows is never part of the GRUB menu, as it disables GRUB from even looking for other operating systems.
You just need to add a line to the /etc/default/grub file:
GRUB_DISABLE_OS_PROBER=true
then save and update grub
```
sudo update-grub
```
then when booting into Ubuntu, like Windows, you should only see the boot menu when a problem happens, like accidental power offs, and such.

---

### Post by prairiepanda on 2017-01-29
Thank you, that's exactly what I wanted! I had fiddled with the Grub timeout options but didn't consider the role of the OS prober.

---

### Post by mastablasta on 2017-01-30
grub can be customized and is rather nice compared to windows boot manager:
[SIZE=2]http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/
[/SIZE]

also grub timeout set at 0 will not show grub on boot.

---

### Post by prairiepanda on 2017-01-30
> **mastablasta said:**
> 

also grub timeout set at 0 will not show grub on boot.

I did try that, but changing that alone didn't work. I think because grub was finding two operating systems? But setting the timeout to 0 and turning off the OS prober did the trick. Ubuntu still takes longer to load than Windows, but I can live with it.

---

### Post by yancek on 2017-01-30
>  Ubuntu still takes longer to load than Windows, but I can live with it. 		

Not really because the default for windows 10 is to have hibernation always on.  Otherwise it would take much longer to boot.

---

### Post by prairiepanda on 2017-01-30
> **yancek said:**
> Not really because the default for windows 10 is to have hibernation always on.  Otherwise it would take much longer to boot.

I have hibernate and fast boot disabled for Windows because it was causing issues with my network driver. I'm not sure what's slowing down Ubuntu's boot time relative to Windows, but Ubuntu makes up for the slow boot with a much faster login. Boot time is 21s for Windows, 26s for Ubuntu, but then Windows takes 6 seconds to fully initialize my desktop after login whereas Ubuntu only adds 1-2 seconds, so they balance out now that Grub isn't holding me up.

---

