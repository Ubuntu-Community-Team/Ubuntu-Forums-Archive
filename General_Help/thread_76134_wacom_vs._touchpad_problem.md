---
title: "wacom vs. touchpad problem"
date: 2005-10-14
forum: General Help
---

### Post by bonvenon on 2005-10-14
I'm trying to get the pressure sensitivity to work with my wacom graphire2 tablet. The problem is that I simply can't find a way to have both my wacom tablet up and running at the same time as my synaptics touchpad. 
To get the wacom tablet to work properly you can't have any input device using /dev/input/mice, but when I change my usb mouse to use /dev/input/mouse2 instead my synaptics touchpad stops working!
I've tried numerous different combinations of devices in the xorg.conf with no luck. 
I don't understand why the touchpad is saffected by the configuration of the mouse. 
Any ideas?

---

