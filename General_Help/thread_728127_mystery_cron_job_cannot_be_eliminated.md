---
title: "mystery cron job cannot be eliminated"
date: 2008-03-18
forum: General Help
---

### Post by waster on 2008-03-18
I installed mysql-admin, and configured a backup of a database to occur. This ran nicely in a cron job until I uninstalled mysql-admin.

The cron job still runs, failing to find /usr/bin/mabackup (because it is part of mysql-admin). There is NO RECORD of the mabackup call in my /etc directory. I reinstalled mysql-admin and made sure the backup job was deleted in the database, too.

Grepping for mabackup gives nothing. mysql is uninstalled. What on earth is running this job?

Thanks, Jack.

---

### Post by Oldsoldier2003 on 2008-03-18
> **waster said:**
> I installed mysql-admin, and configured a backup of a database to occur. This ran nicely in a cron job until I uninstalled mysql-admin.

The cron job still runs, failing to find /usr/bin/mabackup (because it is part of mysql-admin). There is NO RECORD of the mabackup call in my /etc directory. I reinstalled mysql-admin and made sure the backup job was deleted in the database, too.

Grepping for mabackup gives nothing. mysql is uninstalled. What on earth is running this job?

Thanks, Jack.
check for any user with mysql in its name.. and also check roots crontab. you might also want to look in cron.daily (or weekly or monthly)

---

### Post by waster on 2008-04-23
I've no idea where the data was stored, but I fixed this using the crontab command line tool.

---

