---
title: "[SOLVED] Disk check at boot fails"
date: 2008-06-20
forum: General Help
---

### Post by Rohn on 2008-06-20
This has been going on for a while now, and I still have not been able to fix it.  The disk check at boot is forced because my disk has been mounted too many times without a check.  Every time though, it gets to 59.3 percent, hangs, and then reboots.  If left alone, it would be an endless loop of reboots.  I have to hit escape to skip the check in order to boot my system.  I have tried booting on a live disk so that I could use fsck on the unmounted disk through terminal, but this also hangs and reboots.  Any advice on what to try next?  Any help would be greatly appriciated. :)

---

### Post by cariboo on 2008-06-20
Sounds like you've got a corrupted hard drive. Go to your hard drive's manufacturers web site and download the diagnostic tools and run it. Most of the tools will fix minor corruption problems.

Jim

---

### Post by Rohn on 2008-06-20
I'll try that, hopefully it will work.  If not, I believe the drive is still under warranty, so as much as I don't want to, I could always replace it.

---

### Post by Rohn on 2008-06-20
It worked! :) I downloaded the diagnostic iso, burned it to a cd, and booted it.  The drive did indeed have errors, but a scan was able to repair them.  The disk check now works like a charm!  Thanks for your help! :)

---

