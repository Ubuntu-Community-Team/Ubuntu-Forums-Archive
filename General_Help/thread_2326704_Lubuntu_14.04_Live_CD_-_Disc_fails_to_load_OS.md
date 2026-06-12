---
title: "Lubuntu 14.04 Live CD - Disc fails to load OS"
date: 2016-06-03
forum: General Help
---

### Post by dpad on 2016-06-03
Hey all, I don't have a lot of Linux knowledge and I'm looking for some help with an issue I'm having. I have a live CD I use for work and I just bought a new PC. The disc runs fine on my old machine but for some reason the disc is failing to load properly on the new one. I can see the boot menu, I select the OS and it starts to load, I see a purple "Lubuntu 14.04" loading screen, then the loading screen changes from purple to black, then it goes to a blank screen with a flashing cursor and no way to input anything. I can press F6 during the loading screen and I see some things during the start up process that fail (audio/backup video), also during the initial start up it looks like some other things that have to due with encryption might be failing too but the screen loads to fast for me to see it. 

I've tried running with options - acpi=off/noapic/nolapic/nomodeset 

Get the same result every time, secure boot is disabled, bios are set to UEFI+Legacy. 

MB: MSI H170A PCMATE

I'm running the 32bit i386 version of Lubuntu

Any help or ideas are appreciated, let me know if more information is needed.

I downloaded the official Lubuntu 14.04 live CD and it loaded fine.

---

### Post by ventrical on 2016-06-03
There may be some problems with geometry of an older CD burned on an older PC and then tried on an new PC. I would suggest you try to use a USB drive. To install the Lubuntu ISO there.

REgards..

---

### Post by dpad on 2016-06-03
If I just take the files from the CD and add them to a thumb drive it will just work or do I need to change anything?

---

### Post by ventrical on 2016-06-03
> **dpad said:**
> If I just take the files from the CD and add them to a thumb drive it will just work or do I need to change anything?

You need to download the Lubuntu 14.04 ISO and then install it to a thumb drive using gnome-disk-utility 'disk'.

You can then boot from the USB.

Are you running Ubuntu on your PC now? What version? Or are you using Windows to burn your CD?

Regards..

edit:

Ahh .. you already have Lubuntu 14.04 ISO. Then just use 'disks' and 'restore' the ISO image to the USB drive or you can use Startup Disk Creator depending on what version of Ubuntu you are using.

---

### Post by dpad on 2016-06-03
I need the software on the disc, its how I access my PC from home. Currently running Win10 64bit on my machine BTW.

---

### Post by ventrical on 2016-06-03
If you have an extra hdd then install Lubuntu 14.04 using the CD on your old PC. Then you can download the .ISO and use 'disks' to install to USB and then try on your new PC.

Please tell me specs of older PC?

Regards..

---

### Post by ventrical on 2016-06-03
> **dpad said:**
> 

Get the same result every time, secure boot is disabled, bios are set to UEFI+Legacy. 

MB: MSI H170A PCMATE

I'm running the 32bit i386 version of Lubuntu

Any help or ideas are appreciated, let me know if more information is needed.

I downloaded the official Lubuntu 14.04 live CD and it loaded fine.

I have pretty well two of the same MSI MoBos. You might want to try to boot (during bootup) using F11 or F12 is it? Then choose BIOS mode on your CD from the boot menu and see what happens. I still think it is geometry prob but it should work.

Regards..

---

### Post by dpad on 2016-06-03
The disc has the option to install disabled. Is there a program for windows that allows you to take software from a live CD and move it to a new system? Something like the webapp Reconstructor.

Old machine is a ASUS N61J

---

### Post by ventrical on 2016-06-03
> **dpad said:**
> The disc has the option to install disabled. Is there a program for windows that allows you to take software from a live CD and move it to a new system? Something like the webapp Reconstructor.

Old machine is a ASUS N61J

The image creating process does not work that way. Unless someone else wants to chime in:)

There should be an option in the live version to install to disk.

 You can perhaps use a virtual machine on Windows.

Your PC specs are good to go! You can install it as an alongside but you might have to install ubiquity in the live session:

```

sudo apt-get install ubiquity

```

but I would recommend that you load up the live CD on old PC and download a standard .ISO for starters.

Regards..

---

### Post by dpad on 2016-06-03
I ran it from the boot menu and it loaded, but it hangs or something after I closed the session. It shows its unmounting files and then hangs at press ENTER to exit. But the main issue is resolved, if I have to hard reset at the end of the day thats ok, I can live with that. Thanks for the help, I've been trying to fix this for a few days.

---

### Post by ventrical on 2016-06-03
If you feel your issue is solved to some  satisfaction then please mark your thread as sloved.

Regards..

---

