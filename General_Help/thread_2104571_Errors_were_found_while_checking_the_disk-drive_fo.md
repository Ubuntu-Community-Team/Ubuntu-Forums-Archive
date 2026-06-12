---
title: "Errors were found while checking the disk-drive for /"
date: 2013-01-13
forum: General Help
---

### Post by gavinflud on 2013-01-13
Recently, whenever I restart my system I get greeted with this error message when it's booting up:

**Errors were found while checking the disk drive for /**

I then press 'F' to allow Ubuntu to try and fix the problem before getting greeted with another message:

**/tmp is not ready or not present**

This message only stays for a few seconds before my computer boots up successfully. I have read over a few threads with the same problem and have checked the SMART status of my HDD and it evaluated OK with no bad sectors.

Any help or solutions to this problem would be greatly appreciated.

---

### Post by Bashing-om on 2013-01-13
gavinflud; Hi !

Try this;
Boot into recovery mode: hold shift soon as bios splash screen clears -> grub menu
in this menu choose to boot the latest "recovery" kernel; ->choose to fix a broken system (fsck ) when complete -> resume normal boot.

Reboot your machine, does it now boot properly ?
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

