---
title: "after update-grub it takes two reboots to get the grub menu"
date: 2022-12-29
forum: General Help
---

### Post by sofasurfer on 2022-12-29
When I edit my 40_custom menu I then run update-grub. Next I reboot and hit <shift> expecting the grub menu to appear but instead it goes right to Ubuntu. Then I have to reboot and hit <shift> a second time and THEN the menu comes up. After this the menu always appears after reboot + <shift>. Why two reboots to get menu after 40_custom edit?

---

### Post by oldfred on 2022-12-29
Shift is only for very old BIOS systems.
Do you actually have an UEFI system, but installed in BIOS? 
It may then be settings in UEFI/BIOS have to reset.

---

### Post by sofasurfer on 2022-12-30
I have not installed UEFI and I have no /sys/firmware/efi file.

---

### Post by oldfred on 2022-12-30
But if newer than about 10 years old, it is an UEFI system.
So it may be trying to boot in UEFI mode, sees no UEFI entries and then wants to reboot into BIOS mode.
Once you start booting in one mode, you cannot switch but have to start boot in desired mode for those systems with both modes.
You may have a setting in UEFI/BIOS for default boot mode?
If system is over 10 years old ignore all of above.

---

