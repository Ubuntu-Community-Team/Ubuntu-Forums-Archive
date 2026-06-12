---
title: "Windows XP Media Center Edition 2005 will not load after installing 12.04"
date: 2013-05-19
forum: General Help
---

### Post by xTheUntoldStoryx on 2013-05-19
[COLOR=#000000]Hi! after i downloaded ubuntu 12.04 ALONGSIDE Windows XP Media Center Edition 2005 i was unable to use XP when booting Xp from the grub menu i just get a constant blinking "-" on the corner of my screen i do not have a boot disk or a recovery disk so that is out of the question is there anything i did wrong or is there anyway that i can use windows XP again? i have an HP Pavillion a1600i with a 200GB HHD and have a 132GB being used for the ubuntu file system any help?[/COLOR]

---

### Post by mastablasta on 2013-05-20
use the boot repair tool to generate the bootinfo summary and then post it here using the code (the # icon) tags. : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

how was ubuntu installed? side by side? or using wubi?

---

### Post by xTheUntoldStoryx on 2013-05-20
> **mastablasta said:**
> use the boot repair tool to generate the bootinfo summary and then post it here using the code (the # icon) tags. : [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

how was ubuntu installed? side by side? or using wubi?

i installed ubuntu side by side windows XP Media Center Edition 2005 when i get the purple grub menu it even says Microsoft Windows XP Media Center Edition 2005 but when i select it to run that os i just get the constant blinking "-" in the corner with a black screen

---

### Post by j0eb0b on 2013-05-20
I think your Windows MBR is hosed.  Try downloading and running this tool to try and fix it.  
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Mark Phelps on 2013-05-21
You need to follow the instructions in post #2 and generate that report -- as without that information, we're all just guessing here.

---

