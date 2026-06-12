---
title: "Startup sript for touchpad"
date: 2008-05-21
forum: General Help
---

### Post by FokkerCharlie on 2008-05-21
Hi All

I wonder if this is possible?

I have a new Acer Aspire 5920 that is working splendidly with Ubuntu.  It is equipped with a Synaptics touchpad, which I got working fully with help from this thread:

[http://ubuntuforums.org/showpost.php?p=3397052&postcount=4](http://ubuntuforums.org/showpost.php?p=3397052&postcount=4)

However, I also have a Logitech Cordless Optical Trackman, this too works well with Ubuntu.  Unfortunately, the acersynaptics.rules file that is described in the thread needs to be changed, depending on whether the Trackman is connected or not.  So, I have two of these files, one for when I am at home using the Trackman, and one for the road.

The question is:  is it possible to write a script to run at startup to detect whether the Trackman is connected, and depending on this, copy the relevant version of the acersynaptics.rules to /etc/udev ?

Here's the relevant part of cat /proc/bus/input/devices:

```
I: Bus=0003 Vendor=046d Product=c508 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=20017
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10
B: LED=ff00
```


Would be great if this was possible!

Thanks in advance
Charlie

---

