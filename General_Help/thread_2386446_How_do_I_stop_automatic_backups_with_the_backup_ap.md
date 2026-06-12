---
title: "How do I stop automatic backups with the backup app"
date: 2018-03-06
forum: General Help
---

### Post by Old Jimma on 2018-03-06
Hello Ubuntuers:

I want to stop using the automatic backup and restore utility. How do I  do that?

Thanks,

Old Jimma

---

### Post by col48 on 2018-03-06
I've never used automatic backup, so this may be a bit naive....

It must be scheduled: is there something in your startup list which asks whether it is time to do a backup?  And there may be an input file which says when the next backup is due and the interval between them.
It must be done by a program: if you uninstall the program (or, less drastically, rename the executable) it can't happen - although the scheduler might complain when it tries to run it!

---

### Post by deadflowr on 2018-03-06
Open Backups and go down the side panel to scheduling.
Then toggle Automatic Backups to Off.

That's it as far as turning them off is.

It's unclear if you plan on doing anything beyond that.

---

### Post by Old Jimma on 2018-03-07
Thanks deadflowr:

I can't find the backup app on my machine now. I looked at all apps installed.... and it wasn't there.

Can you help me find it? I know its is there someplace.

Thanks
Old J

---

### Post by #&amp;thj^% on 2018-03-07
Maybe look for "Deja Dup"

---

### Post by mc4man on 2018-03-07
```
sudo apt-get purge deja-dup
``` would certainly stop it.

---

### Post by rbmorse on 2018-03-07
look in the utilities sub menu

---

### Post by Old Jimma on 2018-03-08
Thanks 1fallen.

---

### Post by Old Jimma on 2018-03-08
Thanks mc4man

---

