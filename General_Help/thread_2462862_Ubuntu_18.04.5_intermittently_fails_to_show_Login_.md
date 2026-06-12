---
title: "Ubuntu 18.04.5 intermittently fails to show Login Screen on ASUS X456U laptop"
date: 2021-05-28
forum: General Help
---

### Post by frankiefong2 on 2021-05-28
Hello,

I recently ran into this problem with my laptop. And would like to see if any fellow member seeing this also.

Laptop: ASUS X456U
Ubuntu: 18.04.5 (Dual-Boot with Windows-10)
Local changes: Added pci=noaer to linux boot command-line (grub)
Problem: 

Laptop Boots up and shows Grub menu. Selects 'Ubuntu' and it would show the 'burgundy color' screen. After a few seconds, the activity LED turned off. And the laptop remains in this state forever. This happens half the time. In the case where it works, it will flash to a black console screen with the error messages below for a few seconds. Then move on to the expected graphical login screen. And things are normal.

The 'error message' that appears momentarily:

[ timestamp-1] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed4000 f80
[ timestamp-2] tpm_crb MSFT0101:00: [Firmware Bug]: ACPI region does not cover the entire command/response buffer. [mem 0xfed40000-0xfed4087f flags 0x200] vs fed4000 f80
/dev/sda6: clean, 169169/25755648 files, 6980015/103014400 blocks.

---

