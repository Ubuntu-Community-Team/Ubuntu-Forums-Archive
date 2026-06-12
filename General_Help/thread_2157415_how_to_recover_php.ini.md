---
title: "how to recover php.ini"
date: 2013-06-25
forum: General Help
---

### Post by sanjeevdivekar on 2013-06-25
Accidentally i deleted php.ini from /etc/php5/apache2. How to recover it?

I tried to remove and install php5 without luck.

Thanks,

---

### Post by Azdour on 2013-06-25
Hi,

Does this thread help? - [http://ubuntuforums.org/showthread.php?t=1709000](http://ubuntuforums.org/showthread.php?t=1709000)

---

### Post by coffeecat on 2013-06-25
Not a Forum Feedback & Help thread.

*Thread moved to **General Help**.*

---

### Post by SeijiSensei on 2013-06-25
If this is a server, I strongly recommend using rsync to back up key directories like /etc, /var/spool, /var/log, and the like every night.  /etc in particular is usually highly customized to each machine and needs a backup.

Something as simple as 

```
1 1 * * *  cd /; rsync -a etc var/spool var/log /path/to/backup/location/
```

is a good start.  Put this in root's crontab either by using "sudo crontab -e" or by creating the file /var/spool/cron/root directly with an editor and sudo.

---

