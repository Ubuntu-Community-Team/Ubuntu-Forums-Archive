---
title: "How can I access my Kindle Fire via Gmtp (or equivalent)?"
date: 2017-09-13
forum: General Help
---

### Post by Bobby_James on 2017-09-13
I am trying to access my Kindle Fire 7 from Ubuntu so that I can backup the books on to the Calibre Reader.

The "Files" app shows the Kindle partition but it is empty. I installed gmtp but when I run it from the command line and connect the Kindle I get:

Device 0 (VID=1949 and PID=0121) is UNKNOWN in libmtp v1.1.10.
Please report this VID/PID and the device model to the libmtp development team
ignoring libusb_claim_interface() = -6PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
Android device detected, assigning default bug flags
Error 1: Get Storage information failed.
Error 2: PTP Layer error 02fe: get_handles_recursively(): could not get object handles.
Error 2: Error 02fe: PTP: Protocol error, data expected
Detect: No available Storage found on device?

I have no idea how to resolve this. I assumed that mtp would work. Some time ago I was able to get access to the Kindle via Gmtp but I can't remember how I did it. 

I would appreciate any ideas! Thanks!

---

### Post by TheFu on 2017-09-14
I have a Fire 8 HD gen7.  

Just connected it to my minimal Ubuntu 16.04 laptop to look around.  I used **caja** for this.

MTP is working for me, using the usbfs driver according to **lsusb**. Didn't have to do anything special or install anything to make it work.

I see the expected files, but the Kindle and Book directories on both storage devices are empty.  I have only 1 paid Kindle book, never found it on the device, but use alternate programs to read lots and lots of other books, documents, etc.  I find it much easier to avoid DRM.
The device seen is:```

Bus 001 Device 006: ID 1949:0262 Lab126, Inc.
```

Kindle books are almost always encrypted. That makes importing them into Calibre a challenge - and we cannot discuss those techniques here. I have NEVER been able to do it, but know a few people who have .... using Windows.

As for the issue you have - try a different USB cable and/or different USB port?

---

