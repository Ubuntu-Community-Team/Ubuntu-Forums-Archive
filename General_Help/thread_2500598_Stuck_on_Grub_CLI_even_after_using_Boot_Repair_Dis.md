---
title: "Stuck on Grub CLI even after using Boot Repair Disk"
date: 2024-09-06
forum: General Help
---

### Post by carlossuated on 2024-09-06
I tried to remove my Linux partition from windows since I had dual boot and wanted more space.
I removed the partition and extended the windows volume but forgot to uninstall grub.
Whenever I start my pc I am directed to the Grub CLI and can’t do anything to exit it, I already tried many solutions with no result, also used boot repair disk which gave me this report: [https://pastebin.ubuntu.com/p/4ntHsg89Hk/](https://pastebin.ubuntu.com/p/4ntHsg89Hk/)

Thank you in advance

---

### Post by yancek on 2024-09-06
You need to get into the BIOS firmware on your HP and go to the Boot Options tab and under UEFI Boot Order, arrow down to OS Boot Manager, hit the Enter key to see the various boot options, highlight the windows entry (Boot0000, hit the F6 key to move it up to first boot priority.  efibootmgr can usually do this also but doesn't usually work on an HP so you need to do it in the BIOS.

---

### Post by oldfred on 2024-09-06
Closed Duplicate.
Do not post same question multiple times.
We all are volunteers and need to know what has already been suggested.

See
[https://ubuntuforums.org/showthread.php?t=2500596](https://ubuntuforums.org/showthread.php?t=2500596)

---

