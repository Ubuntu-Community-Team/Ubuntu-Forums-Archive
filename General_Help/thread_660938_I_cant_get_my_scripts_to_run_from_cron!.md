---
title: "I cant get my scripts to run from cron!"
date: 2008-01-07
forum: General Help
---

### Post by rugbert on 2008-01-07
I have to back up this server every other night so I added these lines to the crontab:

> 
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
0  3    * * 2   root    tar cvpzf /backupmnt/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backupmnt --exclude=/mnt --exclude=/media --exclude=/sys /
0  3    * * 4   root    tar cvpzf /backupmnt/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backupmnt --exclude=/mnt --exclude=/media --exclude=/sys /
0  3    * * 6   root    tar cvpzf /backupmnt/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backupmnt --exclude=/mnt --exclude=/media --exclude=/sys /
#



So this should run every other morning at 3 am right?

it does not tho. I can run that line from the command line and it runs just find, or throw it into a script and run the script and it works too. But even if I put it in a script and put in in cron.daily it just wont run.

Ultimately I would like to tweak this more but at the moment it's not running and I really need it to.

edit - I also tried adding /usr/sbin/ in front of tar in case it couldn't find the utility but that didn't work either.


also - I have to run this script
> 
cp /var/log/apache2/* /backupmnt/apache2
rm -rf /var/log/apache2
mkdir /var/log/apache2


everyday or else the apache server crashes (havent figured that out yet) buuuut the folder contents of var/log/apache2 wont copy. at first I tried cp -r but that didn't help. The rest of the script runs fine but the first line wont!

---

