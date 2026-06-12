---
title: "WMware - XP emulation??"
date: 2007-01-18
forum: General Help
---

### Post by icehammer on 2007-01-18
i installed XP on VMware, running Ubuntu Edgy.. While it was a smooth install, i don't see my other drives in windows..

So i added "a physical drive to a virtual drive" and i was told that i don't have enough permissions to do so. so i made myself a root by using ```
sudo -i
```, and tried again.. this time i could mount the drives, but when i powered on Windows, i was again told that i don't have permissions..

I'm a newbie, so pl give me detailed info on how to do so...

Case II >> if i forget emulation, and install windows for a dual-boot, is it necessary that windows be installed first?? means, will i have to format this copy of linux, install windows, and install linux again if i need to go in for a double boot??


Thanks..

---

### Post by andreas64 on 2007-01-18
Hi,

Case 1:
what do you mean with "other drives" ?

Case 2:
No, but if you don't install Windows first, you have to reinstall and reconfigure grub because Windows will override the mbr of your harddisk.

Andreas

---

### Post by icehammer on 2007-01-18
i got 9 partitions on my PC, [ 2 physical drives ] .. but in windows i can only see my virtual drive i created using VMware.. what about my 8 other partitions, which contain my data?? "physical drives", as is referred to by VMware.

OK, dual boot sounds easier to me.. how do i reinstall GRUB??

---

### Post by gmc on 2007-01-18
> **icehammer said:**
> i got 9 partitions on my PC, [ 2 physical drives ] .. but in windows i can only see my virtual drive i created using VMware.. what about my 8 other partitions, which contain my data?? "physical drives", as is referred to by VMware.

OK, dual boot sounds easier to me.. how do i reinstall GRUB??

I had a similar problem, until I installed Samba, shared the partitions and drives on Ubuntu and then in VMWare/WinXP mounted the partitions/drives as shared. Now VMWare/WinXP can access everything that Ubuntu can.

Check the forums for a howto on accomplishing this feat.

Gord

---

