---
title: "Booting from SD"
date: 2012-12-26
forum: General Help
---

### Post by Relinies on 2012-12-26
On an Acer Aspire One, Ubuntu 12.04 currently installed, BIOS is Insydeh2o.
I have an SD card prepared with all needed files and it is flagged as bootable, but when I open the boot menu I can't see the SD card anywhere to boot from. I've already tried redoing the setup on the SD card, so I know that isn't the problem. What am I doing wrong, and how can I fix it so I can boot from my SD card? I've never even seen the device listed anywhere on my BIOS (works when Ubuntu starts up, naturally), even before I started trying to boot from it.

It might help to mention I'm trying to get [http://chromeos.hexxeh.net](http://chromeos.hexxeh.net) 
It was set up via the windows method on my main computer because I couldn't figure out the Linux instructions (Permission Denied).

---

### Post by chadk5utc on 2012-12-27
go into the BIOS and make sure USB is set to boot or change the boot order and make it higher so it will boot first then save and exit this will restart the PC and should boot from the SD card

---

### Post by efflandt on 2012-12-27
To use **dd** in Ubuntu you have to **sudo dd**

Is the SD card in a usb device like /dev/sdx where x is some letter?  If it is in a card slot in a laptop, it might be /dev/mmcblk0 which typically you cannot boot from.  But in that case you should still be able to boot the SD in a USB card reader.

My tablet PC can boot from its SD slot, but that is internally connected with USB.  The only computer that I know can boot SD from /dev/mmcblk0 is a Raspberry Pi (credit card size computer on a board) and SD is the only thing it can initially boot from (no hard drive).

PS: I tried the most recent ChromeOS USB image from that site on a USB stick which creates 3 partitions in a gpt partition.  But when I booted that on my tablet PC it just flashes the screen and then in about 5 seconds switches back to text with: **Kernel panic - not syncing: No init found**...

The VirtualBox version does work in VirtualBox 4.2.6, but I had to select "Intel PRO/1000  MT Desktop(NAT)" instead of default PCnet network device, and had to add a filter for my USB mouse.

---

### Post by Relinies on 2012-12-27
> **chadk5utc said:**
> go into the BIOS and make sure USB is set to boot or change the boot order and make it higher so it will boot first then save and exit this will restart the PC and should boot from the SD card

No can do. Card reader not listed in BIOS menu.

> **efflandt said:**
> To use **dd** in Ubuntu you have to **sudo dd**

Is the SD card in a usb device like /dev/sdx where x is some letter?  If it is in a card slot in a laptop, it might be /dev/mmcblk0 which typically you cannot boot from.  But in that case you should still be able to boot the SD in a USB card reader.

My tablet PC can boot from its SD slot, but that is internally connected with USB.  The only computer that I know can boot SD from /dev/mmcblk0 is a Raspberry Pi (credit card size computer on a board) and SD is the only thing it can initially boot from (no hard drive).

PS: I tried the most recent ChromeOS USB image from that site on a USB stick which creates 3 partitions in a gpt partition.  But when I booted that on my tablet PC it just flashes the screen and then in about 5 seconds switches back to text with: **Kernel panic - not syncing: No init found**...

The VirtualBox version does work in VirtualBox 4.2.6, but I had to select "Intel PRO/1000  MT Desktop(NAT)" instead of default PCnet network device, and had to add a filter for my USB mouse.
Don't have a USB card reader, and (see answer to above quote), so I'm going to have to use a USB stick instead of an SD card in this case?

---

