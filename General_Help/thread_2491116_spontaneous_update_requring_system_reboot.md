---
title: "spontaneous update requring system reboot"
date: 2023-09-26
forum: General Help
---

### Post by dwlamb on 2023-09-26
I run my system 24/7.  Occasionally, once maybe up to three times per year, I sit down at my machine to discover the System Notification Helper in the system tray signifying the system requires a reboot.  How does this occur when I have not carried out a system update?  There was no indication in the previous 8 hours of a system update available and I have not carried out a sudo command to update or install a package.  

It is as though an update has been pushed onto the system without my sudo permission.

---

### Post by ian-weisser on 2023-09-26
Unattended Upgrades has been pushing security updates, including security-related kernel updates that require a reboot, for over a decade.

The current iteration of UU checks twice each day.

Automatic security updates is a very popular feature of Ubuntu.

---

### Post by dwlamb on 2023-09-26
Thanks for the explanation.

---

