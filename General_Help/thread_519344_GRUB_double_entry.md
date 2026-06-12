---
title: "GRUB double entry"
date: 2007-08-06
forum: General Help
---

### Post by smmalis on 2007-08-06
When I boot up, there are two Ubuntu entries.  One ends in 16, the other in 15.  I just installed Ubuntu, and this appeared after installing all the updates.  Can I get rid of 15?  or should I get rid of 16?  I'd like just one Ubuntu entry.

---

### Post by apetresc on 2007-08-06
This new entry appears because you have installed a new kernel (probably unintentionally when doing a regular system update through the package manager). Grub lists each kernel as a separate entry. You probably want to remove the old one (the -15 one), though if you do, you may have to reinstall some drivers, such as the proprietary nvidia/ati ones if you were using those.

It is very easy to make those entries disappear. Simply open up the file "/boot/grub/menu.lst" and remove the entries from there that you don't want. An entry consists of 4 or 5 lines, so make sure you delete it entirely or you may find yourself unable to boot. Use the whitespace as a guide to how large each entry is.

Or, post your menu.lst file here and I'll make the change for you if you're not sure you want to take the risk of doing the modification yourself. :)

---

### Post by bodhi.zazen on 2007-08-06
Best keep 1 "old" kernel in case you have problems with the new...

Otherwise you can remove them via synaptic and, as part of the removal, the grub entries will also be removed.

You can keep the old kernel(s) and edit /boot/grub/menu.lst as AdrianP suggests, it will not do more then take up (a small amount of) space on your disk.

---

