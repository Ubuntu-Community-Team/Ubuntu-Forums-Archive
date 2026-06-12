---
title: "pen drive not detected in /dev"
date: 2014-02-15
forum: General Help
---

### Post by MOHAK_SHARMA on 2014-02-15
I am using UBUNTU 12.04 .My problem is that USB is detecting my pendrive.. When i connected my 2gb pendrive it is not detected.Plz Help

lsusb says :
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 1307:0163 Transcend Information, Inc. 256MB/512MB/1GB Flash Drive

dmesg | tail says :
[ 3269.336739] usb 2-1: USB disconnect, device number 5
[ 3296.568113] usb 2-1: new high-speed USB device number 6 using ehci_hcd
[ 3296.709983] Initializing USB Mass Storage driver...
[ 3296.711940] scsi9 : usb-storage 2-1:1.0
[ 3296.712257] usbcore: registered new interface driver usb-storage
[ 3296.712263] USB Mass Storage support registered.
[ 3323.152093] usb 2-1: reset high-speed USB device number 6 using ehci_hcd
[ 3333.400115] usb 2-1: reset high-speed USB device number 6 using ehci_hcd
[ 3349.644109] usb 2-1: reset high-speed USB device number 6 using ehci_hcd
[ 3349.892160] usb 2-1: reset high-speed USB device number 6 using ehci_hcd
[ 3360.272618] scsi 9:0:0:0: Device offlined - not ready after error recovery


does not detect in fdisk ; gpart ; blkid ;

---

### Post by ian-weisser on 2014-02-17
The pen drive is not responding correctly to the kernel's queries. It seems to be unreadable, so it's not mountable.
Time to purchase a replacement pen drive.
It happens.

---

### Post by tgalati4 on 2014-02-17
Try different USB ports and different machines.  If you get at least one machine to mount it, then you can attempt file recovery.

---

### Post by MOHAK_SHARMA on 2014-03-22
it is not mounting on any machine !!!

---

### Post by slooksterpsv on 2014-03-22
Then the Pen Drive is bad. It sucks, but it happens.

---

