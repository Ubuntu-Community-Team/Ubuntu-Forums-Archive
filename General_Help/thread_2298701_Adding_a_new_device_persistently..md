---
title: "Adding a new device persistently."
date: 2015-10-13
forum: General Help
---

### Post by Lars Noodén on 2015-10-13
In 14.04 LTS, I have to add a device manually after each reboot:

```

sudo mknod -m 660 /dev/sr1 b 11 0

```

How do I get that device to persist across reboots?  Where should the change really be made?

---

### Post by ian-weisser on 2015-10-13
Is the device hardware that udev should be detecting?
Or is it a logical device that you want init to create each time?

---

### Post by Lars Noodén on 2015-10-13
I don't know about udev but when I plug the device in, the system does not find it until I go out of my way to manually create *sr1*.   I'd like to skip that step and have the system handle it automatically.

---

### Post by ian-weisser on 2015-10-13
If you plug hardware in, and the kernel recognizes it, the system will run through it's list of udev rules (/lib/udev and /etc/udev/rules) to do whatever action is specified by the rules to make the hardware work properly.

Perhaps an appropriate udev rule in /etc/udev/rules.d/ is all you need. See [https://wiki.debian.org/udev](https://wiki.debian.org/udev)

---

### Post by Lars Noodén on 2015-10-13
The system recognizes it no problem but only if /dev/sr1 already exists.  Reading through the [udev rules](http://reactivated.net/writing_udev_rules.html) it looks like the device has to exist first, or am I reading it backwards?

---

### Post by ian-weisser on 2015-10-13
The udev rule (including a rule to trigger a script or do another action) should be triggered by the device identification (vendor code, etc)

Example rule:
```
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="7c:dd:90:91:0e:e4", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
```
In this example, the MAC address of the device is the identification. It leads to the same device always being assigned wlan1.

---

### Post by Lars Noodén on 2015-10-15
Thanks.  Though it seems overly complicated.  Can you suggest a udev rule based on the log data below?

The "systemd-udevd[xxxxx]: Failed to apply ACL on /dev/sr1: No such file or directory" errors appear before the device is identified.  

```
Oct 15 14:32:33 foo kernel: [80562.693408] usb 3-3.3: new high-speed USB device number 20 using xhci_hcd
Oct 15 14:32:33 foo kernel: [80562.790150] usb 3-3.3: New USB device found, idVendor=12d1, idProduct=1f01
Oct 15 14:32:33 foo kernel: [80562.790152] usb 3-3.3: New USB device strings: Mfr=2, Product=1, SerialNumber=0
Oct 15 14:32:33 foo kernel: [80562.790154] usb 3-3.3: Product: HUAWEI HiLink
Oct 15 14:32:33 foo kernel: [80562.790154] usb 3-3.3: Manufacturer: HUAWEI
Oct 15 14:32:33 foo kernel: [80562.791652] usb-storage 3-3.3:1.0: USB Mass Storage device detected
Oct 15 14:32:33 foo kernel: [80562.791805] scsi17 : usb-storage 3-3.3:1.0
Oct 15 14:32:34 foo kernel: [80563.791348] scsi 17:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Oct 15 14:32:34 foo kernel: [80563.792448] sr1: scsi-1 drive
Oct 15 14:32:34 foo kernel: [80563.792606] sr 17:0:0:0: Attached scsi CD-ROM sr1
Oct 15 14:32:34 foo kernel: [80563.792680] sr 17:0:0:0: Attached scsi generic sg3 type 5
Oct 15 14:32:34 foo kernel: [80563.837358] Buffer I/O error on device sr1, logical block 16
Oct 15 14:32:34 foo kernel: [80563.837361] Buffer I/O error on device sr1, logical block 16
Oct 15 14:32:34 foo kernel: [80563.837367] Buffer I/O error on device sr1, logical block 16
Oct 15 14:32:34 foo kernel: [80563.837369] Buffer I/O error on device sr1, logical block 16
Oct 15 14:32:34 foo kernel: [80563.837370] Buffer I/O error on device sr1, logical block 16
Oct 15 14:32:34 foo kernel: [80563.837372] Buffer I/O error on device sr1, logical block 8
Oct 15 14:32:34 foo kernel: [80563.837374] Buffer I/O error on device sr1, logical block 8
Oct 15 14:32:34 foo kernel: [80563.837375] Buffer I/O error on device sr1, logical block 8
Oct 15 14:32:34 foo kernel: [80563.837376] Buffer I/O error on device sr1, logical block 8
Oct 15 14:32:34 foo kernel: [80563.838154] systemd-udevd[19932]: Failed to apply ACL on /dev/sr1: No such file or directory
Oct 15 14:32:34 foo kernel: [80563.838158] systemd-udevd[19932]: Failed to apply ACL on /dev/sr1: No such file or directory
Oct 15 14:32:34 foo kernel: [80563.852547] systemd-udevd[19932]: Failed to apply ACL on /dev/sr1: No such file or directory
Oct 15 14:32:34 foo kernel: [80563.852551] systemd-udevd[19932]: Failed to apply ACL on /dev/sr1: No such file or directory


```

The errors go away and the device functions as normal if I have manually created /dev/sr1

---

