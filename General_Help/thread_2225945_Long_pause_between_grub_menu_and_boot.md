---
title: "Long pause between grub menu and boot"
date: 2014-05-24
forum: General Help
---

### Post by RecNes on 2014-05-24
[COLOR=#333333][FONT=UbuntuRegular]Fresh installed ubuntu 14.04 pauses on boot time between after pressing enter on grub menu (it disappears and cursor blinks on blank screen) and boot.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I did fresh install again but nothing changed.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]What should I check for this long (~60Sec.) pause? Or what can be caused like this type of pause?

[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Some info:[/FONT][/COLOR]

[LIST]
[*]Problem is alive on Desktop machine.
[*]There is no wireless device attached to machine.
[/LIST]

Additions:

BootChart:

[[IMG]http://s21.postimg.org/mx7rf4d5f/intel_desktop_trusty_20140524_1.jpg[/IMG]]("http://postimg.org/image/mx7rf4d5f/")


header file:

[http://pastebin.com/raw.php?i=uSPp02HV](http://pastebin.com/raw.php?i=uSPp02HV)

---

### Post by oldfred on 2014-05-24
If 30 sec and a hard drive that is not long. If an SSD it is long as my old slow SSD is about 10 sec, but same system with older hard drive is about 40 sec.

You can look at what processes take time. I review outright errrors, warnings, and repeated trys and either success or failure. Any entry with a long time from previous entry requires review.

You may have log file viewer or just open dmesg with a text editor. That is the log of the boot process and is the same as you see scroll by on boot, if you remove quiet splash on grub menu linux line entry.

 sudo nano /var/log/dmesg 
or
gksudo gedit /var/log/dmesg

Mounting file systems is the slowest on my system:

```
[    3.696238] usbhid: USB HID core driver
[    4.992233] EXT4-fs (sdd3): mounted filesystem with ordered data mode. Opts:$
[    7.689992] Adding 3076412k swap on /dev/sdc11.  Priority:-1 extents:1 acros$

```

---

### Post by RecNes on 2014-05-24
It does not releated with Disk type. First I installed HDD, after I faced with this problem I switched to SSD but nothing changed.

I append bootgraph image and short info about computer.

---

### Post by stalkingwolf on 2014-05-24
my experience across several OS's is that ram can make a difference.  on a sysstem with 1 gb of ram boot is much slower than when is has 3 gb.

---

### Post by RecNes on 2014-05-24
> **stalkingwolf said:**
> my experience across several OS's is that ram can make a difference.  on a sysstem with 1 gb of ram boot is much slower than when is has 3 gb.

It is not related with RAM either. 8GB of RAM installed, and there is no crush while running any software.

---

### Post by oldfred on 2014-05-24
Do not know how to read boot chart, plus any that is posted here is too small to read.

Did you look at log file, to see if you have long delays between time stamps?

---

### Post by RecNes on 2014-05-24
You can reach bigger image if you click to chart twice :)

Is this the what we are looking for?

[    6.134504] usb 2-5.3: Product: Microsoft\xffffffc2\xffffffae\xffffffae SideWinder\xffffffe2\xffffff84\xffffffa2\xffffff84\xffffffa2 X3 Mouse
[    6.134505] usb 2-5.3: Manufacturer: Microsoft
[    6.272251] usb 2-5.4: new low-speed USB device number 6 using ehci-pci
[    6.368627] usb 2-5.4: New USB device found, idVendor=04f3, idProduct=0103
[    6.368630] usb 2-5.4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    9.512030] ata1: link is slow to respond, please be patient (ready=0)
[   13.936030] ata1: SRST failed (errno=-16)
[   19.452030] ata1: link is slow to respond, please be patient (ready=0)
[   23.988030] ata1: SRST failed (errno=-16)
[   29.504030] ata1: link is slow to respond, please be patient (ready=0)
[   48.080034] random: nonblocking pool is initialized
[   59.016030] ata1: SRST failed (errno=-16)
[   59.016034] ata1: limiting SATA link speed to 1.5 Gbps
[   64.028030] ata1: SRST failed (errno=-16)
[   64.038799] ata1: reset failed, giving up
[   64.204492] Freeing unused kernel memory: 1332K (ffffffff81d1e000 - ffffffff81e6b000)
[   64.204494] Write protecting the kernel read-only data: 12288k
[   64.206788] Freeing unused kernel memory: 844K (ffff88000172d000 - ffff880001800000)
[   64.208554] Freeing unused kernel memory: 708K (ffff880001b4f000 - ffff880001c00000)
[   64.230370] systemd-udevd[140]: starting version 204
[   64.251363] pps_core: LinuxPPS API ver. 1 registered

---

### Post by oldfred on 2014-05-24
It is this:

ata1: SRST failed (errno=-16)

But do not know issue.

What computer is this? Is SRST from Windows?

---

### Post by RecNes on 2014-05-25
Problem solved by changing SATA Compitability mode from AHCI to IDE.

---

