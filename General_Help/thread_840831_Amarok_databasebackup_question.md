---
title: "Amarok database/backup question"
date: 2008-06-25
forum: General Help
---

### Post by dartmusic on 2008-06-25
I finally switched from the SQLite database to mySQL database and now Amarok is nearly perfect -- if only I could find a transcoding script (for transferring to an iPod) that actually works correctly, doesn't crash/hang, and/or has a decent interface for changing options (yeah, I know I want a lot!).  I have nearly 40k tracks, so most players choke when getting that high.  It still took 2 days to replaygain all of my music.  

My question is this: how or what do I back up to make sure that I don't lose all the work I've done.  Is the replaygain data saved into the tags of the songs?  What do I do if I decide to do a clean install (probably about the time that Intrepid is released)?

Any info or tips/tricks/etc. would be great!

Thanks.

---

### Post by logos34 on 2008-06-25
One thing I know: you want to save this file:
[FONT=monospace]
[/FONT]~/.kde/share/apps/amarok/collection.db

---

### Post by cariboo on 2008-06-25
You may want to backup your database, the way to do it is in a terminal type:

```
mysqldump -u <user> -p amarok > amarok.sql
```

<user> is the user your created for your database, you will be asked for a password, use the password you used when you created the database.

To restore the backup:

```
mysql -u <user> -p amarok < amarok.sql
```

Jim

---

### Post by p_quarles on 2008-06-25
I use this script from the Amarok Wiki (note that there are a few lines you have to fill in with your own details -- I've italicized those):
```
 #!/bin/sh
 # Backup the Amarok MySQL database
 # Version 2007-02-06-b, 
 # now "/bin/sh -> /bin/dash" compatible; backup files now named "amarok.mysql.tar.bz2"; ask before overwrite
 

 ######### CHANGE SETTINGS HERE #########
 # Location to place Amarok-database backups:
 BACKUP_BASE_DIR=~/backup
 
 # Name of MySQL-database:
 AMAROKDB_NAME=*amarok*
 
 # Username and password for Amarok-MySQL-database:
 AMAROKDB_USER=*amarok*
 AMAROKDB_PW=*db_user_password*
 
 # Location of amarokrc:
 AMAROKRC=~/.kde/share/config/amarokrc
 ######### END OF SETTINGS SECTION #########
 
 BACKUP_SUBDIRECTORY=`date +%Y-%m-%d`
 
 if [ ! -w $BACKUP_BASE_DIR -o ! -d $BACKUP_BASE_DIR ]
 then
   printf %b "\n\n $BACKUP_BASE_DIR doesn't exist or is not writable!\n\n"
   printf %b "STOP.\n\n"
   exit 1;
 fi
 
 if [ ! -r $AMAROKRC ]
 then
   printf %b "\n\n $AMAROKRC doesn't exist or Amarok is not installed!\n\n"
   printf %b "STOP.\n\n"
   exit 1;
 fi
 
 mkdir -p $BACKUP_BASE_DIR/amarok/$BACKUP_SUBDIRECTORY

                #using a temporary file in order not to overwrite an existing copy when the script is 
                #manually invoked a second time (e.g. right before restoration of existing backup of same date!)
 mysqldump -u $AMAROKDB_USER -p$AMAROKDB_PW $AMAROKDB_NAME -c -e --hex-blob > /tmp/amarok.mysql

 tar --remove-files -C /tmp -cvvjf /tmp/amarok.mysql.tar.bz2 amarok.mysql

 mv -i -v /tmp/amarok.mysql.tar.bz2 $BACKUP_BASE_DIR/amarok/$BACKUP_SUBDIRECTORY
 
 # The config file amarokrc will also be secured:
 cp -i -v $AMAROKRC $BACKUP_BASE_DIR/amarok/$BACKUP_SUBDIRECTORY

```

---

### Post by dartmusic on 2008-06-26
This is exactly what I was after.

Thanks!

---

