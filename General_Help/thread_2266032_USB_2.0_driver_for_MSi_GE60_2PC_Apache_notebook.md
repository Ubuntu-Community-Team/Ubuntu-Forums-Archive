---
title: "USB 2.0 driver for MSi GE60 2PC Apache notebook"
date: 2015-02-19
forum: General Help
---

### Post by a-richardson92 on 2015-02-19
I am trying to find a USB 2.0 driver for MSi GE60 2PC Apache notebook as the one I get with Ubuntu 14.10 malfunctions causing key presses to be missed and the mouse to behave erratically. I have tried looking for additional drivers in software and updates but it cannot find any.

---

### Post by efflandt on 2015-02-20
Have you tried 14.04.1? I have a little over a year old MSI GE60 2OE. It worked fine with 13.10 and I recently installed 64-bit 14.04.1 on an separate internal mSATA SSD which works fine. Although, I often use a separate Logitech wireless mouse. If there were any keyboard issues I likely would have noticed it playing TF2 in Steam. Although, I specifically bought while I could still get Win7, so while it is capable of UEFI, it is using legacy BIOS and msdos partitions. Not even sure if the built-in keyboard uses USB, at least nothing shows up for it in lsusb, or are you using some type of external USB keyboard.

One of the 2 times I noticed keyboard down or up events not being properly registered in Linux (missing or repeating keys) was when some USB 1.0 keyboards were used with the USB 2.0 on a Raspberry Pi (credit card size ARM computer running a special Debian version), if not forced to use USB 1.0. But that was some time ago and they may have fixed that by now. The only time I ever noticed that in Ubuntu was that for a long time minecraft was using an old lwjgl version that occasionally resulted in repeating keys, but that was resolved by updating the 2.4.2 version of lwjgl that came with minecraft to 2.6 or newer. Current minecraft has a newer lwjgl version.

---

