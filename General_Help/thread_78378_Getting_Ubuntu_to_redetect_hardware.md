---
title: "Getting Ubuntu to redetect hardware"
date: 2005-10-18
forum: General Help
---

### Post by BIGtrouble77 on 2005-10-18
I just noticed something, I had my laptop's wifi card turned off when I installed breezy so drivers were never installed.  

How can I force Ubuntu to do a new hardware check and install those drivers automatically?

---

### Post by nocturn on 2005-10-18
[QUOTE=BIGtrouble77]I just noticed something, I had my laptop's wifi card turned off when I installed breezy so drivers were never installed.  

How can I force Ubuntu to do a new hardware check and install those drivers automatically?[/QUOTE]

If your card is supported natively, it should still work.  
My guess is that it needs Ndiswrapper to work...

---

### Post by az on 2005-10-18
Turn it on and go into the networking tool.  If it shows you a wireless connectino to configure, configure it and you are done.

If not, you need to install a driver for it.  In this case, all windows wireless drivers use the same protocol (NDIS) and there is a tool which can use those drivers in linux.  

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

---

### Post by BIGtrouble77 on 2005-10-18
Thanks guys.  No, the card does not come up with the networking devices.  I know it's supported becauseI had it working fine with hoary.  

I'm gonna give that a shot and see how it goes.

---

### Post by BIGtrouble77 on 2005-10-18
that worked beautifully.  Are there any other drivers that can be installed this way?  Like flash card readers or webcams? (the only two things left I can't get working)

---

### Post by lithorus on 2005-10-18
Ndiswrapper is only for network devices (and mostly for wireless).

---

### Post by az on 2005-10-18
[QUOTE=BIGtrouble77]that worked beautifully.  Are there any other drivers that can be installed this way?  Like flash card readers or webcams? (the only two things left I can't get working)[/QUOTE]

Many webcams already have linux drivers.  Some of those drivers are already in the Ubuntu kernel.  The flash card reader should work just like any other usb hard disk.

Open the log viewing tool and plug in each device.  What messages appear in /var/log/messages after you plug them in?

---

### Post by BIGtrouble77 on 2005-10-18
[QUOTE=azz]Many webcams already have linux drivers.  Some of those drivers are already in the Ubuntu kernel.  The flash card reader should work just like any other usb hard disk.

Open the log viewing tool and plug in each device.  What messages appear in /var/log/messages after you plug them in?[/QUOTE]
Both the webcam and card reader are integrated into my laptop.
The webcam is detected and shows up in the device manager, but it crashes my system when I try to access it through gnome meeting.  The card reader is an unknown device in the device manager- it's a winbond device.  

This is the 4th time i'm writing this message, lol.  Stupid gnome meeting keeps crashin my computer.  I should learn to do things one at a time...](*,)

---

### Post by sabitha on 2005-12-13
haved you try with the permision on your device i think.
try change permision of your cam device with:
code:
sudo chmod 666 dev/video0

i hope thats help ;)

---

