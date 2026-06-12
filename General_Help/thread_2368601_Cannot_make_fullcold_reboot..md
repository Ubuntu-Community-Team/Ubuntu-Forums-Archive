---
title: "Cannot make full/cold reboot."
date: 2017-08-12
forum: General Help
---

### Post by sotiris2 on 2017-08-12
I have a strange issue, whenever i try to restart my PC (either via GUI or CLI) I do not get a normal reboot (i.e. getting POST messages) but rather very quickly get dropped to the login screen.


In fact I initially thought that Xorg was maybe crashing but I after I checked the logs it appears that a kernel actually boots (there are entries with 0.00 timestamps for example). Furthermore I booted the oldest available kernel (4.4.0-42) and upon restarting it restarted to the newest available kernel (4.4.0-91). I also got to see a message on screen, kexec: starting new kernel.

This makes me thing that it probably is some kind of configurable behavior and not a bug.

The system is Ubuntu 16.04.02 in an efi installation. There is a win 10 installation on another disk (it reboots to post normally). Fast/Secure boot etc are disabled in uefi settings.
I don't have any issue in shutting down the machine or booting it. 

The hardware is Athlon 860k on Asus A88XM-PLUS. I have an amd rx480 using the amdgpu driver.

And here are [kernlog](http://pastebin.ubuntu.com/25300158/) and [syslog](http://pastebin.ubuntu.com/25300180/) both start seconds before I tried to restart the machine (I emptied the logs).

It is not a critical problem since I can just shutdown the machine but it makes me curious. Unfortunately I can't tell how long it has been like this.

Any  help is appreciated.

---

### Post by DuckHook on 2017-08-12
The linux kernel has some arcane ACPI settings that may set your HW to skip the POST sequence in the event of a soft reboot (one that does not involve a power-down). Unfortunately, I do not know the ACPI call offhand. Some of my machines act the same way; others don't. I've always considered it a "feature", and since I feel that the POST routine only needs to be invoked once at power-up, I feel the time savings to be a convenience and therefore have never been bothered to delve into the guts of it.

---

