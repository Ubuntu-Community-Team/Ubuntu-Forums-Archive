---
title: "Ubuntu ate my modem, so I ate a GRUB!"
date: 2007-09-12
forum: General Help
---

### Post by Uncle_Grombor on 2007-09-12
I have been having problems with Ubuntu my modem and other things so I re-installed RHEL5.  When I did this I was going to dual-boot.  Ubuntu should still be there.  Originally I hade hda/free hdb/ubuntu hdb-extended-swap/GRUB.  I didn't like my swap on hdb.  I installed redhat, formated hdb-extended-swap so all hdb is is a large ext3/ubuntu.  Installed hda RHEL5/Grub.  Now my pointer is broke.  Is there a way I can fix this without reinstalling ubuntu.  Thanks.  I'm in a hurry, hope it made sense.

---

### Post by eggdeng on 2007-09-12
Try adding
```
title		ubuntu
root		(hd1,0)
chainloader	 +1
```
to the end of Red Hat's /boot/grub/menu.lst

---

