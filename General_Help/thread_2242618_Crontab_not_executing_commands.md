---
title: "Crontab not executing commands"
date: 2014-09-02
forum: General Help
---

### Post by derek23 on 2014-09-02
Hi All,

Having an issue with crontab on my macmini 2007.  I'm running 14.04 and have created a crontab to run a couple commands locally on the machine to backup a MySQL database it is running.  Here are the contents of my crontab:

```
#!/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games


10 2 * * * /usr/bin/mysqldump -u xbmc -pxbmc MyVideos78 | gzip > "/mnt/MySQL/db-`date +%Y-%m-%d_XBMC`.ql.gz"
30 2 * * * find /mnt/MySQL -name "db-*.sql.gz" -mtime +20 -exec rm {} \; >>  /mnt/MySQL/database_del.lg 2>&1
```

Can anyone point me in a direction to troubleshoot this?  I have looked in the crontab logs and not found anything helpful.

---

### Post by CaptainMark on 2014-09-03
Here is a discussion into some common reasons why crontab doesn't work as expected, [http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work](http://askubuntu.com/questions/23009/reasons-why-crontab-does-not-work)
crontab is extremely well tested and stable so try not to make the beginner mistake of thinking you've found a bug in cron, it's probably something simple you've done by accident.

I've got to be honest I've never seen the shebang put inside crontab itself, normally I'd put it in the script cron would run but I don't know if this would cause a problem exactly, just that shell expansion can get kind of messy in the crontab in my experience.

As always with cron trouble shooting, my best advice would be to change the command to something really really simple first ( echo "$(date)" > /home/mark/Desktop/crontest.txt ), establish that cron IS actually working and then add components back into your command slowly until you get your cron command back to where it is now, that will help you figure out which bit exactly cron doesn't like.

---

### Post by derek23 on 2014-09-04
Does look like the crontab is working.  I created a different cron job for it to run and it worked as expected.  So you might be on to something with the shebang thing.  When i have time i'm going to try and throw those into a script and run them from there then add the script to the crontab.

---

