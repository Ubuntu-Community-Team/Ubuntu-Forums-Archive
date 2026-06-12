---
title: "Slow File transfers"
date: 2008-05-22
forum: General Help
---

### Post by crash91 on 2008-05-22
This happens when I try to copy a large 500-700MB file to an external USB device or to my SD card in the slot.
I have a Sansa e250 and the same happens regardless of whether the MicroSD is in the player or the slot, I get a constantly decreasing file transfer rate. The transfer will start off at around 8MB/s then drop to 4,3,2,1 and then keeps slowly dropping.
This happens while using my USB drive as well but to a lesser extent. This is not a hardware problem because I can get upto 8-10MB/s on my SD and ~15MB/s on my USB in Windows (In Ubuntu the USB is only around 2-3MB/s).

Please help!
Crash

---

### Post by Sam Lars on 2008-05-22
When it starts to slow down, do you have a lot of disk activity still or does it drop off with the rate?

---

### Post by crash91 on 2008-05-23
It drops off with the rate.

---

### Post by Roostey on 2008-05-25
I've had this problem since the 8.04 beta.  Try to copy a large file, it starts off at the correct speed for the device, then slows down to sub 1 mb/s speeds.  I've found that the best way to live with this is to copy files one at a time, and unmount the device between each one.

Here's the bug report

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197762]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197762")

---

