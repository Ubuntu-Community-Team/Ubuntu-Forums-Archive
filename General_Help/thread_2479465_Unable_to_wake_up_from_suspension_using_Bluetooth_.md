---
title: "Unable to wake up from suspension using Bluetooth keyboard"
date: 2022-09-25
forum: General Help
---

### Post by zeegeek on 2022-09-25
I'm using Xubuntu 22.04 on Intel NUC11PAHi5 with Bluetooth keyboard and mouse. The NUC supports waking up from Bluetooth devices according to the technical specifications. However, whenever I put the computer to sleep, Bluetooth seems to be turned off because the keyboard LED indicates it's lost connection. Pressing keys on the keyboard won't wake the computer up. I have tried using the following udev rule to keep power on on the Bluetooth adapter with no luck. Is there any way to wake up from Bluetooth devices?

```
SUBSYSTEM=="usb", ATTRS{idVendor}=="8087", ATTRS{idProduct}=="0026" RUN+="/bin/sh -c 'echo enabled > /sys$env{DEVPATH}/../power/wakeup;'"
```

Here's my lsusb output.

```
Bus 003 Device 004: ID 8087:0026 Intel Corp. AX201 Bluetooth
```

```

$ grep . /sys/bus/usb/devices/*/power/wakeup

/sys/bus/usb/devices/3-10/power/wakeup:enabled
/sys/bus/usb/devices/3-3/power/wakeup:enabled
/sys/bus/usb/devices/usb1/power/wakeup:disabled
/sys/bus/usb/devices/usb2/power/wakeup:disabled
/sys/bus/usb/devices/usb3/power/wakeup:enabled
/sys/bus/usb/devices/usb4/power/wakeup:disabled

```

---

