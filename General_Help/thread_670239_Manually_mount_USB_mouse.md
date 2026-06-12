---
title: "Manually mount USB mouse?"
date: 2008-01-17
forum: General Help
---

### Post by perfektion on 2008-01-17
My system sometimes loose my USB mouse and it doesn't automount it if I remove and replug it. I have to restart Xorg to get the mouse back. So what command do I use to manually mount the USB mouse so I don't have to restart Xorg every time it happens?

---

### Post by comandrei on 2008-01-17
You can't mount a mouse, because it is not a block device (i.e. something that can store data)
udev should automatically mount it for you. See if the device is seen with lsusb.

---

### Post by perfektion on 2008-01-17
This is what it looks like when the mouse is plugged in and working:

```
:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c01d Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

```


And this is what it looks like after removed and replugged in the same USB-port but not working:

```
:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c01d Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
```


(So now I have to restart Xorg for it to work again.)

I also have to restart Xorg to make my Wacom tablet to work too. (However I have no problems with other USB-devices like iPod or external harddrives.)

Does this means something is wrong with my udev? And any ideas how to fix it?

---

