---
title: "linux partition help"
date: 2008-02-15
forum: General Help
---

### Post by rcarm on 2008-02-15
i'm trying to merge 4 partitions and install linux there but i'm scared that i may wipe out grub. i recently installed ubuntu but i noticed that it didn't install gnome so i'm trying to reinstall it and i can't apt get it because this thing doesn't have an ethernet port and i'm using a wireless usb adapter. here's my how my partition looks like

1 - Windows XP NTFS - 5.5gb (boot) C:
2 - ubuntu(without gnome) - ext3 - 3.25gb
3 - linux swap - 250mb
4 - unallocated - 3mb
5 - Windows Server 2003 (don't ask) NTFS 4gb F:

so i'm trying to merge 2, 3, 4, and 5 using acronis disk director suite (i can't use qparted or parted magic because this thing doesn't support usb boot and i don't have a blank cd). So here are my questions.

1. will it screw up grub? because i'm not sure if it's installed in C: or the ubuntu partition. and will i still be able to boot into xp cause i can't anymore with 2003.

2. if i partition a linux swap before i install ubuntu, will ubuntu use it?

3. will this work?

---

