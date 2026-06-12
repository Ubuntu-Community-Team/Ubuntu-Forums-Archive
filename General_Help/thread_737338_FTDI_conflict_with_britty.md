---
title: "FTDI conflict with britty"
date: 2008-03-27
forum: General Help
---

### Post by paul437114 on 2008-03-27
When I try and connect the FTDI USB to serial device I get the following error messages:

 kernel	[ 3145.652000] ftdi_sio 2-5:1.0: FTDI USB Serial Device converter detected
kernel	[ 3145.652000] usb 2-5: configuration #1 chosen from 1 choice
kernel	[ 3145.652000] usb 2-5: FTDI USB Serial Device converter now attached to ttyUSB0
NetworkManager	<debug> [1206640715.896622] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_403_6001_FTCVPZUO'). 
brltty[3830]	USB interface in use: ftdi_sio
kernel	[ 3145.980000] usb 2-5: usbfs: interface 0 claimed by ftdi_sio while 'brltty' sets config #1
kernel	[ 3145.984000] ftdi_sio 2-5:1.0: device disconnected
kernel	[ 3145.984000] ftdi_sio ttyUSB0: FTDI USB Serial Device converter now disconnected from ttyUSB0

Can anybody help with this?

---

### Post by geraldm on 2008-03-27
I know what needs to be done, disable britty (braille terminal typewriter) if you do not use braille device.  

There was a reply in another thread to try remove britty and britty-x11, and the person did not reply after that.  It might work for you.  After that, then try to connect the FTDI device.
[http://ubuntuforums.org/showthread.php?t=289250](http://ubuntuforums.org/showthread.php?t=289250)

Gerald

---

### Post by paul437114 on 2008-03-28
Thanks a lot for the help.  It definitely pointed me in the right direction and I have now edited the brltty udev rules and the problem is sorted. Seems like a lot of people had the same problem, but it was knowing where to look.
Thanks again

---

