---
title: "I am having problems with my Verizon Motorola L7c phone and Moto4Lin"
date: 2007-10-10
forum: General Help
---

### Post by Siph0n on 2007-10-10
This is my device and settings :

ACM Device: /dev/bus/usb/001/002
AT Vendor ID: 22b8
AT Product ID: 2a64
P2K Vendor ID: 22b8
P2K Product ID: 2a64

I see a lot of people saying the device is '/dev/ttyACM0' , but that device doesn't show up on my computer....

I configured Moto4Lin as sudo, than went back into moto4lin as a regular user and went to preferences (since it was in AT mode) and clicked Switch to P2K, and the dialog window says:

[info] Switching device /dev/bus/usb/001/002 to P2K mode...
[error] Unable to open device
[error] Please check preferences

Any help would be awesome!!! Thanks

---

### Post by geraldm on 2007-10-12
Just after the usb phone is plugged in look for "ttyACM" in file /var/log/syslog
If the phone is driven by module cdc_acm, that is where the information would be logged.
If you configured the device using sudo, then possibly the permissions are owned by root,
and you would need to change the permissions to whatever group/user is needed to
use the device.

Find the permissions of the device:
```

ls -l /proc/bus/usb/001/002

```
The file /proc/bus/usb/devices might contain information on the driver for the device.

Gerald

---

### Post by Siph0n on 2007-10-13
This is what I see in /var/log/syslog

Oct 13 12:05:13 wepwawet kernel: [ 4654.224000] usb 1-1: new full speed USB device using uhci_hcd and address 2
Oct 13 12:05:13 wepwawet kernel: [ 4654.384000] usb 1-1: configuration #1 chosen from 1 choice

Does this mean that the phone isn't using the cdc_acm module? And if not, how do I get it to use that module? Thanks.

---

### Post by Siph0n on 2007-10-13
I did a modprobe -r uhci_hcd and modprobe cdc_acm to load the cdc_acm module and than plugged my phone in... but no luck. I loaded the uhci_hcd module back and still no ttyACM device :( Any other suggestions?

---

