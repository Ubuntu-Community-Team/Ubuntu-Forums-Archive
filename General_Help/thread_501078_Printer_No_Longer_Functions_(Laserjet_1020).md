---
title: "Printer No Longer Functions (Laserjet 1020)"
date: 2007-07-14
forum: General Help
---

### Post by jakefromlondon on 2007-07-14
Hello,

I have a LaserJet 1020 running directly connected under Ubuntu Feisty.  It worked perfectly after initial configuration and hasn't given me any trouble until now.  Currently, when a document is printed to it, the document goes into the queue and then vanishes after a short while.  The printer is detected just find, verified by a simple reinstall.

It may be unrelated, but I recently installed and removed cups-pdf (it just didn't have the flexibility I was looking for).

Running dmesg | grep "usb" yields the following foreboding message when printing is attempted:

usb 2-4: usbfs: USBDEVFS_CONTROL failed cmd hpiod rqt 161 rq 1 len 1 ret -110

Any assistance would be greatly appreciated.

---

### Post by scrooge_74 on 2007-07-14
not sure if this would help but on your browser you can type localhost:631/  and will give you access to CUPS and you may get a better idea of what is going on

---

### Post by jakefromlondon on 2007-07-19
Logging directly into CUPS doesn't really yield any new information.  The jobs go into the queue and everything pretends to work.  As far as the CUPS error log is concerned,  the jobs all go off without a hitch.

---

