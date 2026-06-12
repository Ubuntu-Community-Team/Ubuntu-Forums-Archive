---
title: "Asus S200e touchscreen make compiz crash"
date: 2013-09-23
forum: General Help
---

### Post by tamanti on 2013-09-23
I've got Ubuntu desktop 13.04, but the same issue was while testing 12.04 live.

Sometime the touchscreen works without problems for some hours. Other times I have a crush of compiz about every minute.

syslog loops this message (touchscreen working or not):

```

Sep 22 01:55:25 tama-X202E kernel: [37699.050537] usb 1-1.3: new full-speed USB device number 26 using ehci-pci
Sep 22 01:55:25 tama-X202E kernel: [37699.229679] usb 1-1.3: not running at top speed; connect to a high speed hub
Sep 22 01:55:25 tama-X202E kernel: [37699.644848] usb 1-1.3: New USB device found, idVendor=0457, idProduct=1013
Sep 22 01:55:25 tama-X202E kernel: [37699.644863] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 22 01:55:25 tama-X202E kernel: [37699.644872] usb 1-1.3: Product: SiS HID Touch Controller
Sep 22 01:55:25 tama-X202E kernel: [37699.644880] usb 1-1.3: Manufacturer: USBest Technology
Sep 22 01:55:25 tama-X202E kernel: [37699.730710] input: USBest Technology SiS HID Touch Controller as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input519
Sep 22 01:55:25 tama-X202E kernel: [37699.731479] hid-multitouch 0003:0457:1013.01FE: input,hiddev0,hidraw0: USB HID v1.00 Device [USBest Technology SiS HID Touch Controller] on usb-0000:00:1a.0-1.3/input0
Sep 22 01:55:25 tama-X202E kernel: [37699.731806] usb 1-1.3: USB disconnect, device number 26
Sep 22 01:55:25 tama-X202E mtp-probe: checking bus 1, device 26: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3"
Sep 22 01:55:25 tama-X202E mtp-probe: bus: 1, device: 26 was not an MTP device

```

Every second I've a loop with a new device number.

I found how to avoid compiz crashes by disabling touchscreen:
```
sudo rmmod hid_multitouch
```

Or better, doing it at boot time:
```
sudo echo "blacklist hid_multitouch" > /etc/modprobe.d/blacklist-hid_multitouch.conf
```


I'd like to find a way to fix the touchscreen feature, but in the meantime I'll do without it. Under Windows 8 I haven't found any problem to use it.

Searching on the net I found another similar problem here, where I posted my partial solution:
[http://forum.ubuntu-fr.org/viewtopic.php?pid=14722361](http://forum.ubuntu-fr.org/viewtopic.php?pid=14722361)

---

### Post by gordintoronto on 2013-09-24
This is the kind of issue which should be fixed by the next release, 13.10. It's 24 days away.

---

### Post by Kuka_Vaan on 2013-10-09
Meanwhile this should work:

Add the following line to file /etc/modprobe.d/usbhid.conf (create if necessary):
 [COLOR=#333333][FONT=Ubuntu Mono]options usbhid quirks=[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]0x0457:[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]0x1013:[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]0x20000000[/FONT][/COLOR]
Then run:
[COLOR=#333333][FONT=Ubuntu Mono] sudo update-initramfs -u[/FONT][/COLOR]
After this reboot and the touchscreen should work! This solution was copied from [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1180881](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1180881)[COLOR=#333333][FONT=Ubuntu Mono]


[/FONT][/COLOR]

---

### Post by timswait on 2013-12-25
I've got an Asus S200e, but the touchscreen doesn't work at all for multi touches, it only recognises single touches. tamanti, Did you have to do something to set it up for multitouch, or does yours only do single touches anyway? I'm running 13.10 on it now, so hopefully the crashing won't be a problem if I do get it set up.

---

