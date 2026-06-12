---
title: "[SOLVED] Backups"
date: 2008-04-20
forum: General Help
---

### Post by timboellis on 2008-04-20
I have installed Ubuntu 7 onto a big standard PC IDE drives etc.

However I am using this as a web server with effect with Apache, MYSQL, PHPMYADMIN etc.

THe question is this : in the /var/www folder the content does not change as all the content is driven by several SQL databases so can I just backup the folder where ever the SQL databases are stored rather than just backing up and running a SQL query.

Also if i done this and lets say the machine crashed i do a rebuild the same way it is now, can i just drop the SQL folder backinto the same directory would it work or is this a no no.

---

### Post by SpaceTeddy on 2008-04-20
backing up the folder with for the database can lead to incinsitent snapshots of the data, which might render your backup useless. Instead, i would suggest you do a dump of your database into a textfile, zip it and shove it into a backup.
the other option is to shutdown the mysql server, then do the backup, then start it again.

i do the dump in a daily run cron job and always overwrite the same file. Then i mirror that file every day with rsnapshot so i have a history of it for 7 days, 8 weeks, 6 month and 1 year.

is that what you were looking for ?

---

### Post by timboellis on 2008-04-21
spot on thanks

---

