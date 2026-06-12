---
title: "My 3 Step Backup System"
date: 2008-04-28
forum: General Help
---

### Post by nami on 2008-04-28
Dear Experts,

I am trying to create a cronjob which uses rdiff-backup, truecrypt, and wput to give me encrypted backups on a remove server, but it does not seem to work.

Here is the script:

# at the beginning of every hour use rdiff-backup to create the backup files
00 * * * * rdiff-backup /var/www/ /home/nami/Desktop/backup

# copy the back files into a truecrypt file
01 * * * * cp --remove-destination -r /home/nami/Desktop/backup /media/truecrypt1

# upload the truecrypt file to a remove ftp server
02 * * * * wput truecrypt1 [ftp://[user]:](ftp://[user]:)[pass]@www.some_external_server.com/mybackup/

Anyone know why this is not working?  If this is not a good method, please give details for a better method.

Thanks

---

### Post by Oldsoldier2003 on 2008-04-28
> **nami said:**
> Dear Experts,

I am trying to create a cronjob which uses rdiff-backup, truecrypt, and wput to give me encrypted backups on a remove server, but it does not seem to work.

Here is the script:

# at the beginning of every hour use rdiff-backup to create the backup files
00 * * * * rdiff-backup /var/www/ /home/nami/Desktop/backup

# copy the back files into a truecrypt file
01 * * * * cp --remove-destination -r /home/nami/Desktop/backup /media/truecrypt1

# upload the truecrypt file to a remove ftp server
02 * * * * wput truecrypt1 [ftp://[user]:](ftp://[user]:)[pass]@www.some_external_server.com/mybackup/

Anyone know why this is not working?  If this is not a good method, please give details for a better method.

Thanks
general trouble shooting for any cron based system of scripts:
the first step is to be sure that each command works as expected when invoked from a shell. If it doesn't you need to consider what needs to be done with error messages and other output.

---

### Post by nami on 2008-04-28
The first part is ok, the second part cp does not seem to like rdiff-backup or rdiff-backup does not seem to like the truecrypt file because it copies the files into the truecrypt file, but it does not create the extra files rdiff-backup normally creates.

---

