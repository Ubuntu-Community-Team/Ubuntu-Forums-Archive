---
title: "Remote Connect to Active/Default Session"
date: 2012-11-28
forum: General Help
---

### Post by BigBubbaX on 2012-11-28
Hi,

I'm working on a project that ties an arduino to a magstripe card reader through a laptop.


The setup:
A user can swipe a card, which is connected to the laptop. The laptop recognizes the reader as a HID/keyboard and prints the card to the screen, appending a line return at the end. I have a serial client open on the laptop, so the card data is sent straight to the Arduino, which interprets it and acts on it.

For most of the semester, I've been using Windows 7, with PuTTY to connect to the arduino. This setup sucked for the most part, because no matter how many steps I took to troubleshoot the connection, the serial port would die after a day or two (and I need it to run for weeks on end).

So I installed Ubuntu 12.04 on the laptop, and then installed "minicom" on Ubuntu. 

Sweet, finally a really useful serial client! Everything works great, except for a small quirk with my specific setup:


The problem:
The laptop has no screen. Which is why I'm recycling it with this project. I need to by able to log into the laptop through my dorm's wireless network (my own router) and configure it. So far as I can tell, only the actual, physical session that is directed to the computer's non-existent screen has access to the USB card reader... I can plug in an external screen and see the card reader print out data to a text file, but whenever I try a remote program, I get a new session, and the card reader doesn't do anything at all. How can I connect to the "real" desktop? VNC has been awful because of artifacts and screen refreshes even though it seems to be connecting to the right one.

I've tried:
Vino, TightVNC, x11vnc, freeNX, xRDP, X2go

I have not tried TeamViewer, because it leaves the "Please like us on Facebook" dialog after I close the connection, and that gets in the way of the serial program collecting keyboard data.

Thanks!,
-BBX

---

