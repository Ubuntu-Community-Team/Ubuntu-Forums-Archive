---
title: "USB keyboard and mouse dont work after upgrade to 22.04"
date: 2023-07-31
forum: General Help
---

### Post by sachithnalaka on 2023-07-31
Today I upgraded from 20.04 to 22.04. There were no errors in upgrade process and rebooted.

When I logged into Ubuntu I can insert my password to gnome using my usb-keyboard and mouse pointer also working. But after few seconds both stop working (specially after desktop is loaded)

`lsusb` shows

> Bus 001 Device 003: ID 413c:2113 Dell Computer Corp. KB216 Wired Keyboard<br>
> Bus 001 Device 002: ID 413c:250e Dell Computer Corp. Dell Laser Mouse MS3220

In journel logs :

```
kernel: input: input-remapper mouse as /devices/virtual/input/input34
kernel: input: input-remapper Dell Computer Corp Dell Laser Mouse MS3220 forwarded as /devices/virtual/input/input35
kernel: sd 0:0:0:0: [sda] Synchronizing SCSI cache
kernel: sd 0:0:0:0: [sda] Stopping disk
kernel: xhci_hcd 0000:05:00.3: WARNING: Host System Error
kernel: hid-generic 0003:413C:2113.0005: usb_submit_urb(ctrl) failed: -19
kernel: hid-generic 0003:413C:2113.0005: usb_submit_urb(ctrl) failed: -19
kernel: Bluetooth: hci0: command 0x0c03 tx timeout
kernel: Bluetooth: hci0: HCI reset during shutdown failed
kernel: xhci_hcd 0000:05:00.4: xHCI host not responding to stop endpoint command.
kernel: xhci_hcd 0000:05:00.4: USBSTS: 0x00000015 HCHalted HSE PCD
kernel: xhci_hcd 0000:05:00.4: xHCI host controller not responding, assume dead
kernel: xhci_hcd 0000:05:00.4: HC died; cleaning up
kernel: usb 3-1: USB disconnect, device number 2
kernel: usb 3-1.1: USB disconnect, device number 4
kernel: usb 3-2: USB disconnect, device number 3
```

`sudo ubuntu-drivers autoinstall` - > All the available drivers are already installed.

[Here]([https://askubuntu.com/questions/1461375/mouse-and-keyboard-not-working-in-ubuntu-22-04](https://askubuntu.com/questions/1461375/mouse-and-keyboard-not-working-in-ubuntu-22-04)) still no proper answer.

[nvidia graphic]([https://askubuntu.com/questions/1460916/why-are-keyboard-mouse-not-responding-after-being-suspended-ubuntu-22-04](https://askubuntu.com/questions/1460916/why-are-keyboard-mouse-not-responding-after-being-suspended-ubuntu-22-04)) issue is not related to me as I use AMD.

[Here no clear answer for this issue]([https://www.reddit.com/r/Ubuntu/comments/vp9h0n/mouse_any_maybe_keyboard_not_working_on_fresh/](https://www.reddit.com/r/Ubuntu/comments/vp9h0n/mouse_any_maybe_keyboard_not_working_on_fresh/))

[x-server is in latest version]([https://askubuntu.com/questions/1296619/ubuntu-usb-keyboard-and-mouse-driver-fail-after-upgrade](https://askubuntu.com/questions/1296619/ubuntu-usb-keyboard-and-mouse-driver-fail-after-upgrade))

---

### Post by sachithnalaka on 2023-08-01
I kind of solved my issue after stopping TLP service. I disabled it and rebooted. It solved my issue.

---

