---
title: "Shutdown or reboot no longer works with U 12.04"
date: 2013-07-12
forum: General Help
---

### Post by ineuw on 2013-07-12
Volunteering at a seniors' community hall, I replaced Windows XP with Ubuntu 12.04 some months ago as I couldn't keep up with virus related issues. The desktop is an IBM  Pentium 4, 2.66 GHz Processor with 1 GB RAM, it works like a charm and the users love Ubuntu. :-)

After a software update some weeks ago, the OS no longer shuts down, doesn't reboot, and always returns to the login screen. The shutdown or reboot commands work fine in the terminal. It's a single OS system and using the Grub optimizer for convenience, I appended **acpi=force** to the **GRUB_CMDLINE_LINUX_DEFAULT= quiet splash**. This worked once and then the old problem returned. Any help is much appreciated.

---

### Post by ineuw on 2013-07-13
_Answering my own post:_ After searching for possible issues with the standard command options of the GRUB file, I found the problem for this hardware/OS version combination: the GRUB_SAVEDEFAULT was set to = false. 

Changed the value to **= true**, updated the grub file and had to shut off the computer manually. Now, both shutdown and restart function repeatedly.

Note: This may not resolve this same issue with different hardware/OS version combinations.

---

