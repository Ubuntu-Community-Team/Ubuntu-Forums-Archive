---
title: "STMicroelectronics USB serial device connection problem on ARM"
date: 2022-08-30
forum: General Help
---

### Post by tmono on 2022-08-30
I have a hardware device that connects to a computer via USB.  It should present as a serial virtual com port.

It's working fine on an intel based laptop.  A serial device is created under /dev when its plugged in.

It's not working on an arm installation (Pi).  The device is recognised when plugged in and shows up with lsusb.  But no device is created under /dev.  lsusb and udevadm say he device is an STMicroelectronics Virtual Serial device.

I'm guessing a driver hasn't been ported to ARM or there is some package I have to install on the ARM device to get it to work - but this is not something I know much about.

Any help/guidance/pointers would be appreciated.

---

### Post by tmono on 2022-08-31
I'm making some progress.  There was a USB driver missing from the system.  A clean OS install seems to fix the problem.

---

