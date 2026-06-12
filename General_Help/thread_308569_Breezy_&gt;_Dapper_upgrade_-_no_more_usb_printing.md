---
title: "Breezy &gt; Dapper upgrade - no more usb printing"
date: 2006-11-28
forum: General Help
---

### Post by kmoz on 2006-11-28
I recently upgraded from Breezy to Dapper.  The initial upgrade went okay, until the system tried to reboot the new 2.6.15 kernel - black screen and nothing else.  System boots fine from the old 2.6.12 kernel.  

Perhaps related to this, CUPS printing is now slightly broken.  My parallel printer works fine, but my usb printer (which was working under breezy) now gives status as:
```
Printer not connected; will retry in 30 seconds..."
```

Here is the printer settings:
```
Description: Epson Stylus Photo 1280
Location: **
Make and Model: EPSON Stylus Photo 1280 - CUPS+Gutenprint v5.0.0-rc2
Printer State: processing, accepting jobs, published.
Device URI: usb:/dev/usb/lp0
```

I've tried setting up a new printer, but there isn't even a choice for USB Printer.  lsusb gives this:
```
Bus 001 Device 002: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 001 Device 001: ID 0000:0000
```
How can I get this printer working again?

Also, has anyone else experienced the inability to boot the 2.6.15 kernel after a breezy to dapper upgrade?

***UPDATE*** I am now able to boot 2.6.15 in recovery mode.  Everything boots up fine, and CUPS allows me to select my USB printer.  Any suggestions on where to start looking for what in regular mode is preventing bootup, while recovery mode works fine?

---

