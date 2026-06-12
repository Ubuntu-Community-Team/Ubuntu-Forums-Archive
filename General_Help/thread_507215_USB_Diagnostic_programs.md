---
title: "USB Diagnostic programs"
date: 2007-07-22
forum: General Help
---

### Post by Howard Kaikow on 2007-07-22
Are there Linux programs for diagnosing USB drives?

---

### Post by geraldm on 2007-07-22
Possibly [http://linux-diag.sourceforge.net](http://linux-diag.sourceforge.net) in package sysdiag

usbsnoopy is a program that exposes the traffic on the usb bus for a windows system.
That can be helpful, but not exactly what you are seeking.

Gerald

---

### Post by Howard Kaikow on 2007-07-23
> **geraldm said:**
> Possibly [http://linux-diag.sourceforge.net](http://linux-diag.sourceforge.net) in package sysdiag

usbsnoopy is a program that exposes the traffic on the usb bus for a windows system.
That can be helpful, but not exactly what you are seeking.

Gerald

Thanx.

What I am seeking might be clarifed by the following:

My sister has a USB drive that was causing errors in Windows.
I had her reformat the  drive, then run a full scan of the sectors.

Alas, the scan only took a minute or so, which seems short for an 80GB drive.

We tried Seatools for Windows, but that crapped out with an unhandled exception ("Object variable or With block variiable not set", clearly a programming error). I'll report that to Seagate later today.

So, I figured that I'd introduce her to Linux, and see if I could find a Linux prog that will verify all the sectors on a USB drive.

---

