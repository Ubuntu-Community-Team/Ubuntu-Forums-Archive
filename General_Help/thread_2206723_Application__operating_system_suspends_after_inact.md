---
title: "Application / operating system suspends after inactivity (ACPI settings?)"
date: 2014-02-20
forum: General Help
---

### Post by caleb5 on 2014-02-20
I am working with Ubuntu 12.04 Server with xorg installed in order create a kiosk to run my application.  All has gone well and generally works as desired with the exception that after a minute or so of keyboard/mouse inactivity the GUI freezes and the network activity stops (ssh sessions are cut off and cannot be reestablished until the computer wakes up).  Once the mouse is moved or keyboard button is pushed everything resumes as desired.  I have observed this behavior on Desktop installations of Ubuntu as well.

I have done some research and experimentation, and it seems that this behavior is related to ACPI.  When I pass the kernel parameter 'acpi=off' in the GRUB_CMDLINE_LINUX_DEFAULT variable, the behavior is not exhibited.  HOWEVER, it also disables my ability to shutdown and power off the computer - it merely halts all operation.

What configuration options are available that will keep the application and operating system responsive AND allow me to power off the computer with a shutdown command?

---

### Post by caleb5 on 2014-02-20
-- UPDATE --

I have continued to look into the kernel parameters, and I wonder if acpi_sleep might have some effect.  There does not seem to be much documentation on this though.  My reference at this point is [here]("https://www.kernel.org/doc/Documentation/kernel-parameters.txt").

---

