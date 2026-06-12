---
title: "problem connecting smartphone to 12.04 64bit"
date: 2014-03-21
forum: General Help
---

### Post by DrScum on 2014-03-21
I want to connect a smartphone (htc wildfire s) to my laptop which runs 12.04 64bit version. When I connect the usb cable a message "wired connection 2 connection established" pops up, but the phone doesn't become available in nautilus or anywhere else.

When I connect it to my desktop, which runs 12.04 32bit the behaviour is normal, i.e. the phone becomes available in nautilus.

How can I diagnose and fix this problem?

---

### Post by kurja on 2014-03-21
Check if your phone has different USB modes, like "PTP" or "Mass Storage" or "Debugging". What are you trying to do when you connect your phone to your computer, transfer files, something else..? For that you'd want the mass storage mode.

---

### Post by DrScum on 2014-03-21
There are different USB modes and I have set it to mass storage. As I said, it works fine with my desktop, which also has Ubuntu 12.04 but the 32bit version. The  differences between my laptop and the desktop is definitely the 32 vs 64 bit version and there might be differences in settings and software which are relevant for the problem. What I don't know is how to diagnose and eventually solve the problem.

---

### Post by kurja on 2014-03-21
Hm that's weird, I haven't had any problems with 32b 12.04... my mobile devices are a little dated compared to yours though. Maybe you could try the MTP usb mode? Afaik it shouldn't show up in wired connections anyway - _unless_ the system is trying to use the device as a modem. Have you used it that way before on your laptop, check your connections when the phone is plugged? Maybe the issue lies there. If not, hopefully someone more knowledgeable steps in...

---

### Post by slooksterpsv on 2014-03-21
kurja has the right idea, you may want to see if you have tethering enabled. If you go to Settings -> Wireless & Networks - do you have Internet sharing enabled?

---

### Post by DrScum on 2014-03-22
Thans a lot, the hint with tethering and Internet sharing was the right one. Turning off all Internet sharing options on the phone does the trick.

---

