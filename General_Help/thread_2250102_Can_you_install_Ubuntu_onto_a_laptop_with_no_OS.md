---
title: "Can you install Ubuntu onto a laptop with no OS?"
date: 2014-10-26
forum: General Help
---

### Post by mike249 on 2014-10-26
I downloaded Ubuntu from my desktop onto a USB flashdrive, with the intention of installing it on my laptop ...But when I try to load Ubuntu on my laptop I get "SYSLINUX 4.07 EDD 2013-07-25 Copyright (C) 1994-2013 H. Peter Anvin et - al" 

That's it. Nothing else happens. Yet, when I plug the USB into my desktop, Ubuntu loads up perfectly fine. Why would it work on my desktop, but only display the 'SYSLINUX...." message on my laptop?

---

### Post by sudodus on 2014-10-26
Yes, you can install Ubuntu into a laptop with no OS :-)

The installed OS is not involved when the computer boots from a USB pendrive. But the BIOS/UEFI system is, and the hardware of the computer.

Please describe your laptop computer, both hardware, and the BIOS/UEFI settings.

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by keltonoliver1957 on 2014-12-05
If your computer has UEFI, installing a non-Windows OS can be a real challenge. I suspect the UEFI was designed specifically to reject non-Windows OSs (as opposed to just being an unfortunate side effect). Sometimes you can get it to work by tweaking the BIOS/UEFI settings, but in one case I never got it to work.

---

### Post by eight.coffee.beans on 2014-12-05
> **mike249 said:**
> [B][SIZE=2]I downloaded Ubuntu from my desktop onto a USB flashdrive, with the intention of installing it on my laptop ...But when I try to load Ubuntu on my laptop I get "[/SIZE][SIZE=2]SYSLINUX 4.07 EDD 2013-07-25 Copyright (C) 1994-2013 H. Peter Anvin et - al" 

That's it.[/SIZE] [SIZE=2]Nothing else happens. [/SIZE][SIZE=2]Yet, when I plug the USB into my desktop, Ubuntu loads up perfectly fine. Why would it work on my desktop, but only display the 'SYSLINUX...." message on my laptop?[/SIZE][/B]

Have you configured your laptop's BIOS/UEFI to boot from USB?

---

### Post by Darth Riker on 2014-12-05
> **mike249 said:**
> [B][SIZE=2]I downloaded Ubuntu from my desktop onto a USB flashdrive, with the intention of installing it on my laptop ...But when I try to load Ubuntu on my laptop I get "[/SIZE][SIZE=2]SYSLINUX 4.07 EDD 2013-07-25 Copyright (C) 1994-2013 H. Peter Anvin et - al" 

That's it.[/SIZE] [SIZE=2]Nothing else happens. [/SIZE][SIZE=2]Yet, when I plug the USB into my desktop, Ubuntu loads up perfectly fine. Why would it work on my desktop, but only display the 'SYSLINUX...." message on my laptop?[/SIZE][/B]

Just a question - did you follow the steps outlined here: [http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389) (make sure you read the second post about UEFI if that applies to you).

Personally, since I was using a Windows machine to make the bootable USB drive, when loading just one iso to a usb I used the method outlined here make the USB drive: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

---

### Post by mörgæs on 2014-12-05
The thread has been inactive for more than a month. 
Thanks for trying to help but there's no need for posting.

---

