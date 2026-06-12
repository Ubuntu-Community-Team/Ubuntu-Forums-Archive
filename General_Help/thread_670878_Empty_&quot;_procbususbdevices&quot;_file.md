---
title: "Empty &quot; /proc/bus/usb/devices&quot; file"
date: 2008-01-17
forum: General Help
---

### Post by miqie on 2008-01-17
I cannot get Gutsy to see my flashdrive.  I am on a dualboot WinXP/Ubuntu computer.  The drive works fine in XP, but is absolutely dead in Gutsy.  Not even a flicker.  Is the fact that the"/proc/bus/usb/devices"  file is empty a clue to me problem?  Here is the output from the terminal window:

Bus 001 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

I have a USB mouse plugged in, which is working and an old Visioneer Onetouch scanner which is not detected by Xsane.
One thing that did come up right before the login screen was a checklist of what was loading. I noticed 3 lines:

USB 5-5 device not accepting address 5 error-110
USB 5-5 device not accepting address 6 error-110
USB 5-5 device not accepting address 7 error-110

then it went to the login screen. Also, yesterday I loaded "USB View" thinking maybe it could help. When I put the stick in and open this application I get the message: "Cannot open the file /proc/bus/usb/devices" and then it says: "Verify that you have USB compiled into your kernel, have the USB core modules loaded, and have the usbdevfs filesystem mounted." Does this provide any clues to my problem? The flash drives also do not work when running Gutsy from the live CD.
__________________

---

### Post by geraldm on 2008-01-18
When the file /proc/bus/usb/devices is NOT present, it may be because the usbfs is not mounted.  One way is to try mounting it, (which may fail if there is no directory /proc/bus/usb)
```

sudo mount -t usbfs usbfs /proc/bus/usb

```

Another way to get the device information that does not depend on that file is to use the command lsusb, which might show the vendor and product:
```

lsusb

```
Bus 001 Device 010: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

Then try lsusb, with the vendorID and productID shown above:
```

 lsusb -d 067b:2303 -v

```
The output of the above command provides all the information that would be shown in the devices file.

Gerald

---

### Post by miqie on 2008-01-18
Here is the output from the terminal:
mike@mike-desktop:~$ sudo mount -t usbfs usbfs /proc/bus/usb
[sudo] password for mike:
mount: usbfs already mounted or /proc/bus/usb busy
mount: according to mtab, usbfs is already mounted on /proc/bus/usb
mike@mike-desktop:~$ lsusb
Bus 001 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
mike@mike-desktop:~$ 

There is still no activity from the stick.  It doesn't show up anywhere.  I know its working because i can boot into WinXP and it works fine.

---

### Post by geraldm on 2008-01-18
If your system can get the device to accept an address, then you can get the information from that bus, device number.
The command would use the bus-device number that has already appeared in the log, either dmesg or /var/log/syslog
for example, 
USB 5-5 device not accepting address 5 error-110
```

lsusb -s 5:5 -v

```
Note that if the device does not accept an address, then this does not work.  Not accepting an address may mean a defective or a device non-compliant with the usb standard.

Gerald

---

