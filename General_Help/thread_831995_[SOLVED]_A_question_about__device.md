---
title: "[SOLVED] A question about  device"
date: 2008-06-17
forum: General Help
---

### Post by ubuscout on 2008-06-17
Hi people, a question...

when I insert a new device (ie usb-storage, usb-serial or mass-storage...), I know it'll be mapped on /dev like char/block device and its major an minor number...

for example my usb-serial :

crw-rw---- 1 root uucp 188, 0 17 giu 15:38 /dev/ttyUSB0

I can also with lsusb command see the device ... :

Bus 003 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port


Lookin' around I find file /usr/share/usb.ids that report that information.
I also found in /usr/src/linux/Documentation/device.txt information about its major number as reported again in /etc/modprobe.conf...

So my question :)  ...where I can find the link about "vendor_number : pr_vendor_number"  and its major:minor number related... I'm thinking must be a somewhat like a "crosstable" ...maybe this work has done by kernel directly, but I think always by a crosstable I think ?

The question's target is exploit, for my knowledge, how this process work... also for be sure at which device is related in /dev my usb-serial for example... (In this case I know ...it was easy see ttyUSB0 ;)  ... )


thx for all could clarify me about this question :)

---

### Post by ubuscout on 2008-06-18
bump...  could anyone help me plz ? :)

---

### Post by geraldm on 2008-06-18
The vendorID is assigned by the usb organization, which promulgates the standard.  Some systems may have a file containing the vendorID numbers that have been already assigned in file /usr/share/usb.ids  or /usr/local/share/usb.ids
This file is present in the usbutils package.

The major number is assigned by Linux.  If you have the kernel source, the information is in LINUXSRC/Documentation/devices.txt  This number is the identification of the driver.  It is the driver that may assign dynamically the minor number.  This information may be available in the "ls -l " command for the device.

crw-rw---- 1 root uucp 188, 0 17 giu 15:38 /dev/ttyUSB0
The major shown for your device is 188 with a minor number of 0

The minor number is usually displayed in the file /var/log/syslog 

Gerald

---

### Post by ubuscout on 2008-06-19
> **geraldm said:**
> The vendorID is assigned by the usb organization, 
...
The minor number is usually displayed in the file /var/log/syslog 
Gerald

thx Gerald... that's was what I've got  lookin' around... but my question is still alive, maybe I've not explain me well...

here we are... but exactly, where is stored the information (...or how is the process) for kernel with which it link that "vendor_number : product_number" at the the specific major number ?

thx :)

---

### Post by ubuscout on 2008-06-19
> **geraldm said:**
> The vendorID is assigned by the usb organization,
...
The minor number is usually displayed in the file /var/log/syslog 

Gerald


Sorry... lookin' better, as u remembered, in file usb.ids at the end there is 
 also the "List of known device classes, subclasses and protocols" ...that clarify me all :) ...so when insert an usb device ie. kernel read the device descriptor and associate it his major/minor number etc...  thx

---

