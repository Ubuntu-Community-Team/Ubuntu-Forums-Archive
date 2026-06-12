---
title: "[SOLVED] Grub question"
date: 2008-06-15
forum: General Help
---

### Post by thezood on 2008-06-15
EDIT: I suddenly realize what an idiot I am. Of course grub doesn't write its own menu.lst. It only installs the boot loader. I guess sometimes you gotta post things on a forum to realize the obvious answer. #-o

I have a dual boot system with Winxp and Ubuntu 8.04. I recently made a change in my partitions with Partition Magic, and inserted a new partition so that my Linux root partition became sda2 instead of sda1. Since then the Grub menu doesn't work. I have to edit the boot menu before I can boot to Linux. 

I have run grub and made hd0,2 as Linux boot instead of hd0,1 but the changes are not saved in menu.lst. I was under the impression that the grub program wrote its own menu.lst. Or am I wrong? Of course I can change menu.lst myself but if grub is supposed to do it but doesn't, I'm thinking there's something wrong with my setup or there's a bug in Grub.

---

### Post by Happy_Man on 2008-06-15
Whether it's a bug in GRUB or not, it still works to boot the computer, so there can't be that much harm in editing menu.lst, even if only as a temporary solution.

---

### Post by meierfra. on 2008-06-15
> I was under the impression that the grub program wrote its own menu.
 No, grub does not write its own menu.   The program "update-grub" is able to write "menu.lst". But it is only used when you install Ubuntu and during kernel updates. You can also run it manually via "sudo update-grub".

But even if you run update-grub, it will usually not change the "root (hd?,?")" part.  Indeed, "update-grub" looks at  the line

# groot=(hd?,?)

in menu.lst and uses that for "root (hd?,?)"

But if you delete  "# groot=(hd?,?)" from menu.lst or if you delete "menu.lst" altogether, then  update-grub will compute "(hd?,?)" on its own.

Maybe you didn't really want to know all of this, but here comes the important part:

**Change "# groot=(hd0,2)" in menu.lst to "# groot=(hd0,1)"**

otherwise  all the "root (hd0,1)" will be changed back to "root (hd0,2)" during the next kernel update,

---

### Post by thezood on 2008-06-17
> **meierfra. said:**
> No, grub does not write its own menu.   The program "update-grub" is able to write "menu.lst". But it is only used when you install Ubuntu and during kernel updates. You can also run it manually via "sudo update-grub".

But even if you run update-grub, it will usually not change the "root (hd?,?")" part.  Indeed, "update-grub" looks at  the line

# groot=(hd?,?)

in menu.lst and uses that for "root (hd?,?)"

But if you delete  "# groot=(hd?,?)" from menu.lst or if you delete "menu.lst" altogether, then  update-grub will compute "(hd?,?)" on its own.

Maybe you didn't really want to know all of this, but here comes the important part:

**Change "# groot=(hd0,2)" in menu.lst to "# groot=(hd0,1)"**

otherwise  all the "root (hd0,1)" will be changed back to "root (hd0,2)" during the next kernel update,

Thanks, that was really helpful! I always welcome new knowledge. :)

---

