---
title: "mysql connection to second HD"
date: 2013-09-01
forum: General Help
---

### Post by bill-lancaster on 2013-09-01
I'm recovering data from a hard drive where the (kubuntu) o/s crashed.  Its attached to another pc at the moment as a 'secondary' HD
How can I connect to the mysql database on it?
My intention is to back up the db to the main hd.

---

### Post by steeldriver on 2013-09-01
I'm not an expert in this area but since it's a weekend and the real db admins might be offline I'll throw my hat in

If you can boot the old system at all (iirc from your previous thread, it booted OK to the command line - just wouldn't start the KDE GUI?) I strongly advise you to consider doing so, and using mysqldump from the running system while you still can

[https://dev.mysql.com/doc/refman/5.5/en/mysqldump.html](https://dev.mysql.com/doc/refman/5.5/en/mysqldump.html)

Although it *should* be possible to rebuild databases from the fileset in /var/lib/mysql it's a lot more complicated - especially if the mysql versions and setups are not exactly the same - see for example

[http://serverfault.com/questions/250559/how-to-restore-mysql-database-from-the-physical-files](http://serverfault.com/questions/250559/how-to-restore-mysql-database-from-the-physical-files)

or do a web search for "/var/lib/mysql restore". Hope this helps.

---

### Post by cipherboy_loc on 2013-09-01
You have two options: Try and chroot and then back it up regularly (using mysqldump or the utility of your choice), or you could copy the /var/lib/mysql folder off of the drive as a replacement for a new install.
Basic chroot tutorial as follows:
```

mount -o bind /dev   /<mount point>/dev
mount -o bind /dev/pts   /<mount point>/dev/pts
mount -t proc none   /<mount point>/proc
chroot /<mount point>

```
This will give you a command prompt as if you were on the crashed o/s. 


Thanks,
Cipherboy

---

