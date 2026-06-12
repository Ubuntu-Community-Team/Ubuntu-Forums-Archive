---
title: "Lost Mbr"
date: 2007-09-24
forum: General Help
---

### Post by Don DeGregori on 2007-09-24
Did have dual boot with XP and Ubuntu on single internal HD. To make a long story short, all I see now with LiveCD and QTParted is XP partition intact, and extended partition, the rest is free where Ubuntu was. When I boot, I see grub load stage 1.5, then error 22. That's it. Need to get XP back first. The menu.lst was from Ubuntu. Please help. I don't know what to try next.
Thanks, Don

---

### Post by psusi on 2007-09-24
You blew away your Ubuntu partition.  Reinstall it.

---

### Post by Don DeGregori on 2007-09-24
Will XP be bootable from menu.lst after I re-install. Is there a question I should annswer during grub installing menu.lst, for XP is  not bootable because no menu.lst? I guess I need reassureance that all will go OK and I can boot XP again arter re-install Ubuntu.

Thanks, Don

---

### Post by kellemes on 2007-09-24
If I where you I would burn and boot from [Super Grub Disk]("http://supergrub.forjamari.linex.org/").. from there you can try to boot Windows so at least you know it's still there..

---

### Post by psusi on 2007-09-24
Yes, if you reinstall you should have windows on the grub boot menu.  The reason you can't boot windows now is because you blew away grub.

---

