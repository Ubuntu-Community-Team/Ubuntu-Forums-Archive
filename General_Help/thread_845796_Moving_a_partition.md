---
title: "Moving a partition"
date: 2008-06-30
forum: General Help
---

### Post by McTek on 2008-06-30
If I move a linux partition how do I get grub to find it?

---

### Post by dominiquec on 2008-06-30
You have to edit /boot/grub/menu.lst to tell it where the partition is.

---

### Post by McTek on 2008-06-30
> **dominiquec said:**
> You have to edit /boot/grub/menu.lst to tell it where the partition is.

Can I do that by just editing Menu.lst from the old uuid to the new uuid?
Tried that and it does not work.

---

### Post by dominiquec on 2008-07-01
Thought about my previous answer then I realized I should have asked: are you moving your main Linux partition?  Because if you are, chances are GRUB will not find it.  

These two links might help:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
[http://roshan18.wordpress.com/2008/02/03/reinstalling-grub-boot-loader/](http://roshan18.wordpress.com/2008/02/03/reinstalling-grub-boot-loader/)

However, if the partition you are moving is not your main Linux partition (the one associated with GRUB), then you can just edit menu.lst.

---

