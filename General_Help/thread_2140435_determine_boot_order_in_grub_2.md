---
title: "determine boot order in grub 2"
date: 2013-04-29
forum: General Help
---

### Post by doralsoral on 2013-04-29
Is there anyway to look and see the boot order of all the entries in grub2. I currently have an issue where it seems i am going to have to boot from an older kernel until something is done about it. I know i can choose which entry is default but is there a way to figure this out without rebooting it and looking at the grub menu. I currently don't have physical access to the machine and would like to test it out. Thanks

---

### Post by oldfred on 2013-04-29
This will list the items in grub.cfg.

 List of grub menu:
grep menuentry /boot/grub/grub.cfg
or numbered list:
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0


This used to work but it did not
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting--number=0

---

### Post by ajgreeny on 2013-04-29
Try ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
``` which simply adds a space to "menuentry " to avoid a lot of unimportant entries of that word in grub.cfg appearing in the output, and also cuts the length of each output line to 100 characters (it can be fewer than that if you wish).

That will show you what your menu contains in the order that it occurs in grub.cfg but not which is set to be the boot menu item.  I have never needed to boot anything other than the most recent kernel by default, so can't help with that query, but have a look in the grub2 links in my signature.

---

