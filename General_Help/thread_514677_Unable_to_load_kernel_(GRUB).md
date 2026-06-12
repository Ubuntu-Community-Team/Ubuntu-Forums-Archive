---
title: "Unable to load kernel (GRUB)"
date: 2007-08-01
forum: General Help
---

### Post by TheFoe92 on 2007-08-01
Well, I was playing around with Start-up Manager. I'm actually not sure what causes this problem. Here it is: While trying to load the most recent kernel from the GRUB menu, the screen goes black, and the Caps Lock light blinks. I try to go to recovery mode and it freezes at some point (I will reboot into recovery mode, right down where it stops, and post it here in my next post). It was working fine before; all I changed was the screen resolution from 1280x1024 to 1024x768. Before, I did try changing the screen resolution to 1600x1200 (don't ask why; I was just experimenting, trying to see how different resolutions would look), but it booted perfectly fine. It was after changing it to 1024x768 that it stopped working. I don't get an error message, it just freezes with a black screen and the caps lock light blinks. I have included screenshots of my StartUp-Manger options. The kernel I am trying to load is 2.6.20-16-generic. Right now, I was forced to boot into 2.6.20-15-generic to be able to run anything. Did I screw anything up? Is there a setting I missed or messed with? Should I reinstall Ubuntu Feisty? Any suggestions would be greatly appreciated. Thank you in advance!

---

### Post by dragonwings on 2007-08-01
boot live cd

in terminal type

sudo su

grub

find /boot/grub/stage1       (to findhard drive eg hda0,0)

root (your harddrive name as eg above goes here with brakets see eg blow

eg         root (hda0,0)

setup (hd0,0)

quit

restart pc

note where ever i put hdo,0 you will have to replace that with yours

---

### Post by TheFoe92 on 2007-08-01
Here is the output from recovery mode:

```

[    0.855726] RAMDISK : ran out of compressed data
[    0.855770] invalid compressed format (err=1)
[    0.856097] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
[    0.856141]

```

Again, I have no idea what I did. It was working perfectly before I changed the screen resolution to 1024x768. This looks somewhat like a Windows STOP error. Just in case you will need it, my system specs are:
[B]
Gateway 7330GZ laptop[/B]
_Processor_

Processor
    * Intel Mobile Pentium 4 532 / 3.06 GHz

Data bus speed
    * 533 MHz

Processor features
    * Hyper-Threading Technology, Enhanced SpeedStep technology

Chipset type
    * Intel 852GME

_Cache Memory_

Type
    * L2 cache

Cache size
    * 1 MB

_RAM_

Installed Size
    * 512 MB / 1.5 GB(max)

Technology
    * DDR SDRAM

RAM form factor
    * SO DIMM 200-pin

_Storage Controller_

Storage controller type
    * IDE

_Display_

Display Type
    * 15.4 in TFT active matrix

Max Resolution
    * 1280 x 800 ( WXGA)

Display (Projector) / Widescreen Display
    * Yes

Color support
    * 24-bit (16.7 million colors)

Features
    * UltraBrite technology
[U]
Video[/U]

Graphics Processor / Vendor
    * Intel 852GME

Video Memory
    * Dynamic Video Memory Technology 2.0
------------------------------------------------------------
If you need all the specs, head over to [this site]("http://reviews.cnet.com/laptops/gateway-7330gz-mobile-pentium/4507-3121_7-31477979.html?tag=nav").

---

### Post by TheFoe92 on 2007-08-01
Thank you for the reply dragonwings! I followed dragonwings' advice, but nothing changed. The numbers inside the brackets of the error message do, though. I tried restarting four more times after trying dragonwings' advice. This (first time I tried booting): 
```
[    0.855726] RAMDISK : ran out of compressed data
[    0.855770] invalid compressed format (err=1)
[    0.856097] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
[    0.856141]
```

Changed to this:
```
[    0.751539] RAMDISK : ran out of compressed data
[    0.751582] invalid compressed format (err=1)
[    0.751906] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
[    0.751949]
```

This,
```
[    0.843742] RAMDISK : ran out of compressed data
[    0.843785] invalid compressed format (err=1)
[    0.844113] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
[    0.844157]
```

This, 
```
[    0.948895] RAMDISK : ran out of compressed data
[    0.948938] invalid compressed format (err=1)
[    0.949260] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
[    0.949303]
```

And this, 
```
[    0.847814] RAMDISK : ran out of compressed data
[    0.847859] invalid compressed format (err=1)
[    0.848185] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
[    0.848229]
```

Is it a hardware problem? Maybe a kernel bug? I don't compress anything, so I don't know why it says 'invalid compressed format' and 'ran out of compressed data'. I have to partitions, if it is of any use. One is running Windows XP SP2 and the other is obviously running Ubunt Feisty 7.04. GRUB version is 1.5.

---

### Post by TheFoe92 on 2007-08-01
> **dragonwings said:**
> boot live cd

I did everything, but I didn't use the Live CD. Do I actually need to? I'll try it but I'm not sure if it will make a difference since Live CDs run just off the CD.

---

### Post by TheFoe92 on 2007-08-07
No one here knows how to fix this?

---

