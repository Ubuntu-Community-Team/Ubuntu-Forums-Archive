---
title: "crontab problem"
date: 2006-07-05
forum: General Help
---

### Post by mega on 2006-07-05
Having trouble with this cron, there's no error, no log created

[email]mega@freddy:/etc/cron.hour[/email]ly$ more dkp.sh
#!/bin/sh
/root/dkpupdate.sh > /root/dkplog.txt


mega@freddy:/root$ more dkpupdate.sh
#!/bin/sh
mysql -u user33 -pblahh web2_db1 -v -v -v < /root/dkp-decay.txt


mega@freddy:/root$ more dkp-decay.txt
SET @DAYS := 60;
#removes raid from users raid history
delete from eqdkp_raids where from_unixtime(raid_date) < date_sub(curdate(), interval @DAYS day);

#removes items from purchase history
#delete from eqdkp_items where from_unixtime(item_date) < date_sub(curdate(), interval @DAYS day);


sugestions?

---

### Post by mannheim on 2006-07-05
I think you need to rename the file dkp.sh in /etc/cron.hourly so that it does not contain a period: it needs to consists of lowercase alphanumerics and hyphens. See the man-page for run-parts.

I think the reason for this restriction is that the scripts get run in alphabetical order of their names. If more general characters are allowed in the names, then alphabetical order becomes ambiguous because it depends on the character encoding.

---

### Post by xtacocorex on 2006-07-05
Have you allowed yourself and root to run cron jobs by creating:
```
sudo touch /etc/cron.allow
```

and then editing it with:
```
sudo gedit /etc/cron.allow
```

and inside, type:
```

root
mega

```
(I'm assuming that your username is mega)

---

### Post by mega on 2006-07-05
renamed the file, checked the others, the job still wont run

my other jobs work fine though, including one that does a mysqldump

---

### Post by mannheim on 2006-07-05
Hmm. I guess you have checked that both scripts have the executable permission?

---

### Post by mega on 2006-07-05
yep, everything has +x, root owns all files

---

### Post by mannheim on 2006-07-05
Well, dunno. I presume you've checked that this works okay:

```
[COLOR="Blue"]mega@freddy:/etc/cron.hourly$[/COLOR] sudo ./dkp.sh

```

If so, you should check that the following works okay: what the default crontab does each hour is do "run-parts" on /etc/cron.hourly, so you should test:

```
[COLOR="Blue"]mega@freddy:~$[/COLOR] sudo run-parts --verbose /etc/cron.hourly

```
 
The above should run all the scripts in cron.hourly, and report on its doings for each one. Finally, you should confirm that /etc/crontab really does contain a line similar to

```
17 *    * * *   root    run-parts --report /etc/cron.hourly
```

---

