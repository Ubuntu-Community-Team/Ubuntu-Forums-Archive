---
title: "[SOLVED] Wubi Error"
date: 2008-03-02
forum: General Help
---

### Post by samitharansara on 2008-03-02
Wubi gives me an error while installing inside windows. It makes the CD image and virtual disks. When I select Ubuntu from NT bootloader, the computer installs Ubuntu. But after some time it gives me an error. I did this several times. But It says that "Error, Installation cannot continue, your system will be reboot now". 

What is the reason?

System Configuration

3GHz Intel HT
512 DDR RAM 400MHz
Intel 945GV Chipset
80 GB HDD (Free space of the selected drive 20 GB)

Thanks a lot.
samitha
:confused:

---

### Post by ago on 2008-03-02
At the moment there are some issues with migration-assistant triggrering a failure_command, [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/195905](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/195905)

Open up the zipped logs in /ubuntu/ (will only be there if you used wubi 440+) and look at the bootom of var/log/syslog. If it mentions migration-assistant it is probable the same issue above.

---

