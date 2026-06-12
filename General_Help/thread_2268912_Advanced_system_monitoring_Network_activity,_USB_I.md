---
title: "Advanced system monitoring? Network activity, USB I/O, etc."
date: 2015-03-12
forum: General Help
---

### Post by tessk2 on 2015-03-12
I am currently using htop and various Panel widgets in Xubuntu 14.04 to monitor CPU and RAM activity. However, it would be nice to have more diagnostics than just those, so that when I encounter lag or slow downs on my machine that are not related to those, I can easily figure out what might be causing it. Is there an easy way to monitor this?

 In particular I am looking to monitor network activity, along with I/O on all connected devices. I am currently running off of a USB 2 flash drive until my new SSD arrives, and as a general test drive that I can run on various machines, so it would be very handy if I had a way to tell when USB throughput is throttling system performance. Is there any way to tell when system I/O channels are saturated, or when connected devices are saturated and operating at peak I/O performance regardless of further available headroom on the motherboard side? This would help to keep me from mistakenly attributing system lag to the computer when in reality the connected devices could be the ones holding everything up.

Thanks!

---

### Post by TheFu on 2015-03-12
Easy? Depends.
Cacti, SysUsage are the ways we do it for servers.
I hear lots of home users like conky.

---

