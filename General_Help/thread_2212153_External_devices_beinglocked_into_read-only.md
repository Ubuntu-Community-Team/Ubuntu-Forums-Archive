---
title: "External devices beinglocked into read-only"
date: 2014-03-19
forum: General Help
---

### Post by hopkinsjeni on 2014-03-19
In the last week or so every device (SD Card, USB Stick) I have plugged into my ubuntu has ended with the contents becoming read-only. I am honestly not doing anything to the files just opening them, editing and doing 'save as' when I am finished and all my personal files hae been converted to read-only some I am not even able to access at all. This is a major issue, I have bascially lost all my files, as I don't keep things saved on my PC only on USB's or External Devices. Please help!

---

### Post by ajgreeny on 2014-03-19
Plug in one of those USB devices that is causing the problem, find its mountpoint by looking in /media in nautilus, and then run command ```
ls -l /media/*username/mountpoint*
``` Change the words *username* and *mountpoint* to fit your own system.

---

