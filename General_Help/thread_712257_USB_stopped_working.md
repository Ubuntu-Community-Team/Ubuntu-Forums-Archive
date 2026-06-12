---
title: "USB stopped working"
date: 2008-03-01
forum: General Help
---

### Post by ryantmer on 2008-03-01
I posted about my DLink WUA-1340 USB wireless G adapter not working a few days ago, but I have discovered that it is my USB ports that stopped working, not the adpater itself. I have no idea even where to start... lsusb just hangs, and the problem solves itself for a few hours (about a day) if I restart. Any ideas or suggestions as to what to try?

---

### Post by geraldm on 2008-03-01
When something stops working, always look in the logs for a pertinent error message.
The file is /var/log/syslog

I would guess that there is an error message in there that may have to do with unloading the entire bus that the device was on, and lsusb cannot complete accesses that it needs to finish.
It should not hang, and if it hangs without a message in the log, then that should be considered a bug (check first if there is already a bug reported before entering a new report.)

Gerald

---

### Post by ryantmer on 2008-03-02
Thanks for the tip. This message seems to be appearing whenever I plug in a USB device:

```
phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error
```

Any ideas?

---

### Post by geraldm on 2008-03-02
There is apparently no driver set up for this device yet ?
The message about "usb_vendor_request" indicates that the device is using instructions that are specific to that vendor. With Linux, it is always best to check before buying to see if you can use a device that is known to work.

This is for you to evaluate, it may help,  Provided without recommendation
[https://help.ubuntu.com/community/WifiDocs/Device/D-Link_WUA-1340](https://help.ubuntu.com/community/WifiDocs/Device/D-Link_WUA-1340)

Gerald

---

### Post by ryantmer on 2008-03-02
No, it does work, as do all my other USB devices (printer, external drive, flash drive, etc.), but after a few hours of the D-Link being plugged in, none of the USB ports work anymore, forcing me to restart, and I would rather avoid doing that.

---

### Post by rubing on 2008-07-05
I am having the same problem using a WUSB54GC Linksys Wireless G adapter.  I bought it about a week ago and it was working fine, except for the computer periodically freezing up (I think b/c cause of flash).  Then yesterday I started getting those same messages and could not use the internet for more than a couple of minutes.  Today, I have now been on for 15 and not been kicked off...so maybe it fixed itself?

Could these errors be due to the fact that one time I unplugged and replugged the USB device, while the computer was running?

Here are the kind of errors I get:

/var/log/syslog:Jul  4 07:52:52 rubing-laptop kernel: [  182.033399] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
/var/log/syslog:Jul  4 07:52:54 rubing-laptop kernel: [  184.533095] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
/var/log/syslog:Jul  4 07:52:57 rubing-laptop kernel: [  187.031771] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
/var/log/syslog:Jul  4 07:52:59 rubing-laptop kernel: [  189.530448] phy0

---

