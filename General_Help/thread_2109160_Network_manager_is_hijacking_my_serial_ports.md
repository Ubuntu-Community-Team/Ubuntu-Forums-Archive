---
title: "Network manager is hijacking my serial ports"
date: 2013-01-26
forum: General Help
---

### Post by kleptophobiac on 2013-01-26
I'm trying to set up some scripts to run test equipment in my lab. Some of the hardware connects via RS232 through a USB to serial adapter.

As soon as I plug in the adapter into my Ubuntu 12.04 machine my test equipment goes nuts due to junk coming out from my computer.

[This looks like a relevant bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/708231") but it got marked as a duplicate of a bug that doesn't make sense to me. Disabling Network Manager seems to prevent the serial problem, but isn't a realistic workaround.

How do I prevent Network Manager from trying to be too helpful?

Thanks,
Sasha

---

### Post by steeldriver on 2013-01-26
I have no direct knowledge of this but I followed the link to the supposedly duplicate bug report and there's a suggested workaround using a udev rule to set ENV{ID_MM_DEVICE_IGNORE}="1" for serial usb devices - maybe that will work for you?

---

