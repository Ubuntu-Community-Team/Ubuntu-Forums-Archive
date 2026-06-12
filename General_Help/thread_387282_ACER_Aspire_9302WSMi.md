---
title: "ACER Aspire 9302WSMi"
date: 2007-03-18
forum: General Help
---

### Post by slacpersona on 2007-03-18
Hi,
I am tring to install Ubuntu (ubuntu-6.10-desktop-amd64.iso) on my ACER Aspire 9302WSMi (AMD Turion 64x2) and get:
 
Decompressing Linux... done.
Booting the kernel.

And then nothing happens. I just have to unplug the battery to restart the computer.
Anybody can help?
Thanks

---

### Post by teaker1s on 2007-03-18
first check the md5sum of the download you burned
secondly burn iso slow as possible and verify it burned okay

Next if live install won't work you may need alternate.iso (text install)
**but try this first**

Installation

First things first: if your laptop fails to boot the LiveCD (i.e. hangs at a certain point), then you most likely have a common problem with "apic."

Solution: When given boot options for the LiveCD, press F6 for other options and you should see a command line with commands already entered. Simply add any or if needed all

```
NOAPIC NOAPCI
```

---

### Post by slacpersona on 2007-03-18
md5sum is OK and I burned in 8X

With option NOAPIC NOAPCI, I get an I/O error: error reading boot CD
isolinux: Disk error FF, AX=4280, drive 9F

---

### Post by HughR on 2007-12-29
> **slacpersona said:**
> md5sum is OK and I burned in 8X

With option NOAPIC NOAPCI, I get an I/O error: error reading boot CD
isolinux: Disk error FF, AX=4280, drive 9F

Interesting.  I have an Acer Aspire 9300-3089.  The Fedora 8 Live disk gives me this error too.  Actually, AX is slightly different: 425D.

I also have (different) troubles with Ubuntu 7.10 Live.  See [http://ubuntuforums.org/showthread.php?p=4032382](http://ubuntuforums.org/showthread.php?p=4032382)

Very annoying.  I currently blame Acer but I don't know enough to point my finger accurately.

The BIOS on my machine is 1.17.  The latest version is 1.20 but it is only released for Windows XP and my machine came with Windows Vista.

I suspect that the 42 in AH (the top half of AX) signifies the "extended read" function code for the BIOS int 13h routine.  I don't know what the next two hex digits signify.  See 3.1.2 in [http://www.phoenix.com/NR/rdonlyres/9BEDED98-6B3F-4DAC-BBB7-FA89FA5C30F0/0/specsedd11.pdf](http://www.phoenix.com/NR/rdonlyres/9BEDED98-6B3F-4DAC-BBB7-FA89FA5C30F0/0/specsedd11.pdf)

---

### Post by HughR on 2007-12-31
> **HughR said:**
> The BIOS on my machine is 1.17.  The latest version is 1.20 but it is only released for Windows XP and my machine came with Windows Vista.


I have noticed no improvements.

I've updated the BIOS to v1.20, using a technique outlined here (in French): [http://www.nautile.org/Flasher-un-bios-de-portable-sous.html](http://www.nautile.org/Flasher-un-bios-de-portable-sous.html)

I've not noticed any improvement.

I think I know how to reliably generate a (CD) disk I/O error from the splash screen.  Just wait at the initial choice screen (Start Ubuntu, Install with driver update, ...) until the DVD drive shuts down (not just quiet, but an audible clunk after that (about 20 seconds later still)).  Then the next read will fail.

I can get a related problem from the BIOS setup screen.  I have my first boot device set to DVD drive.  On boot, hit F2 to get into setup screen.  Wait for DVD to shut down (as above).  Then exit without saving changes.  It will fail to boot the CD and it will proceed to boot (WinVista) from the hard drive.

My guess is that the BIOS extended read function is buggy.

Work around 1: don't be slow editing options!  Boot linux itself before the DVD drive shuts down.

Work around 2: if the DVD drive has stopped and you are about to continue the booting process, pop the disk out and in.  That will start up the drive.  Once it is up to speed, let the boot go ahead.

---

