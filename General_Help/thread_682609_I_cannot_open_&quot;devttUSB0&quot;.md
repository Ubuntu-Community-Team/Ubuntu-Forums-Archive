---
title: "I cannot open &quot;/devttUSB0&quot;"
date: 2008-01-30
forum: General Help
---

### Post by sankari on 2008-01-30
Hello!

I cannot open "/devttUSB0".

In my application when doing:
 open("/dev/ttyUSB0",O_RDWR|O_NOCTTY|O_NDELAY|O_NONBLOCK); 
I get "open error 2 no such file or directory"
when doing this:
 open("/dev/ttyS0",O_RDWR|O_NOCTTY|O_NDELAY|O_NONBLOCK);
works

When I go into "/dev" ttyUSB0 appears so then I do not understand the error message.
Also trying with minicom I get:

If I open "minicom" using ttyS0 then it works
If I open "minicom" using ttyUSB0 then I get "cannot open /dev/ttyUSB0: No such device" even if "ttyUSB0" appears in my /dev list.

Any help, please?

Thank you in advance.

---

### Post by dgray_from_dc on 2008-01-30
What exactly are you trying to do?

I'm no expert on what you're doing but it looks to me like you're making the assumption that /devttUSB0 will allow you open a USB port in the same way /dev/ttyS0 would allow you to open a COM port.

Or I could be wrong about the whole thing!!!!

Often times I find though that things like USB devices are channeled through the SCSI interface for easier handling in the software.  May be worth finding out through what interface the device you want to access goes.

---

### Post by geraldm on 2008-01-31
The special files under /dev can exist independent of whether there is a device attached.
When a USB device is plugged into a USB hub, there should be a message in /var/log/syslog that displays the filename.  Here is the message from a USB-to-RS232 serial converter:
Jan 30 12:15:19 lo kernel: usb 1-1.1: pl2303 converter now attached to ttyUSB0
When the device is unplugged, the special file /dev/ttyUSB0 still remains, but the device cannot be accessed.

Gerald

---

