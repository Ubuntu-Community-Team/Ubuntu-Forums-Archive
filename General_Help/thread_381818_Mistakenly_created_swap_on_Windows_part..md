---
title: "Mistakenly created swap on Windows part."
date: 2007-03-11
forum: General Help
---

### Post by knuno on 2007-03-11
I happened to set my hda1 as a Linux swap partition by accident. I used the command 'mkswap /dev/hda1'
I did not format the disk.
The problem is that this is my Windows XP boot partition formatted with NTFS (and the only partition on the disk). And now I can't boot Windows XP.
Is there any way to restore hda1 as my Windows boot partition?

Knut

---

### Post by taurus on 2007-03-11
Try using gparted from the LiveCD to retag /dev/hda1 as ntfs again (without formatting).  Now, see if you can boot XP from it.

---

### Post by knuno on 2007-03-11
Do I do that by right-clicking and choosing "Format to"? (That sounds a bit scary!)

Knut

---

