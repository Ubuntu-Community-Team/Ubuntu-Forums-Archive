---
title: "USB port randomly disconnects [gutsy]"
date: 2007-12-03
forum: General Help
---

### Post by drengi on 2007-12-03
The USB port that handles my WUSB54G v4 keeps disconnecting by itself every 20-60 minutes. A full reset is required each time to restore functionality. The wusb54g works fine, but it dies as soon as the USB port disconnects.  When the USB  disconnects it also completely cuts power - unplugging and plugging back in the wusb54g doesn't restore it either.

The USB port that handles my mouse doesn't disconnect, so I have really no idea what's going on. It can't be the drivers since this problem has happened with both ndiswrapper and native linux drivers. I'm pretty sure it's not the actual USB port hardware either since it works fine in Windows and I even installed a PCI usb card to make sure. I even installed feisty on another partition and tested it there, but it didn't fix it. It can't be my network applet either: it has happened with gnome network manager as well as with WICD.

I'll post exactly what my system log says as soon as it happens again using another computer. From what I remember it just says "usb 4-1: disconnect, address 3" out of nowhere. No prior messages indicate that the port is about to fail/disconnect.

---

### Post by drengi on 2007-12-03
Update:

I installed fedora 8 and managed to get on the internet. But guess what - the exact same problem is still there. My USB ports still randomly disconnect.

Looks like the problem has two possible causes: 

-Linux kernel
-PC Hardware

Since both of those things are completely out of my reach, I guess it's back to windows for me...sigh :(

---

### Post by geraldm on 2007-12-03
I was expecting to see messages in the log.
Some possible sources of the problem are the driving module, which should have handled some event, or the usb subsystem, which should provide information about the cause of the disconnect.  It could happen that the device received a reset, and could/did not reset, and
so the usb subsystem ejected the device off the OS,  Look for a possible bug report against 
the module that was driving the device.  Which module was it? 
If you do not find a bug report on the driver, then create one, showing the details OS, device,
message received, frequency that this occurs, etc.

Gerald

---

### Post by nitrofurano on 2007-12-04
if you are using usb memories (pen-drives or whatever), be sure doing 'sudo sync' any time you're doing important file transfer for avoiding loosing stuff (even before ejecting!) - i inserted an icon launcher on the gnome panel with 'gksudo sync', for example, it's very useful! :-)

---

