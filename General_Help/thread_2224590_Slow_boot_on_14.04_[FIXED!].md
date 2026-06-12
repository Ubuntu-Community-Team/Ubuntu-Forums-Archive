---
title: "Slow boot on 14.04 [FIXED!]"
date: 2014-05-16
forum: General Help
---

### Post by mystronyx on 2014-05-16
UPDATE: I have fixed this problem. I followed the first step in the link below, downgrading the kernel with the 3 files. It now boots like it did in 13.10 in less than 10 seconds.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1308264/comments/9](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1308264/comments/9)

--------------------------------------------------------------------------------------------------

Hello,

I have a chromebook that had 13.10 installed. It booted in a matter of a couple seconds. I just now formatted and installed 14.04, and the boot time is upwards of a minute. I installed bootchart and posted the image. Anyone have an idea of what's causing it to hang for so long?

I also noticed a large jump in dmesg. Here's where the jump in time occurs:

[    1.822904] usb 2-3: New USB device found, idVendor=1bcf, idProduct=2c67
[    1.822910] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.822913] usb 2-3: Product: HD WebCam
[    1.822915] usb 2-3: Manufacturer: NC.21411.0244020DFD9LM0001
[    2.004426] usb 2-4: new full-speed USB device number 4 using xhci_hcd
[    2.022118] usb 2-4: string descriptor 0 malformed (err = -61), defaulting to 0x0409
[    2.024014] usb 2-4: New USB device found, idVendor=0489, idProduct=e056
[    2.024017] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.608410] Switched to clocksource tsc
[   53.812067] regulator-dummy: disabling
[   53.812126]   Magic number: 14:202:159
[   53.812171] acpi device:26: hash matches
[   53.812238] rtc_cmos 00:08: setting system clock to 2014-05-17 03:11:39 UTC (1400296299)
[   53.812464] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   53.812466] EDD information not available.
[   53.812507] PM: Hibernation image not present or could not be loaded.
[   53.813685] Freeing unused kernel memory: 1332K (ffffffff81d1e000 - ffffffff81e6b000)
[   53.813687] Write protecting the kernel read-only data: 12288k
[   53.816941] Freeing unused kernel memory: 844K (ffff88000172d000 - ffff880001800000)
[   53.819408] Freeing unused kernel memory: 708K (ffff880001b4f000 - ffff880001c00000)
[   53.849438] systemd-udevd[116]: starting version 204
[   53.891534] hidraw: raw HID events driver (C) Jiri Kosina



[IMG]http://i.imgur.com/4jqPaoh.png[/IMG]

---

