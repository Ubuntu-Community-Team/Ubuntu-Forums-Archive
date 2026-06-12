---
title: "Driver help please?"
date: 2015-04-05
forum: General Help
---

### Post by krs360 on 2015-04-05
Hi all,

Been away for sometime but I've recently purchased an odroid c1 and in the full ubuntu image I get kernel panics but my usb --> ethernet adapter driver works. The minimal image (which is what I want to use) doesn't seem to have the drivers for my usb --> ethernet adapater. I am hoping that this isn't the cause of the panics but I really want to be able to use the minimal image as it's to be a router/gateway anyway and doesn't need all the extras.

I boot the image to only have eth0, no eth1 or usbnet0 I've included this image - [http://i.imgur.com/0nNcU6o.jpg](http://i.imgur.com/0nNcU6o.jpg) - the image is too big to [img], sorry!

Any help would be greatly appreciated.

---

### Post by ian-weisser on 2015-04-05
The last line of that picture seems to show your usb-ethernet dongle properly detected, a driver assigned, and interface usbnet0 assigned.

What is the output of the command 'ifconfig -a' ?

---

