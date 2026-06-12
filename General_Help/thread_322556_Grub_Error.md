---
title: "Grub Error"
date: 2006-12-20
forum: General Help
---

### Post by kyldere on 2006-12-20
After I do a clean install of Edgy, I have the screen comes up with "error 15: file not found". I press enter to continue and it brings me back to the grub menu. What is going on here? I have one drive with a hardware RAID-0 setup (SATA sda1) and a boot drive (SATA sdb1). I set up partitions for /boot, /, and swap on the boot drive and am trying to use the RAID as a /home drive. If I use the Live CD, during the install (step 6 of 6, if I remember correctly) asks where I want to install GRUB (defaulting to hd0). Unless I change this to hd1 (which is sdb1, right?), I get an error that tells me that GRUB did not install. If I try installing with the server CD, I get the same error message without having to tell the installer where to put GRUB. Can anyone shed some light on this for me, please?

---

### Post by linuchsan on 2006-12-20
Can we have some hardware configuration (hardware raid) ?

---

### Post by kyldere on 2006-12-20
Sure ... the hardware RAID is a set of 4 Hitachi Deskstars (163 GB each) striped together in a RAID-0 (128K) for a total of a drive just under 660 GB. The RAID card is a 3ware. This array shows up as sda1 (if I remember correctly). The array was set up in the 3ware bios manager and appears to be healthy.

The boot drive is a WD 360 and it connects to an on-board PCI Silicon Image 3112A Controller on an Intel XE7505VB2 Server board. This shows up as sdb1.

---

