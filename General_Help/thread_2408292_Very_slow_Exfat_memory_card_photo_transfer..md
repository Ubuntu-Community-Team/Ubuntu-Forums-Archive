---
title: "Very slow Exfat memory card photo transfer."
date: 2018-12-16
forum: General Help
---

### Post by Lloyd_Hayes on 2018-12-16
1st My rant: I am beginning to hate Ubuntu Studio 18.10.  I have had it installed for about a week, and I have installed it three times to get it to work at all. (And yes, the checksums were checked.) Version 18.10 has far too many bugs. And reporting them also seems to be a problem. It seems that the only way to report them is if the software itself decides to report them.

Here is my latest bug. I have a 2 hour transfer of my 664 MB camera photos from a 64 GB Memory card, using a built-in hardware card reader. 
These transfers took just a few seconds with Ubuntu Studio 18.04. 
But the transfers are now measured in hours with Studio 18.10.

I am reminded of just over a year ago when Linux programmers went crazy over security concerning external storage devices.

Anyway, there was no Exfat drivers in the Ubuntu site for version 18.10, so I got the exfat-fuse driver using the Synaptic software.

I have camera memory cards up to 128 GB in size. I don't even want to think about filling those up and transferring the files to my desktop at this speed. My cameras shoot 24 MP images, and files are saved in both RAW and a high-quality version of the JPG file formats. So I end up with some hefty photo files. And each camera hold 2 memory cards. (I have several cameras.)

What do I have to do in order to get faster transfer speeds again, besides installing a previous Ubuntu version? (Which is starting to sound pretty good.)
:mad:

---

### Post by him610 on 2018-12-17
> These transfers took just a few seconds with Ubuntu Studio 18.04.
If you wanted stability then why did you install 18.10? Unless you are prepared for hiccups and unexplained issues, you probably should not be using the interim releases. You probably would be better off reinstalling LTS 18.04.

---

### Post by sudodus on 2018-12-17
> **him610 said:**
> If you wanted stability then why did you install 18.10? Unless you are prepared for hiccups and unexplained issues, you probably should not be using the interim releases. You probably would be better off reinstalling LTS 18.04.

+1

Unless there is a specific problem, I recommend that you stay with the LTS releases (now 18.04) until the first point release of the next LTS (expected to be 20.04.1 LTS in July or August 2020). That way you will have debugged and polished software, that will be well maintained for at reasonable period of time.

---

### Post by partofthething on 2018-12-22
Also seeing the slowness.. it's about 10-50x slower, if not more. I see  nothing notable in htop or iotop. I do see messages in syslog that are  probably related:
```
[FONT=courier new]
 26 Dec 21 22:15:41 box kernel: [469298.638082] usb 2-3.4.2: Disable of device-initiated U1 failed.
 27 Dec 21 22:15:47 box kernel: [469303.758184] usb 2-3.4.2: Disable of device-initiated U2 failed.
 28 Dec 21 22:15:47 box kernel: [469303.838771] usb 2-3.4.2: reset SuperSpeed Gen 1 USB device number 4 using xhci_hcd
 29 Dec 21 22:15:47 box mount.exfat: failed to read cluster 0x8c47b
 30 Dec 21 22:15:47 box mount.exfat: failed to read cluster 0x8c47c
 31 Dec 21 22:15:47 box mount.exfat: failed to read cluster 0x8c47b
 32 Dec 21 22:15:47 box kernel: [469304.207338] sd 6:0:0:0: [sdd] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
 33 Dec 21 22:15:47 box kernel: [469304.207346] sd 6:0:0:0: [sdd] tag#0 Sense Key : Unit Attention [current]&#8901;
 34  Dec 21 22:15:47 box kernel: [469304.207352] sd 6:0:0:0: [sdd] tag#0  Add. Sense: Not ready to ready change, medium may have changed
 35 Dec 21 22:15:47 box kernel: [469304.207358] sd 6:0:0:0: [sdd] tag#0 CDB: Read(10) 28 00 08 c5 78 d0 00 00 08 00
 36 Dec 21 22:15:47 box kernel: [469304.207363] print_req_error: I/O error, dev sdd, sector 147159248
 37 Dec 21 22:15:47 box kernel: [469304.207373] Buffer I/O error on dev sdd1, logical block 18390810, async page read
[/FONT]
```
Lots  of errors and stuff. But it should be a good card... has been working  fine before the upgrade. Is this a bug worth reporting?

---

### Post by wildmanne39 on 2018-12-22
Hello partofthething, please start your own thread instead of posting in someone else's so you both can get the individual help you deserve.

Thanks!

---

