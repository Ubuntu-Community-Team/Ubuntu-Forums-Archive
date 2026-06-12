---
title: "Syslog-ng log files don't rotate"
date: 2008-04-04
forum: General Help
---

### Post by seeker1458 on 2008-04-04
I have tried installing logrotate to more effectively rotate my syslog-ng files.  After I installed it, my logs stopped rotating all together.  How do I get them to start rotating again? I would like them to rotate out every week.  Thanks in advance.

---

### Post by aussie2008 on 2008-07-03
I have also the same problem. but i didn't got any fix yet.

---

### Post by aussie2008 on 2008-07-08
i found on my server logrotate was not cron to daily. logrotate scripts was cron to monthly. i have copy that script to cron daily and created /etc/logrotate.d/syslog

#cat syslog

/var/log/syslog {
   daily
   missingok
   rotate 20
   compress
   postrotate
      /etc/init.d/syslog-ng restart >/dev/null
   endscript
}


/var/log/messages {

   daily
   missingok
   rotate 7
   notifempty
   compress
   sharedscripts
}

you can put more logs name, if you want to rotate daily.

i hope, this will  help you.

---

