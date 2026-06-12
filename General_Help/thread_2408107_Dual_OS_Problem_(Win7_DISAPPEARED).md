---
title: "Dual OS Problem (Win7 DISAPPEARED)"
date: 2018-12-13
forum: General Help
---

### Post by sergi011 on 2018-12-13
Hello everyone,

I recently installed Ubuntu 18.04 LTS, and now want to go back to windows.
i had the following problems:

1.At start Ubuntu loads automatically
2. WIndows 7 does not show anywhere on bios but if i check my partitions on Ubuntu all my windows files and documents are there.
3. If i change the boot priority and reboot sometime i have the option of start ubuntu normally, start ubuntu on safe mode (?) and system settings. last option takes me to bios menu.

I've already reinstalled Ubuntu 3 times, one time i manage to boot windows( i dont know how) and delete ubuntu partitions but then when i rebooted i couldnt load windows 7, so i managed to install ubuntu again.

Please somebody help me i want to load windows again or at least have the option to choose wich OS to boot at start.

sorry for my englsh

---

### Post by freemedia2018 on 2018-12-13
You could try running:

```
sudo update-grub
```

And that might add Windows to your boot menu.

---

### Post by oldfred on 2018-12-13
Do you have Windows repair flash drive?
That would be best, and you always should have current version repair/recovery/live flash drive  for every system you have installed.

Boot-Repair is primarily for Linux systems, but can do a few minor fixes to Windows like install a Windows type boot loader (not Windows version) to MBR, if that is all that is required. You may need boot flag (make active in Windows repairs) on the primary NTFS partition with the Windows boot files.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

