---
title: "Mouse unresponsive only through Thunderbolt monitor"
date: 2019-04-17
forum: General Help
---

### Post by asandhu on 2019-04-17
I'm having an issue with a mouse connected through the USB hub on a LG Ultrawide monitor (connected via Thunderbolt). The mouse seems to get recognized by the OS, however it is completely unresponsive. When it is connected directly to a USB port on the laptop it works as expected.
Also, a keyboard that I have connected to the same monitor works fine through Thunderbolt, just the mouse seems to be an issue. Tried another mouse and that also did not work through the monitor.
Heres dmesg output when connecting the mouse directly to the laptop:

```
[ 1407.076318] usb 1-2: new full-speed USB device number 6 using xhci_hcd
[ 1407.235219] usb 1-2: New USB device found, idVendor=1b1c, idProduct=1b2e, bcdDevice= 3.06
[ 1407.235223] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1407.235226] usb 1-2: Product: Corsair Gaming M65 Pro RGB Mouse
[ 1407.235228] usb 1-2: Manufacturer: Corsair
[ 1407.235230] usb 1-2: SerialNumber: 11033025AEBE8461563A6BB1F5001946
[ 1407.243832] input: Corsair Corsair Gaming M65 Pro RGB Mouse Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/0003:1B1C:1B2E.0008/input/input34
[ 1407.304888] input: Corsair Corsair Gaming M65 Pro RGB Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/0003:1B1C:1B2E.0008/input/input35
[ 1407.305138] input: Corsair Corsair Gaming M65 Pro RGB Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/0003:1B1C:1B2E.0008/input/input36
[ 1407.305705] hid-generic 0003:1B1C:1B2E.0008: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Corsair Corsair Gaming M65 Pro RGB Mouse] on usb-0000:00:14.0-2/input0
[ 1407.308730] hid-generic 0003:1B1C:1B2E.0009: hiddev1,hidraw2: USB HID v1.11 Device [Corsair Corsair Gaming M65 Pro RGB Mouse] on usb-0000:00:14.0-2/input1
```

And dmesg when connecting to monitor:

```
[ 1486.770993] usb 5-1.4: TI USB 3410 1 port adapter converter now attached to ttyUSB0
[ 1493.213067] usb 5-1.3: new full-speed USB device number 75 using xhci_hcd
[ 1493.451372] usb 5-1.3: New USB device found, idVendor=1b1c, idProduct=1b2e, bcdDevice= 3.06
[ 1493.451376] usb 5-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1493.451379] usb 5-1.3: Product: Corsair Gaming M65 Pro RGB Mouse
[ 1493.451381] usb 5-1.3: Manufacturer: Corsair
[ 1493.451383] usb 5-1.3: SerialNumber: 11033025AEBE8461563A6BB1F5001946
[ 1493.467629] input: Corsair Corsair Gaming M65 Pro RGB Mouse Mouse as /devices/pci0000:00/0000:00:1b.0/0000:02:00.0/0000:03:01.0/0000:05:00.0/0000:06:03.0/0000:07:00.0/usb5/5-1/5-1.3/5-1.3:1.0/0003:1B1C:1B2E.000A/input/input37
[ 1493.525407] input: Corsair Corsair Gaming M65 Pro RGB Mouse as /devices/pci0000:00/0000:00:1b.0/0000:02:00.0/0000:03:01.0/0000:05:00.0/0000:06:03.0/0000:07:00.0/usb5/5-1/5-1.3/5-1.3:1.0/0003:1B1C:1B2E.000A/input/input38
[ 1493.525674] input: Corsair Corsair Gaming M65 Pro RGB Mouse as /devices/pci0000:00/0000:00:1b.0/0000:02:00.0/0000:03:01.0/0000:05:00.0/0000:06:03.0/0000:07:00.0/usb5/5-1/5-1.3/5-1.3:1.0/0003:1B1C:1B2E.000A/input/input39
[ 1493.526266] hid-generic 0003:1B1C:1B2E.000A: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Corsair Corsair Gaming M65 Pro RGB Mouse] on usb-0000:07:00.0-1.3/input0
[ 1493.529752] hid-generic 0003:1B1C:1B2E.000B: hiddev1,hidraw2: USB HID v1.11 Device [Corsair Corsair Gaming M65 Pro RGB Mouse] on usb-0000:07:00.0-1.3/input1
```

The only difference I can spot is in the input: ... lines. Xorg seems to recognize the mouse in both scenarios.

Any ideas?

---

