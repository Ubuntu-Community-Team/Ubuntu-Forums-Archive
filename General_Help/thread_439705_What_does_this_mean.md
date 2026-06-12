---
title: "What does this mean?"
date: 2007-05-10
forum: General Help
---

### Post by Dimension7 on 2007-05-10
Whenever I install a K/Ubuntu or PCLinuxOS I always have to include this command on boot option,
"irqpoll pci=noacpi noapic nolapic acpi=off"
otherwise the installation would hang or freeze.

I'm just curious what it means or what it does? And why do my installation freezes without these boot commands?  Is there any installation solution so that I don't have to enter these commands everytime.  I am in the process of comparing different distros to my liking.

Does it have to do with my computer's specs.

My specs:
AMD64 3200+
Chaintech VNF4
1GB memory
40GB hda1 (Windows)
10GB hdb1 (Linux)
160GB sda1 (Storage)

---

### Post by Theimon on 2007-05-12
Apparently you get irq conflicts when you let APIC handle things, and the conflicts make the system freeze. 
A way to not have to typ it anytime you boot is, open a terminal and enter ```
sudo nano /boot/grub/menu.lst
```
Then scroll down to menu entries, find the kernel line and paste those options at the end of the line.
Also look for default options in the same file. Add the options there as well, so when your kernel gets upgraded, it will have those options at the kernel boot line automatically, otherwise you have to edit th efile again and again every time you upgrade the kernel.

---

### Post by Dimension7 on 2007-05-12
Thanks.

---

