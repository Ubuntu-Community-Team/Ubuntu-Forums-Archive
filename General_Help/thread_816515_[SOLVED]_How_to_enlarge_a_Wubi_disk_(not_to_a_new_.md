---
title: "[SOLVED] How to enlarge a Wubi disk (not to a new partition or move /home to another"
date: 2008-06-02
forum: General Help
---

### Post by unicorn_2003_1 on 2008-06-02
As is in the title, is there a way I can enlarge the Wubi created disk? 

I know it's possible to have another disk or move /usr, /home, etc to another dedicated disk.

Just wondering can we just enlarge the disk? that would be more convenient than another disk I think.

Thanks.

---

### Post by Dave2k6 on 2008-06-02
Use LVPM from [http://lubi.sourceforge.net/lvpm-latest.deb]("http://lubi.sourceforge.net/lvpm-latest.deb") to resize the / (root) partition.

---

### Post by unicorn_2003_1 on 2008-06-02
Thanks Dave, I'll check into that.

---

### Post by dimitris2006 on 2008-06-19
i had the same question, i used LVPM but after LVPM finished resizing i couldnt boot windows and ubuntu. then i restored windows backup and installed ubuntu with wubi again :(

---

