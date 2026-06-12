---
title: "wireless"
date: 2007-03-18
forum: General Help
---

### Post by theophane.weber on 2007-03-18
Hi,

my wireless used to work right after installing ubuntu.. I have a WUSB54G (Linksys USB modem), that works on the rt2500 driver i think. The device was called 'rausb0'. For some reason, after 
a) updating the system (small updates that I would be surprised have anything to do with wireless)
b) simply changing the hostname (reverting didn't help),
'rausb0' became 'rausb1', and does not work anymore..

can anyone help me figure out what is going on?

thanks!

-theo

---

### Post by CocoAUS on 2007-03-18
Perhaps you need to change the value in your /etc/iftab file?  If the device has the wrong identifier, it won't work.

---

