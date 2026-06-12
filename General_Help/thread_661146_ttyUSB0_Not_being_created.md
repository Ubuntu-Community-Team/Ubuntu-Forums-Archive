---
title: "ttyUSB0 Not being created"
date: 2008-01-07
forum: General Help
---

### Post by Jivicin on 2008-01-07
I am currently having a problem with my USB to serial adapter.  I have a Keyspan adapter that worked perfectly under Feisty.  When I plug the device in /dev/ttyUSB0 is created, and I can interact with it.  Now that I have updated to Gutsy, the device no longer mounts under /dev.

I also tried removing brltty, which had no effect.  Here is the output of dmesg:

```
[ 2035.885978] usb 2-1: new full speed USB device using uhci_hcd and address 6
[ 2036.089936] usb 2-1: configuration #1 chosen from 2 choices

```

lsusb output: 

```
Bus 004 Device 002: ID 413c:2003 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 0424:2504 Standard Microsystems Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 002 Device 006: ID 06cd:0121 Keyspan 
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 413c:3012 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000 
```

---

### Post by geraldm on 2008-01-08
It is best to have the serial device plugged in at boot.  The name used to access the device can found in the log then.  If the device name does NOT appear, it is usually related to not having the correct modules loaded.  Check in the /boot directory for a config-{version} for a version that matches the kernel you are using for these:
CONFIG_USB_SERIAL
CONFIG_USB_SERIAL_KEYSPAN
try after substituting your version:
grep CONFIG_USB_SERIAL_KEYSPAN /boot/config-{version}
If these are not "=y" or "=m" then you will need to get a kernel that has those options available.

After you have the correct modules loaded, you can find the name in the log when you replug the device.
```

tail /var/log/syslog

```

Gerald

---

