---
title: "cron not working with DISPLAY"
date: 2007-03-08
forum: General Help
---

### Post by kobewan on 2007-03-08
For some reason, my cron stopped working properly a couple of weeks ago. I use it, like so many other people, mainly as an alarm clock to play mp3 files. I had a script and everything set (using Amarok to play the files). The script used to work perfectly fine. However, one day it stopped working. cron itself still works, and it will run any job that I set that doesn't need X. I can't just can't get it to run anything that needs to communicate with X to work. The output of crontab -l with a simple task is: 

* * * * * export DISPLAY=:0 && /usr/bin/xmms

And the last line of /var/logs/syslog is something like this:

Mar  9 07:55:01 {computer name} /USR/SBIN/CRON[14835]: {(username)} CMD (export DISPLAY=:0 && /usr/bin/xmms )

There aren't any errors in the log.

EDIT: After posting, I checked the logs again and they read like this:

Mar  9 07:55:01 (username)-ubuntu /usr/sbin/cron[4481]: ((username)) RELOAD (crontabs/(username))
Mar  9 07:55:01 (username)-ubuntu /USR/SBIN/CRON[14835]: ((username)) CMD (export DISPLAY=:0 && /usr/bin/xmms )
Mar  9 07:56:01 (username)-ubuntu /USR/SBIN/CRON[15021]: ((username)) CMD (export DISPLAY=:0 && /usr/bin/xmms )
Mar  9 07:57:01 (username)-ubuntu /USR/SBIN/CRON[15205]: ((username)) CMD (export DISPLAY=:0 && /usr/bin/xmms )
Mar  9 07:57:01 (username)-ubuntu /USR/SBIN/CRON[15204]: ((username)) MAIL (mailed 116 bytes of output but got status 0x0001 )

---

### Post by kobewan on 2007-03-10
Nobody knows why this won't work? I'm even ok with not being able to fix it, but I'm curious as to how it broke in the first place.

---

### Post by unni on 2007-03-10
Will this work?


* * * * * DISPLAY=unix:0 /usr/bin/xmms

---

### Post by kobewan on 2007-03-12
> **unni said:**
> Will this work?


* * * * * DISPLAY=unix:0 /usr/bin/xmms

Nope, still no effect.

---

