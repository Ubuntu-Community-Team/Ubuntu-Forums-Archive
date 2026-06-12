---
title: "Shutdown results in reboot (USB Related)"
date: 2013-12-30
forum: General Help
---

### Post by cprofitt on 2013-12-30
I have a Lenovo T530 and have an interesting issue. I am running 13.10. When the laptop is suspended by closing the lid and then resumed by opening the lid it will reboot instead of shutdown. If I suspend from the menu, resume shutting down works as expected.

---- steps to reproduce ----
1.  Suspend by closing the lid
2.  Resume by opening the lid
3.  Try to shutdown computer

Expected behavior - computer shutsdown and powers off.
Actual behavior - computer reboots.

Hoping to get some advice as to what log files to look at in an attempt to solve the issue.

---

### Post by cprofitt on 2013-12-31
Update:

If I initiate a suspend using the menu and resume the laptop by hitting a key on the keyboard it will then shutdown properly.
If I initiate a suspend using the menu, close the laptop lid, open the laptop lid (the machine resumes) it will then reboot instead of shutdown.

I think this isolates the issue to how the opening the lid resumes the computer.

---

### Post by cprofitt on 2013-12-31
One more update:
This issue is related to having an Anker USB 3.0 hub attached to the laptop. The problem does not happen unless the hub is attached.

---

### Post by cprofitt on 2014-01-02
Another update:
I tested some other usb devices in the USB 3.0 ports and they cause the issue was well. I need to do more testing to confirm, but I was hoping that someone could help me understand how a USB device can cause a computer to reboot.

---

