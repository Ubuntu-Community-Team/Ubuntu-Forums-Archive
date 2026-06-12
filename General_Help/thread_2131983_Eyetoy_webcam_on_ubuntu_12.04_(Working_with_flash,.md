---
title: "Eyetoy webcam on ubuntu 12.04 (Working with flash, but not cheese)"
date: 2013-04-03
forum: General Help
---

### Post by bluelight0 on 2013-04-03
Hi.

i just plugged in a [eyetoy webcam for ps2]("http://en.wikipedia.org/wiki/EyeToy") and i have it working with flash apps online.

But for some reason it will not work under cheese or skype.
I had a search around the internet but cannot find anything like this.

Any hints?

Some info:

Skype recognizes device but no video data shown when tested
Flash recognizes and displays video perfectly.
Cheese opens but shows no sign of recognising any camera.
Ubuntu 12.04

---

### Post by robert shearer on 2013-05-04
Same problem here (also 12.04) and after some research the consensus was that it either worked out of the box or not depending on the Ubuntu version.  Sometimes working then not then working again as versions incremented....go figure.
However one user claimed that it worked on some usb sockets and not others and the sockets that worked changed as versions incremented too...!

Sooooo,  with nothing to lose I tried my non working eyetoy in another usb socket and it was recognised and worked...!!!
~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 004: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 001 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
**Bus 004 Device 003: ID 054c:0155 Sony Corp**. 

So keep replugging and running this... ```
lsusb
``` until it is recognised then it should work in cheese et al.

So conclusion is that it runs in usb 1.1 and not in usb 2.0. if your compy is so modern as to be usb 2.0 only then...?????

---

