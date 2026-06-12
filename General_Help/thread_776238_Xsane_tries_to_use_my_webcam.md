---
title: "Xsane tries to use my webcam"
date: 2008-04-30
forum: General Help
---

### Post by Andre-D on 2008-04-30
I have a webcam on the laptop.
When I conect a LIDE 600F scanner, Xsane starts, and so does my webcam on laptop's monitor.

-how can I choose another device ? (scanner?)


:~$ scanimage -L   
returns:
device `v4l:/dev/video0' is a Noname Logitech Orbicam virtual device

:~$ sane-find-scanner

found USB scanner (vendor=0x04a9 [Canon], product=0x2224 [CanoScan]) at libusb:005:006
found USB scanner (vendor=0x046d, product=0x0896) at libusb:005:005

I also added this line to  /etc/sane.d/epkowa.conf

usb 0x04a9 0x2224



I also tried to add this line to

---

