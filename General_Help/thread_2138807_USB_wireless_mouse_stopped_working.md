---
title: "USB wireless mouse stopped working"
date: 2013-04-25
forum: General Help
---

### Post by mconlin on 2013-04-25
[COLOR=#000000][FONT=Helvetica]I am using Ubuntu 10.04 
Mouse is a Logitech m570[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]This problem occured after a two years of successful usage of this mouse on this machine[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Helvetica]
mark@marks-Latitude-E6510:~$ lsusb
Bus 002 Device 007: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]

```
```
[COLOR=#000000][FONT=Helvetica]mark@marks-Latitude-E6510:~$ dmesg | grep -i usb
[ 620.335673] usb 2-1.3: device descriptor read/64, error -32
[ 620.524650] usb 2-1.3: new full speed USB device using ehci_hcd and address 44
[ 620.945042] usb 2-1.3: device not accepting address 44, error -32
[ 621.023990] usb 2-1.3: new full speed USB device using ehci_hcd and address 45
[ 621.442056] usb 2-1.3: device not accepting address 45, error -32
[ 621.442366] hub 2-1:1.0: unable to enumerate USB device on port 3[/FONT][/COLOR]

```

---

### Post by SifGrey on 2013-04-25
This might be of use for you:
[http://askubuntu.com/questions/117524/usb-device-not-accepting-address](http://askubuntu.com/questions/117524/usb-device-not-accepting-address)

It seems to be the same issue you are having.

---

### Post by mconlin on 2013-04-26
> **SifGrey said:**
> This might be of use for you:
[http://askubuntu.com/questions/117524/usb-device-not-accepting-address](http://askubuntu.com/questions/117524/usb-device-not-accepting-address)

It seems to be the same issue you are having.

Yeah that doesn't help me.

---

