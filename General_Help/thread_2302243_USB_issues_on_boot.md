---
title: "USB issues on boot"
date: 2015-11-08
forum: General Help
---

### Post by solitudefields on 2015-11-08
I've been having issues with USB devices since the 3.18 kernel where the keyboard and mouse don't work correctly for 30 seconds or so until it finally initializes. When I reboot the keyboard and mouse don't function (UEFI BIOS stays on code 99) which forces me to clear CMOS to fix it. I've tried everything to fix it - changing keyboard, mouse and USB DAC, changing motherboard, unhooking all USB headers, clean Ubuntu installs, using newer kernels, etc. The last kernel which works best for me is 3.17 however I can't continue using it. Anyways looking in dmesg I get the following;

```
[   11.225438] usb 1-3: device descriptor read/all, error -110
[   11.337524] usb 1-3: new high-speed USB device number 3 using xhci_hcd
[   21.480411] usb 1-3: device descriptor read/all, error -110
[   21.592532] usb 1-3: new high-speed USB device number 4 using xhci_hcd
[   26.615914] usb 1-3: device descriptor read/8, error -110
[   31.743439] usb 1-3: device descriptor read/8, error -110
[   31.959689] usb 1-3: new high-speed USB device number 5 using xhci_hcd
[   36.983086] usb 1-3: device descriptor read/8, error -110
[   42.110574] usb 1-3: device descriptor read/8, error -110
[   42.214694] usb usb1-port3: unable to enumerate USB device
```

Oh boy, the dreaded device descriptor read error only on usb 1-3. So, I ran lsusb and here's my output;

```
Bus 006 Device 002: ID 8087:8001 Intel Corp. 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 8087:8009 Intel Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 002 Device 002: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 010: ID 8087:07dc Intel Corp. 
Bus 001 Device 008: ID 0d8c:0319 C-Media Electronics, Inc. 
Bus 001 Device 014: ID 1532:011a Razer USA, Ltd 
Bus 001 Device 013: ID 046d:c07d Logitech, Inc. 
Bus 001 Device 009: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 007: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 001 Device 006: ID 174c:2074 ASMedia Technology Inc. ASM1074 High-Speed hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

So, which one is the troublesome device? Bus 003 Device 001 (Linux Foundation 2.0 root hub)? Bus 002 Device 003 or Bus 002 Device 002 (ASMedia Technology Inc. ASM1074 SuperSpeed hub)? Something else?

I'm wondering if I can fully disable usb 1-3 to avoid this issue. How would I proceed to do this?

P.S. I'm in a dual boot with Windows 10, but I've fully disconnected the SSD it's installed on and just used straight Ubuntu but the result is the same.

---

