---
title: "Easy server backup script"
date: 2013-03-22
forum: General Help
---

### Post by strid3r on 2013-03-22
This script has saved my ass quite a few times, so I thought I'd share it
I'm running an Apache web server on /var/www and I often manage to screw things up.
Having backups is quite necessary when running a public website.

Here is the script and how to install it on your system.

First ssh into your server:

```
ssh -Y user@0.0.0.0 
```

Next open nano

```
sudo nano /bin/backup
```

and paste the following code:

```

#!/bin/bash
sudo tar -cvzf /var/www/backups/backup-$(date +"%Y-%m-%d").tar.gz --exclude=*.tar.gz --exclude=/var/www/backups /var/www > /var/www/backups/$(date +"%Y-%m-%d").log
### MAKE SURE YOU CHANGE "secretpassword" below or remember it :)
sudo zip /var/www/backups/backup-$(date +"%Y-%m-%d").tar.gz.zip -e -P secretpassword /var/www/backups/backup-$(date +"%Y-%m-%d").tar.gz
sudo find /var/www/backups/backup-2* -mtime +7 -exec rm -v {} \; | sudo tee -a /var/www/backups/del.log
## CHANGE "bzackup" to a mysql user and "sqlpassword" to the password for that user
mysqldump -u bzackup --password=sqlpassword --all-databases > /var/www/backups/database-$(date +"%Y-%m-%d").sql 2> /var/www/backups/db-$(date +"%Y-%m-%d").log
### MAKE SURE YOU CHANGE "secretpassword" below or remember it :)
sudo zip /var/www/backups/database-$(date +"%Y-%m-%d").sql.zip -e -P secretpassword /var/www/backups/database-$(date +"%Y-%m-%d").sql


# removes unprotected data
sudo rm /var/www/backups/backup-$(date +"%Y-%m-%d").tar.gz
sudo rm /var/www/backups/database-$(date +"%Y-%m-%d").sql



```

What this script does is create a backup of /var/www that looks something like /var/www/backups/backup-2013-03-22.tar.gz
The "-mtime +7" tells it to remove tar backups older than 7 days, since these tend to eat up space.
All outputs are recorded as logs with the corresponding date in /var/www/backups
The script puts these files in a password encrypted zip file with the password "secretpassword" so be sure to change it above.
It then makes an sql dump of all databases with a similar format of /var/www/backups/database-2013-03-22.sql
For this part, you need to create a mysql user if you don't want to use root (bzackup in the example)
Here is the mysql code:
```
CREATE USER 'bzackup'@'localhost';
GRANT SELECT , RELOAD , FILE , SUPER , LOCK TABLES , SHOW VIEW ON * . * TO  'bzackup'@'localhost';
```


What's great about this setup is I can just go to example.com/backups and download the sql and tar files if I need to make a local backup or move the site.



Now save this script and exit (hit Ctrl+O ... Ctrl +X)

Next make it executable and unreadable by others

```
sudo chmod 7500 /bin/backup
```



Now to do your first backup, just run:

```
sudo backup
```

To make this automatically backup every day add a cron entry

```
sudo crontab -e
```

Add the following to the bottom

```
0 0 * * * bash /bin/backup
```

Now Exit and Save and you should be Good to Go!   ;)


Oh right right, how do you get your files back once you blow your system? 

Here is the code:

```

#!/bin/bash
read -n1 -p "Enter 1 to restore web dir, 2 to restore mysql database, or 3 for both: " input
echo
case $input in  
  1) cd / ;
      read -p "Enter date of backup [YYYY-MM-DD]: " date;
      echo;
      read -s -p "Password for files: " pass ;
      echo;
      sudo unzip -P $pass /var/www/backups/backup-$date.tar.gz.zip -d /;
      sudo tar -xvzf backup-$date.tar.gz;
      sudo rm backup-$date.tar.gz;; 
  2) cd /var/www/backups;
      read -p "Enter date of backup [YYYY-MM-DD]: " date;
      echo;
      read -s -p "Password for files: " pass ;
      echo;
      sudo unzip -P $pass /var/www/backups/database-$date.sql.zip -d /;
      mysql -u bzackup --password=sqlpassword < database-$date.sql ;
      sudo rm database-$date.sql;;
  3) cd /var/www/backups ;
      read -p "Enter date of backup [YYYY-MM-DD]: " date;
      echo;
      read -s -p "Password for files: " pass ;
      echo;
      sudo unzip -P $pass /var/www/backups/backup-$date.tar.gz.zip -d /;
      sudo tar -xvzf backup-$date.tar.gz;
      sudo rm backup-$date.tar.gz;
      sudo unzip -P $pass /var/www/backups/database-$date.sql.zip -d /;
      mysql -u bzackup --password=sqlpassword < database-$date.sql ;
      sudo rm database-$date.sql;;
  *) echo "Please run program again and enter 1 2 or 3" ;; 
esac



```


Save it as /bin/restore and chmod the file like before . Be sure to also change the mysql password "sqlpassword" in the script above to the one that correlates with your user.

```
sudo nano /bin/restore
```

```
sudo chmod 7500 /bin/restore
```

Okay, that's all folks!  ):P

---

### Post by schragge on 2013-03-22
Just wondering two things

[list=1]
[*]Why would you set setuid, setgid, and sticky permission bits on your backup/restore scripts?
[*]Why would you compress tar with gzip if it were then put into a zip archive?
[/list]

---

### Post by strid3r on 2013-03-24
> 
Just wondering two things

1. Why would you set setuid, setgid, and sticky permission bits on your backup/restore scripts?
2. Why would you compress tar with gzip if it were then put into a zip archive?


Good questions

1. So no-one else can view the passwords
2. gzip and tar don't provide an easy alternative to encrypting the files

You could very well use openssl, the commands would be something like

to encrypt
cat /var/www/backups/backup-$(date +"%Y-%m-%d").tar.gz | openssl des3 -pass pass:secretpassword -salt > /var/www/backups/backup-$(date +"%Y-%m-%d").tar.gz.crypt

to decrypt
cat /var/www/backups/backup-$date.tar.gz.crypt | openssl des3 -d -pass pass:secretpassword -salt |tar -xvzf  /var/www/backups/backup-$(date +"%Y-%m-%d").tar.gz

---

