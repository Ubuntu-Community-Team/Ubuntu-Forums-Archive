---
title: "boot from external ssd on usb 3.0 port"
date: 2013-08-07
forum: General Help
---

### Post by psychomieze on 2013-08-07
Hello everybody,

I'm trying to install an Ubuntu to an external SSD drive with USB 3.0. 

So far it is working as long as I use a 2.0 port. I searched and tried a lot. What happens is:

* GRUB is working (UUID is correct, starts to load Ubuntu)
* I'm dropped to initramfs as the root partition is not found when using USB 3.0

The internet suggests that I need to load the xhci_hcd kernel drivers for initramfs. Tried that first by using dracut, next (again fresh install) by editing /etc/initramfs-tools/modules adding xhci_hcd and then running update-initramfs -u. When trying with dracut lsinitrd did not say anything about xhci. I looked around some more and found out that in newer kernels the xhci module is built-in, so no .so file. I'm not sure how to continue. 

Hard facts:
* Ubuntu 13.04 / 13.10 tested - currently 13.10
* Kernel: 3.10.0-6-generic

If you need more information just tell me. Thanks for any help!

Susanne

---

### Post by Jackson_Wiegman on 2013-08-07
I have seen the same thing. From my researching and testing, I believe this depends on your BIOS and possibly UEFI. I have a few newer devices (<6months, all American Megatrends BIOS) that will not boot Ubuntu on a USB 3 port. I have two slightly older device (~1 year old, NOT American Megatrends) that boot fine on USB 3.

---

### Post by sudodus on 2013-08-07
Welcome to the Ubuntu Forums :-)

Im running 3.10.0-5-generic #14-Ubuntu SMP Mon Jul 22 15:25:20 UTC 2013 i686 i686 i686 GNU/Linux right now. Probably it was an earlier alpha version, when I tried it from a USB 3 device in a USB 3 port of a Toshiba laptop. It worked. There was no issue because of USB 3. But I did notice, that if there was another boot USB drive in a USB 2 port, the USB 2 one was given priority before the USB 3 drive.

What kind of USB 3 system is there in the computer? Was it built-in and delivered with the computer, or a card that you added afterwards? How old is it? What brand name and model? Not that I can tell the difference, but there might be someone else with experience from that particular hardware.

---

### Post by psychomieze on 2013-08-08
Thank you for your replies.

The computer is a fujitsu lifebook s-series(S781). The USB 3 port is built-in and I have no other USB drive in an USB 2 port. As I have no idea what else to do and USB 2 is too slow, I ordered now an USB to eSATA adapter and will try with the eSATA port. 

If you have any ideas how to get this working with USB please let me know.

---

### Post by sudodus on 2013-08-08
According to this link

[http://globalsp.ts.fujitsu.com/dmsp/Publications/public/ds-LIFEBOOK-S781.pdf](http://globalsp.ts.fujitsu.com/dmsp/Publications/public/ds-LIFEBOOK-S781.pdf)

there is an eSATA & USB combo port in addition to the USB 3 port. If that is the case for your particular computer, you can easily boot from an external box via eSATA. There are several external boxes with eSATA and USB 3 ports by for example Akasa and IcyBox. You can have any kind of SATA drive inside, for example an SSD. I have done it and I know that it works. eSATA works pretty much like an internal SATA connection.

It might be possible to find an adapter to connect a USB 3 pendrive via the eSATA port, but I have never done it, and I don't know if it would be possible to boot that way. (I have an adapter, that works the other way, connecting an eSATA device via a USB 3 port. And that works for me, but I guess you don't want that.)

You might also get good results (both speed and ability to boot) with a Sandisk Extreme 32 GB pendrive, which has USB 3 capability. See this link. I have two such pendrives that work well as boot devices in USB 3 ports.

[Link to USB 3.0 Flash Drive Speed Tests]("http://www.whoratesit.com/Best-Flash-Drive/Comparison/1")

---

