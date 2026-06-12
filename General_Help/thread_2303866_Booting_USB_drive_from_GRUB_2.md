---
title: "Booting USB drive from GRUB 2"
date: 2015-11-22
forum: General Help
---

### Post by Milleuros on 2015-11-22
Dear Ubuntu forums,

This is not really an Ubuntu-related question but I figured out you might help me.

Basically : I have a dual boot Windows 10 / Ubuntu 14. GRUB 2 is installed as boot manager.
Windows 10 broke. I am trying to repair it using a recovery USB stick made through Windows when it worked. To do that, I should boot on that USB drive. However I cannot find how to do that on GRUB 2.

If I access GRUB command line and type *ls*, all that I see is related to *hd0* :
```
(hd0) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)
```

I tried writing :
```
set root=(hd1,1)
chainloader +1
```

To what grub answers me : *error: hd1 cannot get C/H/S values*

Looking into Google did not help me to understand what is going on and what should I do to be able to boot on that USB drive.

My computer is 5 years old, it should support USB boot (computer not as old as Windows 7).

---

### Post by grahammechanical on 2015-11-22
How did you install Ubuntu 14.04? Did you not do it from a DVD disc or a USB memory stick? Did you not make some change or other in the UEFI boot system to force the motherboard to look to a USB port or DVD drive for an operating system before looking to a hard disk?

You must do something similar again. Surely. In my case I have a BIOS boot system and I use the BIOS settings to direct which of 2 hard drives to load an operating system from and it is the same if I wish to load an OS from the DVD drive or a USB port.

Regards

---

### Post by Milleuros on 2015-11-22
> **grahammechanical said:**
> How did you install Ubuntu 14.04? Did you not do it from a DVD disc or a USB memory stick? Did you not make some change or other in the UEFI boot system to force the motherboard to look to a USB port or DVD drive for an operating system before looking to a hard disk?

You must do something similar again. Surely. In my case I have a BIOS boot system and I use the BIOS settings to direct which of 2 hard drives to load an operating system from and it is the same if I wish to load an OS from the DVD drive or a USB port.

Regards

I followed some tutorials. Basically I made a DVD, inserted the DVD in the computer, rebooted and voilà I could install. The installation procedure included an automatic installation of GRUB 2. So I made the DVD boot *before* having GRUB on my computer.

Problem is that now I have an USB stick because Windows 10 standard recovery procedure is an USB stick and *not* a DVD.

---

### Post by oldfred on 2015-11-22
You should normally just go into UEFI/BIOS and choose to boot flash drive. 
In boot tab it should show the flash drive. If an older system then it only is BIOS.
My older system had many USB boot options like USB-floppy, USB-DVD etc, but none of those would boot flash drive. Flash was only bootable as another hard drive under hard drive boot choices.

But flash drive will only be bootable if correctly configured as boot device.

---

### Post by Milleuros on 2015-11-22
> **oldfred said:**
> You should normally just go into UEFI/BIOS and choose to boot flash drive. 

You are right. For some reason I thought that the boot process now went through GRUB. I was able to boot on my USB drive. Thanks !

---

