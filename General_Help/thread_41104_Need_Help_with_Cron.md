---
title: "Need Help with Cron"
date: 2005-06-11
forum: General Help
---

### Post by wirjo on 2005-06-11
I have the following when I do 'crontab -l'

40 12 * * * /usr/bin/azureus

It should run azureus at 12:40 PM right? 

Well - it's not doing anything... Please help me.

---

### Post by professor_chaos on 2005-06-11
Try using the 24hour clock.

40 23 * * * /usr/bin/azureus

---

### Post by Xian on 2005-06-12
[QUOTE=wirjo]I have the following when I do 'crontab -l'

40 12 * * * /usr/bin/azureus

It should run azureus at 12:40 PM right? 

Well - it's not doing anything... Please help me.[/QUOTE]
You have to set cron in military time.
Maybe you meant to set it to 00:40?

---

