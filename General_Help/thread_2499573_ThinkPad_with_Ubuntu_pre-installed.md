---
title: "ThinkPad with Ubuntu pre-installed"
date: 2024-07-31
forum: General Help
---

### Post by Joe_Hallenbeck on 2024-07-31
Has anyone purchased the ThinkPad X1 Carbon with Ubuntu pre-installed? Any issues with the haptic trackpad?

---

### Post by Rubi1200 on 2024-08-06
No and no.

But if you could describe what exactly the problems are someone might be able to offer some help.

---

### Post by clausemery165 on 2024-08-06
Check BIOS/UEFI settings to make sure USB wake-up is enabled. Use lsusb to identify the device, then enable wake-up with:

echo enabled | sudo tee /sys/bus/usb/devices/usbX/power/wakeup

Replace usbX with the correct device ID. Also, check for system and kernel updates that might address the issue.

---

