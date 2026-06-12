---
title: "USB3.0 speed compared to Windows"
date: 2015-05-11
forum: General Help
---

### Post by h4ck3rc1 on 2015-05-11
I understand that the Linux drivers for USB3.0 chipsets may not be as polished as Windows but is there a way to improve the speed of USB3.0 transfers or is it more involved than just the driver and file handling of the OS?

---

### Post by sudodus on 2015-05-11
I think you can get quite good data transfer speed in linux with USB 3 devices. A USB SSD drive is quite fast, while many USB 3 pendrives are slow. In this case the internal structure (the flash memory and internal management) in an SSD is much better than what is used in many USB 3 pendrives. But there are some USB 3 pendrives, that are much faster than the average. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Pendrive speed test]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

---

### Post by Mark Phelps on 2015-05-11
Personally, I've found the driver to be a major factor in transfer speed of USB 3.0 connections.  On my desktop running Windows, for example, I installed the native Renesas driver and got considerably faster transfer speeds than I did with the native MS driver -- and faster than in the Linux distros.

---

### Post by sudodus on 2015-05-11
> **Mark Phelps said:**
> Personally, I've found the driver to be a major factor in transfer speed of USB 3.0 connections.  On my desktop running Windows, for example, I installed the native Renesas driver and got considerably faster transfer speeds than I did with the native MS driver -- and faster than in the Linux distros.

Interesting :-)

For what hardware can you use the native Renesas driver?

---

### Post by Mark Phelps on 2015-05-11
> **sudodus said:**
> Interesting :-)

For what hardware can you use the native Renesas driver?

In my case, it was the Nec USB 3.0 chip on the motherboard.  I did a search for drivers and found that station-drivers had a link to the NEC/Renesas page with both the drivers and firmware.  Since both are chip model and version specific, you need the ID off the chip to download the correct files.

---

### Post by sudodus on 2015-05-11
Thanks for sharing :-)

---

