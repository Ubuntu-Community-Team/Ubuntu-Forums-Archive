---
title: "wubi 8.04 booting problems"
date: 2008-03-16
forum: General Help
---

### Post by cm_hartman on 2008-03-16
I've installed Ubuntu 8.04 using wubi 8.04 once up windows xp and Ubuntu run fine. i have a problem with the booting process though. upon booting my pc i get a "missing operating system" error. i found by pressing f10 to access system restore i get a boot menu with a non functioning windows, windows restore, and Ubuntu option. choosing restore goes to windows restore, and choosing Ubuntu goes to the Ubuntu startup where Ubuntu starts fine or pressing escape goes to the grub menu. there are the various Ubuntu options as well as "windows xp[loader]" and "windows xp" options first option goes to windows xp boot menu from where more os options are available, windows xp starts fine from here. i am looking for a solution to eliminate all these extra steps, and to boot windows by default

---

### Post by ago on 2008-03-17
Try running chkdsk /r from windows
In any way, the Ubuntu -> Windows boot menu should be identical to booting directly from windows.

---

