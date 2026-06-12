---
title: "How to define the order that USB webcams are initiated??"
date: 2013-04-29
forum: General Help
---

### Post by dazz100 on 2013-04-29
Hi
I  am developing a webcam server with two Logitech webcams connected.
The No.1 webcam is to be mounted 15m from the server so I have a USB-Ethernet-USB adapter.
This is the webcam I want to set at 960x720 resolution.

The No.2 webcam is connected straight into the server.  This only requires 800x600 resolution.

When the webcams are initialized after a bootup, the first webcam takes enough bandwidth to show 1024x960 resolution regardless of what resolution is selected.
The 2nd webcam is left with enough bandwidth for 800x600 resolution.

The problem I have is that the No.2 webcam is always the first initialized so it takes the bigger chuck of bandwith.  The No.1 webcam is left with the remaining bandwidth.  I need the No.1 webcam to initialize first to deliver the higher bandwidth.

Swapping the connectors at the USB PCI card made no difference.  Swapping the cameras made no difference.  It seems that the USB-Ethernet-USB adapter and the attached webcam is always initiated after the direct connected webcam.
I suspect that the USB-Ethernet-USB is not fully transparent and is always a lower priority for initialization.

So my question is can I define the order that connected USB devices are initialized??  In this case I want the No.1 webcam to be initialized first.

---

### Post by dazz100 on 2013-04-30
Hi

I have found the seemingly obscure command [ usb_reset_device](http://manpages.ubuntu.com/manpages/dapper/man9/usb_reset_device.9.html).

I am thinking that if I can suspend (unbind) both Logitech C500 webcams, then bind in the order I want them to restart, that might work.

Failing that maybe, a unbind, bind, usb_reset_device sequence of commands in the order that I want them to be restarted will achieve my aim.  

The man page warns that the driver needs to expect a device reset.  That is the part I haven't yet figured out before I try and test this.

---

### Post by dazz100 on 2013-05-13
Hi
One of my webcams was connected via a USB1.1-ethernet-USB1.1 extender. 
I have found that the webcam without the extender is always initiated first. In other words, the webcam with the wider bandwidth USB2.0 interface gets initiated first.
The webcam with the lower bandwidth USB1.1 connection gets initiated last.

With the USB extender taken out of the system, I am still unable to define which camera is first initiated. The kernel seems to make a consistent choice.

---

