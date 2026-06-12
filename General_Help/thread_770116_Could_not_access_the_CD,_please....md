---
title: "Could not access the CD, please..."
date: 2008-04-27
forum: General Help
---

### Post by starbase1 on 2008-04-27
I have repeatedly tried installing Ubuntu HH 64 bit with Wubi, and I keep getting the error message "Could not access the CD, please make sure other application are not using it and try again".

This happens about 40% of the way through a progress bar with the header "Creating image..."

I found the log file, Wubi-8.04-beta-rev495.log, (Why is this a beta? I downloaded the final of HH?)

At the end of the log are some messages that look relevant:

Asking user to retry CD2ISO
CD2ISO D:\ubuntu\install\installation.iso


Now the thing I notice here is that the D: drive is not the correct one. The disk is in my F: drive, and d: is a partition of my first hard disk.

Any clues? 

I tried the install to a partition for Ubuntu HH64, but it kicked over my GRUB setup, and I had to fix from a windows recovery disk..

Nick

---

### Post by ago on 2008-04-27
[https://wiki.ubuntu.com/WubiGuide#head-100b63cc0192113d19fa119a9d472412e42ac1a8](https://wiki.ubuntu.com/WubiGuide#head-100b63cc0192113d19fa119a9d472412e42ac1a8)

---

### Post by starbase1 on 2008-04-27
Thanks for the pointer!

---

