---
title: "Can't boot from Ubuntu anymore"
date: 2008-03-13
forum: General Help
---

### Post by werg on 2008-03-13
Hi, I configured my grub menu file incorrectly, and so I can't boot into Ubuntu anymore - I'm currently running on Windows. Is there a way to rectify this?

Thanks.

---

### Post by Rocket2DMn on 2008-03-13
You can either boot from the LiveCD and mount your root partition and edit from there, or from windows you can install this driver to read/write ext2/3 filesystems - [http://fs-driver.org/](http://fs-driver.org/)
From there you can edit the /boot/grub/menu.list file.  For now you may just want to undo the changes you made.  The lesson is, always backup config files before you fiddle with them!

---

