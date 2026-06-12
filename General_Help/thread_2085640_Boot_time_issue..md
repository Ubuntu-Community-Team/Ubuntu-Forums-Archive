---
title: "Boot time issue."
date: 2012-11-18
forum: General Help
---

### Post by atari314 on 2012-11-18
Hello, does anyone know why the kernel is waiting 15s here?

```
[    1.740912] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    2.016306] firewire_core: created device fw0: GUID 001d4ffffe825f7a, S400
[    2.108117] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[    2.528107] usb 3-2: new low-speed USB device number 3 using uhci_hcd
[    2.952115] usb 5-1: new low-speed USB device number 2 using uhci_hcd
[    3.360144] usb 7-1: new low-speed USB device number 2 using uhci_hcd
[    3.788130] usb 7-2: new full-speed USB device number 3 using uhci_hcd
[   18.148495] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.172468] udevd[319]: starting version 175
[   18.242344] lp: driver loaded but no devices found
[   18.268854] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
```[http://pastebin.com/4r2AhGg4](http://pastebin.com/4r2AhGg4)

 I've blacklisted my ethernet module on a previous test, but it's still waiting 10s for something.

Bootchart: [http://i.imgur.com/6hY4j.png](http://i.imgur.com/6hY4j.png)

Ideas?

---

