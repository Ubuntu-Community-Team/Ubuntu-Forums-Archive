---
title: "Suspend Reboots in 13.04 with Radeon HD 6950"
date: 2013-06-13
forum: General Help
---

### Post by TTGRULES on 2013-06-13
I just upgraded to an external Radeon HD 6950 graphics card and installed the proprietary drivers. (The Portal Beta is awesome!) But I can't get my computer to suspend properly. Whenever I try to bring it out of a suspended state (keyboard/power button) It just restarts the machine instead of resuming its previous state. I have played around with my bios settings to see if I can make a difference, but nothing seems to work. Anybody have a clue what's going on? Thanks!

TTGRULES

---

### Post by Toz on 2013-06-13
Is there anything of relevance in your log files (/var/log/pm-suspend.log & /var/log/syslog)? 

There have been some instances in the past of systems rebooting instead of resuming that were fixed by using the **acpi_sleep=nonvs** kernel parameter.

---

