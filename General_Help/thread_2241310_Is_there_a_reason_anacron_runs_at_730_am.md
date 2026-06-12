---
title: "Is there a reason anacron runs at 7:30 am?"
date: 2014-08-25
forum: General Help
---

### Post by pkerr2 on 2014-08-25
I'm doing some analysis of /var/log/mail.log and realized that anacron rotates log files at 7:30AM which means I don't get a full day at the begining and end of the log file.  Is there any reason why I should not change /etc/cron.d/anacron from 30 7 * * * ... to say 00 00  * * * ... 

What is the reason the default is 7:30 AM?

---

