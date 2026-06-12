---
title: "Delete backup"
date: 2008-05-14
forum: General Help
---

### Post by screaminfakah on 2008-05-14
I am running Hardy Heron and I installed a backup program and proceeded to back up my entire system.  The backup failed and when I went to delete the backup I have had problems getting it to delete.  Now it is stuck in my trash can.  Any suggestions on how to force this delete?  The file is 8.8gigs.
Also since it is just a backup is it safe to delete?

Thanks much.

---

### Post by TeoBigusGeekus on 2008-05-14
Since it is a backup (i.e. a copy), I presume it is safe to delete. Open a terminal and type:
```
sudo rm -r ~/.local/share/Trash/files/*
```

---

### Post by screaminfakah on 2008-05-14
Will this be a quick process you think because when I chose to empty trash it started to work then eventually slowed down to a crawl and stopped working.

---

### Post by talz13 on 2008-05-14
> **screaminfakah said:**
> Will this be a quick process you think because when I chose to empty trash it started to work then eventually slowed down to a crawl and stopped working.

Well, you can fire that off in a terminal, and if it doesn't finish quickly, you can always open another terminal, run ```
ps aux | grep rm
```, find the rm process PID, and run ```
sudo kill <process PID number here>
``` to end it

---

### Post by screaminfakah on 2008-05-14
That did the trick.  It deleted quickly with no problems.
Thank you very much for all of your help.

---

