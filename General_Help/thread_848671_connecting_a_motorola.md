---
title: "connecting a motorola"
date: 2008-07-03
forum: General Help
---

### Post by eruheru on 2008-07-03
Hey all, 
I want to connect my motorola w755 to my computer via moto4lin or some other software. However, ubuntu doesn't recognize it when it is plugged in, and I can't seem to mount it. Also, I can't seem to find any of the information I might need to configure it to work. 
do any of you have anything that might help?
Thanks

---

### Post by tomdean@speakeasy.org on 2008-07-28
Did you solve your problem with the w755?

I have a similar problem.  
I installed moto4lin.
# sudo modprobe cdc_acm
Then, I connected the phone
# sudo lsusb
...
Bus 005 Device 018: ID 22b8:2b44 Motorola PCS 
...
Then, as a normal used, moto4lin and set the preferences.
  /dev/ttyACM0
  Update list shows the device above, set it as the AT device and the P2K device
The moto4lin message window shows
[info] Phone pluged as AT
Try to connect
[info] AT phone found
[info] Switching device /dev/ttyACM0 to P2K mode...
[error] Unable to open device
[error] Please check preferences
[error] Unable to connect

Exiting moto4lin and
# sudo moto4lin
I get the same results.  The preferences are there, though.

I believe moto4lin sees the device, just cannot deal with it.

---

### Post by tj111 on 2008-08-04
Same problem as tomdean here.  Anyone got any suggestions?

---

### Post by Canuckelhead on 2008-08-05
what values are you entering in AT vendor ID, AT product ID, P2K Vendor ID etc...

---

### Post by wnelson on 2008-08-10
Do the following

$ /sbin/lsusb | grep -i "motorola pcs"

Bus 004 Device 018: ID 22b8:2b24 Motorola PCS
| |
Vendor:Product

Make sure you vendor= and product= are your phones id's.

Also change the usb:vVENDOR8pPRODUCT* to also reflect your id's.

I had to add this to the end of /etc/modprobe.d/alias to get my motorola w385 to work.

alias usb:v22B8p2B24* usbserial
options usbserial vendor=0x22b8 product=0x2b24

dmesg will result in /dev/ttyUSB0 and 1

moto4lin should work now.


This site will help also.

[http://www.arachnoid.com/linux/linux_mobile_internet_access.html](http://www.arachnoid.com/linux/linux_mobile_internet_access.html)


Walt

---

### Post by billydv on 2008-09-07
Anyone have any luck with this yet? I just rebuilt my kernel including just about all usb serial devices to no avail, no matter what I have done, when I plug the phone in it doesn't connect to a device.

---

### Post by mole84 on 2008-09-25
It seems that there is small confusion of whether to use the cdc_acm kernel module or the usbserial module to connect mobile phones, does anyone have and wisdom on the topic?

---

### Post by mole84 on 2008-09-25
I also think there may be an issue with the correct p2k library. Currently aptitude has libp2kmoto0 v.01

---

### Post by dalessio on 2008-10-29
I just purchased the w755 and I've been trying to get the thing connected via moto4lin. Here's where I've gotten so far.

I added the following to a file I called "w755.options" in my /etc/modprobe.d/ directory.

alias usb:v22B8p2B44* usbserial
options usbserial vendor=0x22b8 product=0x2b44

Note that my device id was 0x2B44 NOT 0x2B24 as written above. I'm not sure if that is just a different version of the same device. You can check the device id by running "lsusb" from the /sbin directory.

When I plug in the phone everything appears to go smoothly, dmesg shows:

[ 2191.725925] usb 1-1: new full speed USB device using uhci_hcd and address 11
[ 2191.757041] usb 1-1: configuration #1 chosen from 1 choice
[ 2191.758778] usbserial_generic 1-1:1.0: generic converter detected
[ 2191.758943] usb 1-1: generic converter now attached to ttyUSB0
[ 2191.769596] usbserial_generic 1-1:1.1: generic converter detected
[ 2191.769759] usb 1-1: generic converter now attached to ttyUSB1

I tell moto4lin to use /dev/ttyUSB0 and it finds the phone, the phone answers, appears to start to connect, and then drops. After this, running /sbin/lsusb it appears that the device id has changed. It now reads 0x2B41 instead of 0x2B44. Upon reconnecting it returns to 0x2B44

I'm not sure if this is a common thing, but I certainly don't know what to do next. After doing some reading I suspect the phone is trying to act as a usb storage device to install some windows software and than changing back into a phone. Perhaps this is part of the solution...

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by ooolongT on 2009-02-13
I can not get my w755 connected either, has anyone made any progress?

---

### Post by gbear14275 on 2009-12-08
i'm guessin theres still no progress here?  tried to walk through but couldn't connect.

---

### Post by Kenjitamura on 2010-05-08
Sorry to bump such an old thread but has anyone been able to get their W755 connected for file transfer?  Is there a way or a newer program I can use to access my W755?  The closest I've gotten to connecting to it is using dalessio's trick.  Seems kind of pitiful ubuntu can't connect to this phone when windows users have reported success using p2k tools and commander.

---

