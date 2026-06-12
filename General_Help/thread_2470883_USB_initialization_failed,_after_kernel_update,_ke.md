---
title: "USB initialization failed, after kernel update, keyboard &amp; mouse dead"
date: 2022-01-15
forum: General Help
---

### Post by Sami Lehtinen on 2022-01-15
[B]Background:
[/B]After Kernel update the greeter stopped to accept any input. Yet that's caused clearly by USB issue as described earlier.

After manually diffing through the dmesg for both failed and successful login, this is the first difference in dmesg.
[B]
Successful USB init:
[/B]```
[    0.798835] kernel: usb 1-1: new high-speed USB device number 2 using ehci-pci
[    0.814835] kernel: usb 2-1: new high-speed USB device number 2 using ehci-pci
[    0.818837] kernel: usb 3-9: new high-speed USB device number 2 using xhci_hcd
```
[B]Failed USB init:
[/B]```
[    0.802713] kernel: usb 1-1: new high-speed USB device number 2 using ehci-pci
[    0.822691] kernel: usb 2-1: new high-speed USB device number 2 using ehci-pci
```

**Notes:**
What happened tu usb 3-9? That's first indication of any meaningful difference, so it's clearly USB related problem, as assumed earlier. I've had this problem now for a week or so, and I've repeated the steps dozens of times, so it's systematic. Initialization works, if  there's any traffic, like keeping clicking a key during the boot (!). Which should clearly indicated what's pretty clear otherwise, that it's not hardware problem, like connectivity issue. Aso the keyboard and connectors are placed so that pressing the key doesn't affect physical properties of the USB connection.

**lsusb:**
```
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID ####:#### Removed
Bus 004 Device 002: ID 05e3:0612 Genesys Logic, Inc. Hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 003 Device 006: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 007: ID ####:#### Removed 
Bus 003 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 003: ID 04d9:0296 Holtek Semiconductor, Inc. USB-HID Keyboard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
####:####, rare devices, removed for privacy reasons

[B]uname -a:
[/B]Linux bender 5.4.0-94-generic #106-Ubuntu SMP Thu Jan 6 23:58:14 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

[B]Conclusions:
[/B]Motherboard got only two xhci root hubs for devices, one for USB3 and one for rest of USB ports. It seems that initialization of one of the hubs fail.

[B]Questions:
[/B]But this still doesn't explain why, oh why. After  assessing USB-tree, it was clear that keyboard was connected directly  the root hub, and mouse was and is still connected via hub. Yet this  problem did not occur ever before the system update and now it does  occur systemically on every boot. Something with USB init / device init is possibly  broken? - Any pro tips what I should try? 

[B]To-Do:
[/B]I'll try process where I start the system, and unplug the devices and re-plugin during greeter and see if anything changes.

---

### Post by him610 on 2022-01-15
Suggest you begin your investigation by disconnecting all devices including hubs and secret devices from USB except minimum. In your case, keyboard and mouse to see if it boots normally with USB ports properly activated. Follow that up by connecting one additional USB device at a time then reboot until the discrepancy reappears. 
Sometimes things go bad.

---

### Post by tea for one on 2022-01-15
> **Sami Lehtinen said:**
> After Kernel update the greeter stopped to accept any input. Yet that's caused clearly by USB issue as described earlier.

Good advice from [COLOR="#0000FF"]him610[/COLOR] - I would try that first.
Also, have you tried a previous kernel? - kernel updates sometimes bring unexpected problems.

---

### Post by Sami Lehtinen on 2022-02-04
After updating system this week, the problem magically disappeared, just as it magically appeared. - Fixed by magic. ;)

---

