---
title: "Need to compile module...but how?"
date: 2006-10-17
forum: General Help
---

### Post by airforceixi on 2006-10-17
It seems that there is a daunting problem with EV-DO PCMCIA cards: they don't work as fast in linux as they do in Windows. I found out what needs to be done in order to fix this, but I need to do something that I have no clue on what to do. Since the card is basically a USB Controller with a USB modem on it, I use the usbserial driver to connect to the device. It works great, but my speeds are limited to 150 kbps down (when I get upwards of 700-800 in Windows). I downloaded my kernel source (linux-source-2.6.15-27) and found the file, usb-serial.c, and made the proper modifications to allow for a maxSize parameter for the buffer. Now I'm stuck because I have absolutely no clue on how to compile and then install this module. Can I just compile this single module or do I have to recompile the entire kernel? Even then, how do I do that? Any help is greatly appreciated.

---

### Post by dancavs on 2006-10-17
ive never done it myself but there is a how-to here

[http://ubuntuforums.org/showthread.php?t=217657](http://ubuntuforums.org/showthread.php?t=217657)

---

