---
title: "POSX Xi3000 Barcode Scanner"
date: 2008-05-03
forum: General Help
---

### Post by DamonChyld on 2008-05-03
I am trying to get my POSX Xi3000 scanner to work but am not having any luck. I can scan the setup barcodes to configure how it reads/outputs info. When I try to scan a product, it will scan one barcode (gives no output) and then will not do anything until I unplug/plug it in again. 

My lsusb on it is:
```
Bus 001 Device 006: ID 04b4:cfa1 Cypress Semiconductor Corp. 
```
A google search for this returns only a few pages that don't seem to be of any help.

I have tried it in my VirtualBox installation but it behaves the same there.

I would appreciate any help or guidance!

---

### Post by Margueritte on 2008-05-08
Hi

Have you managed to sort out your scanner yet??
If so, what did you do to fix this problem.  I have the same or similiar problem with the same scanner

---

### Post by DamonChyld on 2008-05-12
I was not able to find a solution in Ubuntu so decided to dual boot xp/gibbon.

---

### Post by rattboi on 2008-09-03
I found a fix for this problem.

It should be loading the usbkbd module when you plug it in, but it is not. You can load it manually like this:

#:~$ sudo modprobe usbkbd

then enter your password. That should make it work, but only until you reboot. To get it to work all the time, you need to add the usbkbd driver in your /etc/modules file.

#:~$ sudo gedit /etc/modules

at the bottom of the file, add usbkbd. Reboot, and the module will be loaded on boot, and your scanner should work fine.

---

