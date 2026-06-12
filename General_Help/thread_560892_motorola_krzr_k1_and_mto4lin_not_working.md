---
title: "motorola krzr k1 and mto4lin not working"
date: 2007-09-26
forum: General Help
---

### Post by lime4x4 on 2007-09-26
Trying to get my new phone to work with linux. Moto4lin won't connect to it but ubuntu does detect the phone. Here is my dmessage output

Sep 26 22:32:58 john-feisty kernel: [  328.408784] usbcore: registered new interface driver cdc_acm
Sep 26 22:32:58 john-feisty kernel: [  328.408789] drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
Sep 26 22:33:11 john-feisty kernel: [  341.420594] usb 2-4.4: new full speed USB device using ehci_hcd and address 6
Sep 26 22:33:11 john-feisty kernel: [  341.530296] usb 2-4.4: configuration #1 chosen from 1 choice

I'm using a regular usb cable to connect the phone to the pc? What i'm i missing here?

---

### Post by mikeyrb on 2007-10-01
Have you taken a look at [http://moto4lin.sourceforge.net/wiki/KRZR_K1]("http://moto4lin.sourceforge.net/wiki/KRZR_K1")?  I've used that guide and it worked.  I believe your usb connection needs to be data connection, rather than memory card (as set on your phone Settings->Connection->USB Settings).

---

### Post by brundlelinux on 2008-03-28
Any updates on this thread?  I just got a KRZR K1 and am making my first attempts at hacking it with moto4lin, but I'm stumped as to how to switch to P2K.  I have the product and vendor IDs correct, but it won't play ball.  If anybody is alive on this thread, I could use the assistance.

---

### Post by jack_spratt on 2008-05-21
moto4lin is ancient; not updated in years. 

I'm hoping that using a memory card and setting the phone to use it under 'connectivity' will allow direct access to it like a USB storage device.

Anyone tried this? Will it work? Are there other ways of accessing the internal memory?

---

### Post by rosegarden78 on 2008-07-16
No, I tried for hours to access internal memory.  I thought the phone didn't have a memory card slot.  However, a hit a website showing me where the slot was hidden - on top of the SIM card!  It is a Micro-SD card.

Luckily, I had a Micro SD card so I inserted it.  Now the MOTO KRZR can be seen by Ubuntu in Memory Card mode.  But, no, I think it's impossible to mount the KRZR without a memory card.

I did see a couple files under /proc/scsi, /dev/sg* and /dev/scd* though.

---

