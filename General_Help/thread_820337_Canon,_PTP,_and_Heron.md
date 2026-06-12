---
title: "Canon, PTP, and Heron"
date: 2008-06-06
forum: General Help
---

### Post by Chriis on 2008-06-06
Hi , can u help me out to make a mount point?
this is my dmesg after plug my opened camera (Canon powersot s3is)


```

[67858.102223] usb 7-1: new high speed USB device using ehci_hcd and address 4
[67858.257655] usb 7-1: configuration #1 chosen from 1 choice
chris@Commando:~$ 

```

Thanks 

PS: I know it is a PTP protocol and blabla,..but WHY and HOW Gutsy mounted it,..and WHY Hardy can not!? WE definitly lost a very apreciated function in Heron :sad

Chriis

---

### Post by aquavitae on 2008-06-06
Have you checked under settings - removable devices?  IIRC you can set it there to automatically mount cameras so it could be that this is just not set. Otherwise you need to know what the device is called. Can you post a few more lines of dmesg. You chould see something like "new device configured on **/dev/ttyUSB0**" It the /dev/*** that's important. Once you see which device it is, use```
gnome-mount /dev/***
```

---

### Post by Chriis on 2008-06-06
Instead of: 

new device configured on /dev/ttyUSB0

it said:

usb 7-1: new high speed USB device using ehci_hcd and address 13



but maybe it's because it is a ptp protocol??

I wandering how in gusty they can mount it like a drive.
Ans why they change their mind about it in Hardy. :confused:

Btw Thanks for your advice, i realy apreciate :popcorn:

---

### Post by aquavitae on 2008-06-09
So no /dev/*** then? Does it specifically say anywhere that its seen a camera, or just that its seen a high speed USB device? The transfer protocol shouldn't affect that fact that its represented by a block device (i.e. /dev/***).  What do you get from ```
lsusb
```Also have a look at the /var/log/messages file - I think it sometimes shows more info than dmesg.

---

