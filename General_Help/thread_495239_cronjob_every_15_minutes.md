---
title: "cronjob every 15 minutes"
date: 2007-07-07
forum: General Help
---

### Post by 4ndr3w on 2007-07-07
hi,
I need to setup a cron job to run the command "./r2e run" (without ") every 15 minutes. I can't seem to understand what I need to write in the crontab. Could someone tell me?

Thanks!

---

### Post by scxtt on 2007-07-07
in a terminal: **sudo nano /etc/crontab** (to edit the system crontab), you could also do **crontab -e** to edit your own (leave out username, in that case) ...

0,15,30,45 *    * * * <username>   <command>

note: **/15* may work in place of *0,15,30,45*

---

