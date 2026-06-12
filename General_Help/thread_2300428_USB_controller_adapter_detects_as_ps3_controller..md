---
title: "USB controller adapter detects as ps3 controller."
date: 2015-10-25
forum: General Help
---

### Post by ulao2 on 2015-10-25
This is going to be hard to catch someone that knows the answer but I want to try. I have a HID based usb adapter for controllers. During the enumeration of the ps3 consol it sends a feature report 0301 (little endian 0103). For some reason unknown to me ubuntu also does this. No other OS that I have found does. Normal a computer has no use for this feature report, nor is it even defined. This is during the usb function set up. I'd like to find out why Ubuntu is doing this.

---

