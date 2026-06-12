---
title: "Bluetooth device randomly disappears - Kubuntu 24.04"
date: 2024-08-26
forum: General Help
---

### Post by msmalin on 2024-08-26
Hey all,
I have three devices connected to my PC - a logitech keyboard, a logitech mouse, and my galaxy buds 2 pro headphones.  My headphones will randomly disappear from the bluetooth paired device listing every so often, and there's no apparent rhyme or reason to it.  Sometimes they'll disappear after reboot, or after I click 'disconnect', or after putting them back in the case or switching them to a different device.  I have to re-pair the device whenever it disappears, which is inconvenient when I have a work call about to start up.  This has never happened with my mouse or keyboard.

I have a Framework 16 laptop with a Mediatek bluetooth interface.  This never happened with my old Dell laptop running Kubuntu 22.04.  Not sure if this is related to the bluetooth interface or something different with audio drivers - I read somewhere about audio going to low power mode so maybe that's losing the pairing.  No clue.

Here's the bluetooth info from lshw
```

description: Bluetooth wireless interface
product: Wireless_Device
vendor: MediaTek Inc.
physical id: 5
bus info: usb@1:5
version: 1.00
serial: 000000000
capabilities: usb-2.10 bluetooth
configuration: driver=btusb maxpower=100mA speed=480Mbit/s

```

Uname
```
Linux xxxxx 6.8.0-41-generic #41-Ubuntu SMP PREEMPT_DYNAMIC Fri Aug  2 20:41:06 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux
```

---

