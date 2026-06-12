---
title: "Need help uninstalling Ubuntu 13.10 with Grub menu from Windows XP computer"
date: 2016-03-16
forum: General Help
---

### Post by Jim-Luc_Kirkard on 2016-03-16
I have it partitioned, and I don't have the recovery disc of Windows XP, and I'm having issues with it and just want it gone. Figured I'd better ask the experts so I don't fry my hard drive, lol. It's a 20GB partition, I believe, and it's Ubuntu 13.10 with GNU Grub 2.0019ubuntu2 if that matters. Any help would be greatly appreciated, thanks.

---

### Post by grahammechanical on 2016-03-16
Do you still have the Ubuntu live DVD/USB memory stick? Load into a Ubuntu live session and install Boot Repair and use that to put a Windows boot loader on to that hard drive. Then when you a loading into XP without using the Grub boot loader you can delete the Ubuntu partitions, Don't forget the swap partition.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Advanced options has a Repair Windows boot files option.

Regards.

---

