---
title: "Ubuntu Live USB boot. No internet connection."
date: 2015-07-31
forum: General Help
---

### Post by mustafa11 on 2015-07-31
Hey there, im pretty new to this linux operation system.
I've created a live usb that contains Ubuntu in it from a windows machine and connected the usb into my macbook.
I can successfully boot in the operation system however it doesnt seem to recognise any wireless networks?

Any solution to this?

---

### Post by leunam12 on 2015-07-31
Seems like the wireless device does not work "out of the box". Open terminal and type lspci and press enter and post the result. The solution will depend on the kind of wireless device that you have. Another solution is to buy a USB wireless device that works out of the box, I particularly have used the DWA-125 in the past, it is a very good adapter.

---

### Post by grahammechanical on 2015-07-31
Ubuntu is open source software. So, the Ubuntu live session does not have any proprietary drivers. Not for video adapters or WiFi adapters. But once we have installed Ubuntu then Ubuntu will make it easy for us to install certain proprietary drivers. But the Ubuntu that we download and burn to a DVD disc or USB stick does not include proprietary software because of the different licensing requirements of the software and the legal requirements of different governments.

You may need to make a wired connection first.

Regards.

---

