---
title: "zbackup"
date: 2015-01-29
forum: General Help
---

### Post by lance bermudez on 2015-01-29
Was reading [http://www.linuxjournal.com/content/ideal-backups-zbackup](http://www.linuxjournal.com/content/ideal-backups-zbackup) not sure what the below means? as in I like their idea of backing up but I want to do only certin directories like /home/user/Documents /home/user/Videos

#year-month/day/time
export DATEDIR=`date "+%Y-%m/%d/%H:%M"`
#place storing backups of directorys
mkdir -p /home/zbackup/backups/$DATEDIR
tar -c /home/user/ | zbackup --silent backup /home/zbackup/backups/$DATEDIR/files.tar
cat /home/user/database.sql | zbackup backup /home/zbackup/backups/$DATEDIR/database.sql

also how do I add compresstoin to the files using zbackup?

---

### Post by nerdtron on 2015-01-30
> **lance bermudez said:**
> Was reading [http://www.linuxjournal.com/content/ideal-backups-zbackup](http://www.linuxjournal.com/content/ideal-backups-zbackup) not sure what the below means? as in I like their idea of backing up but I want to do only certin directories like /home/user/Documents /home/user/Videos

#year-month/day/time
export DATEDIR=`date "+%Y-%m/%d/%H:%M"`
#place storing backups of directorys
mkdir -p /home/zbackup/backups/$DATEDIR
tar -c /home/user/ | zbackup --silent backup /home/zbackup/backups/$DATEDIR/files.tar
cat /home/user/database.sql | zbackup backup /home/zbackup/backups/$DATEDIR/database.sql

also how do I add compresstoin to the files using zbackup?

Actually the comments on the script says what they do.
> export DATEDIR=`date "+%Y-%m/%d/%H:%M"` = mean it will set DATEDIR variable as 2015-01/29/21:55

> mkdir -p /home/zbackup/backups/$DATEDIR = means it will create a backup directory with the date format (shown above) 

> tar -c /home/user/ | zbackup --silent backup /home/zbackup/backups/$DATEDIR/files.tar
cat /home/user/database.sql | zbackup backup /home/zbackup/backups/$DATEDIR/database.sql
= This will backup the whole home folder named "user" and it will be passed to zbackup to do it's thing and save to the file named fils.tar on the directory with the current date (previous command on date)

cat /home/user/database.sql | zbackup backup /home/zbackup/backups/$DATEDIR/database.sql
> same as the above command, only this one is a single file (not folder)


So I think to answer your question, to backup only certain directories, you need to edit the tar command like:
```
tar -c /home/user/Documents | zbackup --silent backup /home/zbackup/backups/$DATEDIR/Documents.tar
```

As for compression, I think you have two options here.

First, you can try adding the compression option on the tar command (the -z switch), like this:
```
tar -zc /home/user/Documents | zbackup --silent backup /home/zbackup/backups/$DATEDIR/Documents.tar.gz
```

Or you can try to compress the file after zbackup has processed it. In this case you need to add another command after zbackup.
```
tar -c /home/user/Documents | zbackup --silent backup /home/zbackup/backups/$DATEDIR/Documents.tar
gzip /home/zbackup/backups/$DATEDIR/Documents.tar
```

---

