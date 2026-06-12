---
title: "Clash of lspci and my eyes"
date: 2007-07-20
forum: General Help
---

### Post by Majorix on 2007-07-20
When I do an lspci, it tells me that I have 5 usb ports. This surprised me as I am almost certain that I have only 3 usb ports. What can be wrong here?

Here is THAT part from my lsusb:
```
lspci | grep USB
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)

```

EDIT: I have a toshiba m70-215. Anybody with the same laptop can do the same check?

---

### Post by Mr. C. on 2007-07-20
Its says you have 4 and 1 controller.  Your motherboard may have another onboard USB port that isn't accessible or connected.

MrC

---

