---
title: "Editing Crontab"
date: 2017-07-17
forum: General Help
---

### Post by brenneke on 2017-07-17
I am just learning about Cron and am stuck with something I am sure is very simple but cannot find any information on. I am editing by typing crontab -e in terminal, add line, then ^X, Y , it then says "File Name to Write: /tmp/crontab.bk0F19/crontab" What do I do here? I tried typing in /var/spool/cron/crontabs and also /var/spool/cron/crontabs/my_user - in both cases it asks "Save file under DIFFERENT NAME ?" Please clarify - thanks.

---

### Post by Dennis N on 2017-07-17
Is that using nano as the text editor? After typing your crontab entry, ^O (control-O) will initiate save: at "File Name to Write" use the supplied name - just press Enter.  It will report "wrote 1 line". Finally, ^X (control-X) to exit. You are done.

You can enter 
```
crontab -l 
```
to verify your crontab entry is there.

---

### Post by brenneke on 2017-07-17
Dennis - you were absolutely correct, saved to the supplied file name, confirmed it was there with crontab -l as you said - thank you!

---

