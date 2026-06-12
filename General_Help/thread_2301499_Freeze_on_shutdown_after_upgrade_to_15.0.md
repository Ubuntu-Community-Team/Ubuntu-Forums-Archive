---
title: "Freeze on shutdown after upgrade to 15.0"
date: 2015-11-02
forum: General Help
---

### Post by odror on 2015-11-02
After upgrading to 15.10 (on new hardware) my system freezes on shutdown. When I press Esc during the shutdown. I do not get any additional messages.

in /etc/default/grub I have:

GRUB_CMDLINE_LINUX_DEFAULT=""

I still do not see any messages and cannot tell why the system freezes.

Even CTRL+ATL+DEL does not force reboot.

Any Ideas how I can tell what is holding the shutdown/reboot process.

Thanks

---

### Post by john475 on 2015-11-05
I am having this same problem only my system freezes on startup, I am able to force shutdown by holding power button and turning on again then selecting ubuntu in the pre-login startup screen from the BIOS.

---

### Post by odror on 2015-11-05
I suspect that my issues is related to USB. Because at the same time when I type lsusb it freezes. I have removed USB devices. It was working fine, but then after an hour or so. I get the USB freeze again. Many of the USB devices(even during the freeze) are working fine. for example the keyboard and mouse. At least two are not working during the freeze, but removing them does not solve the problem. I have tried USB2.0 and USB 3.0 ports. Did not solve the problem.

I have an MSI X99S MB with USB2.0, USB3.0 and USB3.1 ports. I avoid the USB 3.1 port. I am not sure that it is supported. I also have an Old PCI-E card with 2 USB3.0 ports.

---

