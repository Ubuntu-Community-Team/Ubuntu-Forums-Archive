---
title: "Usb device avoid pc sleep status"
date: 2022-04-06
forum: General Help
---

### Post by trics2 on 2022-04-06
Hello,
I discovered that, when my Bose Sound device is connected to usb port (I do it only for charging it), there is an issue when the pc try to enter in sleep status.

This is the output of the lsusb command:
```
Bus 001 Device 092: ID 05a7:40fe Bose Corp. SoundLink Color II speaker
```

And this is the message in syslog when sleep status is activated:
```
Apr  5 16:13:51 Dante kernel: [ 3683.213170] PM: pci_pm_suspend(): hcd_pci_suspend+0x0/0x30 returns -16Apr  5 16:13:51 Dante kernel: [ 3683.213183] PM: dpm_run_callback(): pci_pm_suspend+0x0/0x170 returns -16
Apr  5 16:13:51 Dante kernel: [ 3683.213193] xhci_hcd 0000:00:15.0: PM: failed to suspend async: error -16
Apr  5 16:13:51 Dante kernel: [ 3683.402672] PM: Some devices failed to suspend, or early wake event detected
```

So I decided to create a udeve rule to solve this issue and to permit the sleep status, like that:
```
root@Dante:/home/trics# cat /etc/udev/rules.d/90-disable-usb-bose.rules 
SUBSYSTEM=="usb", ACTION=="add", ATTR{removable}=="removable", ATTR{idVendor}=="05a7", ATTR{idProduct}=="40fe", ATTR{authorized}="0"
```


Unfurtunately this rule creates a loop, the device continues to be logical connected and reconnected in a loop:
```
....Apr  5 16:16:57 Dante kernel: [ 3869.816229] usb 1-1: new full-speed USB device number 98 using xhci_hcd
Apr  5 16:16:57 Dante kernel: [ 3869.968692] usb 1-1: New USB device found, idVendor=05a7, idProduct=40fe, bcdDevice= 1.00
Apr  5 16:16:57 Dante kernel: [ 3869.968710] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Apr  5 16:16:57 Dante kernel: [ 3869.968718] usb 1-1: Product: Bose Color II SoundLink
Apr  5 16:16:57 Dante kernel: [ 3869.968724] usb 1-1: Manufacturer: Bose Corporation
Apr  5 16:16:57 Dante kernel: [ 3869.968729] usb 1-1: SerialNumber: 5203765662K10010
Apr  5 16:16:57 Dante kernel: [ 3869.974452] input: Bose Corporation Bose Color II SoundLink Consumer Control as /devices/pci0000:00/0000:00:15.0/usb1/1-1/1-1:1.0/0003:05A7:40FE.0342/input/input1726
Apr  5 16:16:57 Dante kernel: [ 3870.032584] hid-generic 0003:05A7:40FE.0342: input,hiddev0,hidraw0: USB HID v1.11 Device [Bose Corporation Bose Color II SoundLink] on usb-0000:00:15.0-1/input0
Apr  5 16:16:57 Dante mtp-probe: checking bus 1, device 98: "/sys/devices/pci0000:00/0000:00:15.0/usb1/1-1"
Apr  5 16:16:57 Dante mtp-probe: bus: 1, device: 98 was not an MTP device
Apr  5 16:16:57 Dante mtp-probe: checking bus 1, device 98: "/sys/devices/pci0000:00/0000:00:15.0/usb1/1-1"
Apr  5 16:16:57 Dante mtp-probe: bus: 1, device: 98 was not an MTP device
Apr  5 16:16:57 Dante acpid: input device has been disconnected, fd 22
Apr  5 16:16:57 Dante kernel: [ 3870.107687] usb 1-1: USB disconnect, device number 98
Apr  5 16:16:57 Dante Thunar[275514]: thunar-volman: There is no device with the sysfs path "/sys/devices/pci0000:00/0000:00:15.0/usb1/1-1".
Apr  5 16:16:58 Dante kernel: [ 3870.492225] usb 1-1: new full-speed USB device number 99 using xhci_hcd
Apr  5 16:16:58 Dante kernel: [ 3870.648694] usb 1-1: New USB device found, idVendor=05a7, idProduct=40fe, bcdDevice= 1.00
Apr  5 16:16:58 Dante kernel: [ 3870.648712] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Apr  5 16:16:58 Dante kernel: [ 3870.648720] usb 1-1: Product: Bose Color II SoundLink
Apr  5 16:16:58 Dante kernel: [ 3870.648726] usb 1-1: Manufacturer: Bose Corporation
Apr  5 16:16:58 Dante kernel: [ 3870.648732] usb 1-1: SerialNumber: 5203765662K10010
Apr  5 16:16:58 Dante kernel: [ 3870.653901] input: Bose Corporation Bose Color II SoundLink Consumer Control as /devices/pci0000:00/0000:00:15.0/usb1/1-1/1-1:1.0/0003:05A7:40FE.0343/input/input1728
Apr  5 16:16:58 Dante kernel: [ 3870.712524] hid-generic 0003:05A7:40FE.0343: input,hiddev0,hidraw0: USB HID v1.11 Device [Bose Corporation Bose Color II SoundLink] on usb-0000:00:15.0-1/input0
Apr  5 16:16:58 Dante mtp-probe: checking bus 1, device 99: "/sys/devices/pci0000:00/0000:00:15.0/usb1/1-1"
Apr  5 16:16:58 Dante mtp-probe: bus: 1, device: 99 was not an MTP device
Apr  5 16:16:58 Dante mtp-probe: checking bus 1, device 99: "/sys/devices/pci0000:00/0000:00:15.0/usb1/1-1"
Apr  5 16:16:58 Dante mtp-probe: bus: 1, device: 99 was not an MTP device
......
```

Do you have any suggestion to solve this issue?

---

### Post by him610 on 2022-04-06
You could charge your device with an AC adapter (probably came in the same box.)

---

### Post by trics2 on 2022-04-07
Brilliant, tell the true, you are Linus Torvalds undercover :P; really I need a software solution!

Anyway thank you for the suggestion.

---

### Post by him610 on 2022-04-07
Oftentimes the most obvious is not obvious to all.

Added: After giving your issue some thought, have you considered using a powered USB hub between your PC and you Bose SoundLink? 
That way maybe the current draw would originate from the USB hub instead of the PC.
It is not a clean solution though because it requires three wires (PC to hub, hub to power source, hub to SoundLink.)

---

### Post by trics2 on 2022-04-08
Yes, but it is not possible to add other hardware (as you told 'cause not a clean solution and not for power saving).
For this I tryed to "mask" the usb device trought udev rules without success. 

For my understanding, do you know why not enought current would't allow the suspension state?

Thanks a lot,

---

