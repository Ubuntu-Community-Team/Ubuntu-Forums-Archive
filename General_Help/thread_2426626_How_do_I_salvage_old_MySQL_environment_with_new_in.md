---
title: "How do I salvage old MySQL environment with new install of OS and MySQL"
date: 2019-09-11
forum: General Help
---

### Post by cscj01 on 2019-09-11
I had a crash and needed to restore my Ubuntu 18.04 x64 system. During the install there was a power surge. I restarted the restore, but did not have a boot record on the system drive after the restore finished. After nothing seemed to work getting a boot record installed, I decided to reinstall my OS from a Live CD, reinstall all my programs, and copy over configuration files where needed to get my system back as it should be. This has worked fine for everything except MySQL. All the necessary files and data bases are on my backup drive containing my OS, but I'm not sure how to go about replacing files in MySQL. I would appreciate any suggestions on how to best accomplish this. Thanks.

---

### Post by Tadaen_Sylvermane on 2019-09-11
If you've been making regular db dumps with mysqldump its trivial. If not, I'm not sure. I dump my dbs every night to google drive. Some people make them more often. If you haven't been doing this, now is a good time to start. Create a user with proper permissions and away you go. Here is what I use.

```
if [[ $(systemctl is-active mysql) == active ]] ; then
    mysqldump \
    --user=backup \
    --password=backup \
    --single-transaction \
    --all-databases \
    | gzip > "$POOLLOC"/backups/mysqldump/mydatabases."$NOW".sql.gz
    find "$POOLLOC"/backups/mysqldump/ -type f -mtime +10 -exec rm {} \;
fi
```

To restore your dbs you simply run below on your fresh installation. Don't forget to manually backup your /etc/mysql/ files as needed to.

```
zcat $BACKUPFILE | sudo mysql
```

This script and zcat command are sourced and modified from the Arch wiki.

Also, unless you have a compelling reason to stay with MySQL specifically, I'd recommend moving to MariaDB. Seems better supported, doesn't have Oracle's grubby hands on it. Also in my own use case, way faster with Kodi.

---

### Post by SeijiSensei on 2019-09-11
I also create plain-text backups every night of all my databases using mysqldump and, for my preferred DBMS PostgreSQL, pg_dumpall.

I've had success by replacing /var/lib/mysql created by a new installation with the contents of the backed-up version.

I'd use rsync to copy the directory to insure that all the permissions are preserved.

```

cd /var/lib
sudo mv mysql mysql.old
sudo rsync -av /path/to/backup/var/lib/mysql .

```
The dot represents the current directory, in this case /var/lib.

Shut down MySQL before doing this transfer, then restart it.  How's it look?

---

### Post by cscj01 on 2019-09-11
> **SeijiSensei said:**
> I also create plain-text backups every night of all my databases using mysqldump and, for my preferred DBMS PostgreSQL, pg_dumpall.

I've had success by replacing /var/lib/mysql created by a new installation with the contents of the backed-up version.

I'd use rsync to copy the directory to insure that all the permissions are preserved.

```

cd /var/lib
sudo mv mysql mysql.old
sudo rsync -av /path/to/backup/var/lib/mysql .

```
The dot represents the current directory, in this case /var/lib.

Shut down MySQL before doing this transfer, then restart it.  How's it look?

In your second command, you're saving the contents of /var/lib/mysql, correct?  I presume that is so I can restore my current /var/lib/mysql should things go wrong.

I did have a chron job (bash script) that dumped my DB's.  That got lost or deleted when I migrated from 14.04 -> 16.04.  I just forgot about it because it had ben around so long and ran in the early morning hours.  I need to reinstate that.

---

### Post by SeijiSensei on 2019-09-11
Yes, I'm preserving the newly-created /var/lib/mysql directory in case something goes wrong.

---

### Post by cscj01 on 2019-09-11
> **SeijiSensei said:**
> I also create plain-text backups every night of all my databases using mysqldump and, for my preferred DBMS PostgreSQL, pg_dumpall.

I've had success by replacing /var/lib/mysql created by a new installation with the contents of the backed-up version.

I'd use rsync to copy the directory to insure that all the permissions are preserved.

```

cd /var/lib
sudo mv mysql mysql.old
sudo rsync -av /path/to/backup/var/lib/mysql .

```
The dot represents the current directory, in this case /var/lib.

Shut down MySQL before doing this transfer, then restart it.  How's it look?

Well, in my old systrem the objects in /var/lib/mysql were in group 130.  I moved them without checking that. The new system has mysql in group 129.  How do I correct this?  Can I change mysql's group to 130, should I redo the rsync without the dot, or what?

---

### Post by Tadaen_Sylvermane on 2019-09-11
Chown the files to the proper user and group. Nothing more should be needed,

---

### Post by SeijiSensei on 2019-09-11
```
sudo chown mysql:mysql /var/lib/mysql -R
```

---

### Post by cscj01 on 2019-09-11
I'll close this thread.

---

### Post by wildmanne39 on 2019-09-11
Will you please post the solution so other searchers will benefit from this thread?

Thanks

---

