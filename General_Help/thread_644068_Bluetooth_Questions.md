---
title: "Bluetooth Questions"
date: 2007-12-18
forum: General Help
---

### Post by sularus on 2007-12-18
Hello,

I have an Acer Ferrari 4000 series laptop. It has 64 bit AMD processor and built in Blutooth. Plenty of MEM and HD space.

I was able to config my bluetooth mouse using the documentation available in the Ubuntu website. However when I tried to connect my GPS, I am unable too do so. I followed the instructions on a few diff posts here but I was unsuccesful. 

I get alot of errors or commands just dont work IE sdptool browse

I get nothing returned on my device even though i can see it on the Bluetooth icon on my task bar.

I was wondering if I can connect more than one device to my pc or is it just one at a time. by the way I have a IO gear BT GPS. Thank you.

---

### Post by geraldm on 2007-12-18
Yes, you may connect more than 1 device.  Generally, connect one device for each available USB port.  There are restrictions on devices for the power that they use.  Devices with radio often exceed the 100ma available at that port, and some use 500ma maximum, which limits the number of devices that can be in use from any one ROOT usb port.
The USB hardware will shut down device(s) if they exceed the power available, and should provide an error (or it is a bug in the software).

There is a file "/proc/bus/usb/devices" that lists all available information about the device, and the power used is shown in the line beginning "C:" or "C:*". 

Gerald

---

