---
title: "Power management in kubuntu 6.10"
date: 2006-11-29
forum: General Help
---

### Post by HW_Hack on 2006-11-29
I've just installed kubuntu 6.10 and am looking for basic power managment support. I'm running on a newer Intel motherboard that supported hibernate on SUSE 10.1. Under System settings I get a battery icon - but under the tab Power Control I get the message 

Your computer seems to have a partial ACPI installation. ACPI was probably enabled, but some of the sub-options were not - you need to enable at least 'AC Adaptor' and 'Control Method Battery' and then rebuild your kernel.

I ran the adept app and installed the acpi modules and rebooted. 

I get the following in terminal mode:

henry@Caddis-Fly:~$ sudo aptitude search acpi
Password:
i   acpi                            - displays information on ACPI devices
i   acpi-support                    - a collection of useful events for acpi
i   acpid                           - Utilities for using ACPI power management
henry@Caddis-Fly:~$


So whats up -- do I need load other modules ??????](*,)

---

