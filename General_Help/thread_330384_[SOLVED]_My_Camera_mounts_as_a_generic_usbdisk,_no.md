---
title: "[SOLVED] My Camera mounts as a generic usbdisk, not a camera"
date: 2007-01-03
forum: General Help
---

### Post by Falcorian on 2007-01-03
When I plug in my Casio EX Z750, it auto-mounts as a usbdisk, and brings up the standard Nautilus window I have set to launch when a USB device is plugged in.

I'd like it to be recognized as a camera, and run the command I have set for when a camera is plugged in (so that it will auto-import into fspot).


Using

```
tail -f /var/log/messages
```

yields the following:

```

Jan  2 23:41:34 newton kernel: [17488827.596000] usb 4-1: new high speed USB device using ehci_hcd and address 7
Jan  2 23:41:34 newton kernel: [17488827.728000] usb 4-1: configuration #1 chosen from 2 choices
Jan  2 23:41:34 newton kernel: [17488827.728000] scsi2 : SCSI emulation for USB Mass Storage devices
Jan  2 23:41:39 newton kernel: [17488832.728000]   Vendor: CASIO     Model: DIGITAL_CAMERA    Rev: 1.00
Jan  2 23:41:39 newton kernel: [17488832.728000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan  2 23:41:39 newton kernel: [17488832.728000] SCSI device sda: 494848 512-byte hdwr sectors (253 MB)
Jan  2 23:41:39 newton kernel: [17488832.732000] sda: Write Protect is off
Jan  2 23:41:39 newton kernel: [17488832.732000] SCSI device sda: 494848 512-byte hdwr sectors (253 MB)
Jan  2 23:41:39 newton kernel: [17488832.732000] sda: Write Protect is off
Jan  2 23:41:39 newton kernel: [17488832.732000]  sda: sda1
Jan  2 23:41:39 newton kernel: [17488832.736000] sd 2:0:0:0: Attached scsi removable disk sda
Jan  2 23:41:39 newton kernel: [17488832.736000] sd 2:0:0:0: Attached scsi generic sg0 type 0

```

So it seems to be saying "Hi, I'm a digital Camera!", but that doesn't seem to help it.  Does anyone have any ideas? I'd love to be able to get this to work. :)



Thanks in advance,

Falcorian

---

### Post by lswb on 2007-01-03
Hmm, I think where your are seeing "Vendor: CASIO     Model: DIGITAL_CAMERA    Rev: 1.00",  the system is just reporting the model id string of the camera, this does not usually indicate anything to the system about what the actual type of the device is. Look at the line where it says "usb 4-1: configuration #1 chosen from 2 choices" What is choice #2, that's the question. 

Does the Casio camera have a setting to change it's presentation to the host system? I know on my HP Photosmart camera, there is a menu that lets me set it up so that the host computer will recognize it as a usb drive rather than a camera. It's helpful if you want to connect to a system that has no photo software installed or if you want to actually just use the camera as usb card reader for copying files to/from a storage card. Post again if this helps or not, there are a few other things to try.

---

### Post by Falcorian on 2007-01-03
There is an option to set it from USB mode to PTP{pictbridge) mode.

Except it never finishes mounting if set to that mode.

Againt, the logs show:

```
Jan  3 10:37:17 newton kernel: [17528168.508000] usb 2-1: new low speed USB device using uhci_hcd and address 3
Jan  3 10:37:18 newton kernel: [17528168.696000] usb 2-1: configuration #1 chosen from 1 choice
```

And that's it.


EDIT: However, if I open Fspot, is sees a "PTP/IP Camera" for importing, but when I try it gives me a "Could Not Claim The USB Device" error.

---

### Post by Falcorian on 2007-01-03
Ok, with the new information, I found a [bug report](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146) on this with a possible solution:

It said to add the following:

```
SYSFS{idVendor}=="07cf", SYSFS{idProduct}=="1043", MODE="0660", GROUP="plugdev"
```

to /etc/udev/rules.d/45-libgphoto2.rules, But with the correct id for my camera.

lsusb gives me this:

```
Bus 004 Device 012: ID 07cf:103b Casio Computer Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:0095 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

So I guess I should try:

```
SYSFS{idVendor}=="07cf", SYSFS{idProduct}=="103b", MODE="0660", GROUP="plugdev"
```


I'll give it a try and see what's up.

---

### Post by Falcorian on 2007-01-03
And it's totally working now! :D


Thanks for the push in the right direction lswb!

---

