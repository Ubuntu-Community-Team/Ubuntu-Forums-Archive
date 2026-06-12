---
title: "mount external harddrive connected to USB hub"
date: 2017-10-10
forum: General Help
---

### Post by GwibberFooey on 2017-10-10
I have a WD external harddrive that I would like to use with my home computer. I have MATE Desktop on Ubuntu 16.04.03 LTS on a machine with Intel quad-core i5. When I connect the external harddrive to a USB hub, there is neither automatic detection nor automatic mounting. For example, the command ```
 df -h 
``` returns the same standard output both before and after the drive is connected to the hub. However, when I connect the drive directly to the USB port of the computer (ie. not connected to the USB hub) then all partitions present on the external harddisk mount automatically.
Please somebody help me mount the harddisk when it gets connected to the USB hub. Thanks in advance.

---

### Post by efflandt on 2017-10-11
Does the USB hub have its own separate power supply and is anything else connected to the hub? If it is an unpowered USB hub, it may not be getting enough power from a single USB port on the PC to power multiple devices. For example USB 2.0 is only required to provide 500 mA, but a drive might use as much as 1A (1000 mA). So USB 2.0 drives were often supplied a cable with 2 USB plugs, just in case. USB 3.0 is required to provide 900 mA.

---

### Post by ajgreeny on 2017-10-11
Some external drives (I have one) have a twin plugged Y cable to allow this problem to be overcome; the main plug goes into the hub, the other into a usb socket on the computer to supply extra power, or you could try it on the hub so both plugs are in the hub.

---

### Post by GwibberFooey on 2017-10-11
The harddisk uses USB 2, and it has no dedicated power cable -- it is powered exclusively by USB. When I wrote the original post of this thread, the USB hub was being powered exclusively over the USB cable which connects it to the computer's USB 2 port. There was already a mouse and a keyboard being powered from the hub. It seems that at that time the hub had not enough power to support a third device such as the external harddisk.
I searched for and found the hub's dedicated 1.5 amp AC power adapter. After adding the AC adapter, when I connect the mouse, the keyboard and the harddisk to the hub, then all volumes on the harddisk become mounted automatically. The problem has been rectified. 
I thank you very much.

---

