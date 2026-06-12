---
title: "No tty* device added when connecting USB device"
date: 2016-05-18
forum: General Help
---

### Post by sportsdude81 on 2016-05-18
Trying to get a diagnostic tool to connect to Ubuntu 14.04.  I added the following file to /etc/udev/rules.d/99-totalphase.rules with 644 permissions owned by root.

```

# This file causes the mode of all Total Phase usb devices to be made
# writable for any user.

# Aarvark I2C/SPI Host Adapter
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0403", SYSFS{idProduct}=="e0d0", MODE="0666"
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0403", ATTR{idProduct}=="e0d0", MODE="0666"

```

lsusb:
```

Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 138a:0010 Validity Sensors, Inc. VFS Fingerprint sensor
Bus 003 Device 004: ID 8087:07da Intel Corp. 
Bus 003 Device 003: ID 04f2:b375 Chicony Electronics Co., Ltd 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0403:e0d0 Future Technology Devices International, Ltd Total Phase Aardvark I2C/SPI Host Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

dmesg:
```

[  953.135214] usb 1-1: new full-speed USB device number 3 using xhci_hcd
[  953.270664] usb 1-1: New USB device found, idVendor=0403, idProduct=e0d0
[  953.270675] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  953.270680] usb 1-1: Product: Aardvark I2C/SPI Host Adapter
[  953.270684] usb 1-1: Manufacturer: Total Phase
[  953.270688] usb 1-1: SerialNumber: TPCFW7nE

```

Ubuntu is not giving it a tty* port.  Any help would be much appreciated.

---

