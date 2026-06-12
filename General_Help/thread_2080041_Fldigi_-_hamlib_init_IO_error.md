---
title: "Fldigi - hamlib_init: IO error"
date: 2012-11-02
forum: General Help
---

### Post by fyrmedic on 2012-11-02
I just upgraded Ubuntu to 12.10 64 bit and as part of the upgrade I install Fldigi. My problem is that when I try to set up my rig I get the following error - hamlib_init: IO error. It doesn't seem to matter how I set it up. 

I have used Fldigi in the past and have had it working flawlessly with previous versions of Fldigi and Ubuntu. 

My radio is a Yaesu Ft-897d and I am using a USB cable, not a USB to serial adaptor. This is the very same cable that I have used in the past with previous software versions.

lsusb returns:

Bus 001 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 002 Device 002: ID 046d:0a01 Logitech, Inc. USB Headset
Bus 002 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1058:1102 Western Digital Technologies, Inc. 

I think the cable that the radio is on is the one labeled Prolific etc... It is connected directly to the back of the computer and not through a hub.

I have checked the connection and even after re-connecting in a different usb port it isn't recognized. 

Here is the output that I get when I run fldigi from command line. I know there are a number of errors relating to audio devices. I am fairly certain this isn't the problem.

[http://pastebin.com/NeKcZnQz](http://pastebin.com/NeKcZnQz)

I don't remember what I did but I was able to get fldigi to at least read the current frequency a day or so ago. Unfortunately, whatever I did didn't stick and I am stuck at square one again.

Any hams out there with a similar experience or a solution?

Any ideas are appreciated.

Regards,

Brad 
KD0GBX

---

### Post by fyrmedic on 2012-11-02
Sorry,

I have googled this and searched this out for several hours over several days without success.

Thought that would be pertinent. I have noticed that new posters on the forum don't often take the time to look elsewhere first and I have rarely encountered a problem that I haven't found a solution to via "the google."

:P:P:P:P:P:P:P:P

---

### Post by fyrmedic on 2012-11-09
bump

---

### Post by CharlesJohnston3 on 2013-03-23
It is a permissions Issue
/dev/ttyUSB0 is part of group "dialout" add your user(s) to that group, log out and log back in.

---

