---
title: "Memory Stick Problems"
date: 2008-06-03
forum: General Help
---

### Post by capg88 on 2008-06-03
Hi!
Im a beginner in the world of Linux. Im having a problem with my internal card reader. The specifications are below. The problem Im having is that it doesnt work! I insert a memory stick adapter for a SanDisk M2 memory. I had read a lot about it in many forums, but any solution works to me. Does it have a solution? Here is the specifications.

08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

Thanks

---

### Post by Sam Lars on 2008-06-07
I have the same hardware, and I can't get MS or MS Pro to work on it either.
What version of Ubuntu are you using?  I'm on Hardy.
I'm going to be away for a while, but when I come back I can experiment a bit with this.  I put in an SD card a few weeks ago and it worked fine.

---

### Post by capg88 on 2008-06-08
Hi Sam!
Im running hardy too. Thanks for your help. Im going to try with a SD.

---

### Post by underdog512 on 2008-06-08
have these stick already been formated or are they brand new sticks?

---

### Post by Calmor on 2008-06-09
I'm having the same problem as well.  I've tried to reload the ricoh-mmc module to no avail.  SanDisk cards work fine and lightning fast, but the Memory Stick Pro (Sony branded) is not recognized.  dmesg shows the following:

```

ricoh-mmc: Ricoh MMC Controller disabling driver
ricoh-mmc: Copyright(c) Philip Langdale
ricoh-mmc: Ricoh MMC controller found at 0000:01:09.2 [1180:0843] (rev 12)
ricoh-mmc: Controller is now disabled

```

The modprobe -v output is:

```

insmod /lib/modules/2.6.24-18-generic/kernel/drivers/mmc/host/ricoh_mmc.ko

```

I'm assuming that it's normal since SanDisk cards work fine.  The machine in question is running Hardy 64-bit on an HP 2700 series laptop (dv2745se).  Both cards are previously in use (not new) and can be read by the machine in Windows.

Hope this can help - if there's any other data needed, I'll gather that as well.

---

### Post by capg88 on 2008-06-11
I had already formated my memory stick, but I still have the same problem. I tried to connect the stick using my phone and it works! But the card reader dont :(. I will keep trying.

---

### Post by Haf on 2008-06-15
I found a thread on the Kernel Mailing List from about a year or so ago stating that the Memory stick part of the reader is not supported because the specifications have not been released and that support will most likely take some time. It seems that nothing has changed since then. :(

---

### Post by core on 2008-08-06
I can't use my Memory Card on Hardy either. On Windows works fine, and I already have thousands of pictures there from my Cybershot camera and therefore formatting in linux is not an option.

This is a SanDisk MemoryStick Pro Duo with 4GB, on a Vaio VGN Series laptop.

Any ideas?

---

### Post by core on 2008-08-06
Fixed, thanks to:

[http://ubuntuforums.org/showthread.php?t=848005](http://ubuntuforums.org/showthread.php?t=848005)

I think this is not a Vaio specific issue, so you could try.

---

