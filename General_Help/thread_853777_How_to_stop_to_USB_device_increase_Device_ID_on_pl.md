---
title: "How to stop to USB device increase Device ID on plug/unplug events?"
date: 2008-07-08
forum: General Help
---

### Post by jreinis on 2008-07-08
How knows solution, not explanation?
If I unplug and than plug ANY USB device (for instance my webcam it works video/sound excellent till plug/unplug event) 
lsusb shows increased Device ID and after that all program associated with that USB device DO not detect the device at all.(skype/ekiga do not detect webcam for example even lsusb sees it)

Note bolded
lsusb:
Bus 008 Device 001: ID 0000:0000  
Bus **007** Device **019**: ID 046d:08c3 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  ....

UNPLUG than PLUG
lsusb:
Bus 008 Device 001: ID 0000:0000  
Bus **007** Device **020**: ID 046d:08c3 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  ....

---

### Post by jreinis on 2008-07-14
Bump

---

