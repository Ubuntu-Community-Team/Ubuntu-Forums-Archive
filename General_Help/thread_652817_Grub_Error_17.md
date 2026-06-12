---
title: "Grub Error 17"
date: 2007-12-29
forum: General Help
---

### Post by PookyHello on 2007-12-29
Hi, I had a dual boot XP/Kubuntu on two different hardisks. I then used a partition manager to delete all the partitions on the Kubuntu Hardisk. I then made a new NTFS partition on that same disk. After rebooting, I got GRUB error 17. How will I delete GRUB and make it boot normally into XP?

---

### Post by bernied on 2007-12-29
You need to 'fix' your master boot record (mbr). There is a DOS application called fixmbr that will do this.

The problem is that the existing mbr, created by grub, will be pointing to a disk partition that no longer exists. You need to reinstate the windows mbr.

[google 'fixmbr'](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

---

### Post by meierfra on 2007-12-29
Click on  FixMBR in my signature.

---

### Post by PookyHello on 2007-12-29
Thanks for your help.

---

