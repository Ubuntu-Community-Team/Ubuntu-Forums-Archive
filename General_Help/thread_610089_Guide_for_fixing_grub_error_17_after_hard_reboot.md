---
title: "Guide for fixing grub error 17 after hard reboot"
date: 2007-11-11
forum: General Help
---

### Post by antimatter15 on 2007-11-11
Sometimes, with wubi, when you do a hard reboot (without unmounting) the disks directory dissapears, which makes your installation useless. in my experience, you can easily fix it by typing chkdsk /F C:, and then navigating to C:\found.000 (or some number, try checking the contents if it has stuff like root.disk, swap.disk, home.disk, shared, or boot.) then there should be one directory named something like dir0000.chk, and then move it over to C:\ubuntu\dir0000.chk and rename it to C:\ubuntu\disks. Then ubuntu should work fine

---

