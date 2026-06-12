---
title: "Help troubleshooting Kernel Panics"
date: 2008-06-23
forum: General Help
---

### Post by ByKeLaO on 2008-06-23
Hello there.
I'm having sleep/resume problems on my computer, namely I get a Kernel Panic every 1/5 or so times I resume from standby mode. The panic does not even get logged, so I can't provide much info other than the contents of /var/messages leading up to the panic:

Jun 23 17:39:03 james-desktop kernel: [ 3379.204949] ACPI: PCI interrupt for device 0000:05:04.0 disabled
Jun 23 17:39:03 james-desktop kernel: [ 3379.249911] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Jun 23 17:39:03 james-desktop kernel: [ 3379.263795] usbcore: deregistering interface driver ndiswrapper
Jun 23 17:39:04 james-desktop kernel: [ 3380.004760] ndiswrapper: device wlan0 removed <-- I put the computer to sleep at this point
Jun 23 19:08:04 james-desktop syslogd 1.5.0#1ubuntu1: restart. <-- The kernel panic happens just before this entry

I have sleep/resume problems on Windows as well, and so I believe this must be a hardware problem. How can I find out some more info about what's causing these problems, so I can replace the dodgy hardware?

---

