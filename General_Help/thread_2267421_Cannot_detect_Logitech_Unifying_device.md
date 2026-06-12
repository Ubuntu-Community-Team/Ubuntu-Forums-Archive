---
title: "Cannot detect Logitech Unifying device"
date: 2015-03-01
forum: General Help
---

### Post by CkDGTAT on 2015-03-01
Hi,

How can I guess the device name of my Logitech Unifying device?

```
% lsusb Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b2da Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```

Thank you

---

### Post by gifford on 2015-03-01
It does not look like it is listed.
This is how it appears on my system.
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver

---

### Post by CkDGTAT on 2015-03-01
Is it a hardware problem? Should I replace the Unifying reciever?

---

### Post by Mike_Walsh on 2015-03-01
What happens if you remove the receiver, re-boot, then plug the receiver back in, and run 'lsusb' again? I use a ZoneTouch T400 mouse, and mine lists as follows:-

```
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
```

Regards,

Mike.

---

### Post by CkDGTAT on 2015-03-02
No change

---

### Post by efflandt on 2015-03-03
Apparently yours is not working (try a different USB port, maybe USB port is bad or deactivated in BIOS).```
efflandt@XPS-8100-1404:~$ lsusb | grep -i logitech
Bus 002 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 004: ID 046d:c21f Logitech, Inc. F710 Wireless Gamepad [XInput Mode]
```

---

