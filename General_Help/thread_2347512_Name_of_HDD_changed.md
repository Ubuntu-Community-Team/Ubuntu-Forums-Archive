---
title: "Name of HDD changed"
date: 2016-12-26
forum: General Help
---

### Post by Aries01 on 2016-12-26
Hi

  I keep my data on a separate HDD, with Ctrl D shortcuts assigned to the most often used directories. The HDD has to be mounted before the shortcuts can be used- if one forgets to do that access is denied but after mounting the HDD access is granted as expected. Recently, after I'd made this mistake, the shortcuts remained inaccessible even after the HDD was mounted and became accessible. Afterwards file browser windows of locations on the HDD have been appearing with the number 1 added to the end of the volume's name. In /media two icons for the same HDD are displayed, the original and the one with the changed name, and permissions are denied for viewing the original, and access is given to the one with the changed name.   
  
  Applications handle files using the changed volume's name, not the original. Data hasn't been lost but the problem is annoying. I wonder if anyone can explain how this problem can be rectified.

---

### Post by ajgreeny on 2016-12-26
Is your data disk normally mounted at boot from /etc/fstab or do you have to click on it in the file manager or desktop icon to mount it?

Using /etc/fstab is the way to go if the disk is needed permanently, and using that system you can mount it wherever you wish, and it will always be available using the same disk name in the file manager.

It is probably worth giving the partition on the disk a label using, for example, gparted, and the disk will then always show in the file manager with that label name.

---

