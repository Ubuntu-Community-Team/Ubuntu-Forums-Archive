---
title: "Cron Jobs / Crontab - NOT Able to Edit or Create File"
date: 2020-10-06
forum: General Help
---

### Post by aaronesteban on 2020-10-06
I try to edit the crontab file to create con jobs by using ssh "sudo crontab -e" and "crontab -e", but I keep getting the following error message (or as shown in the image below):

> no crontab for root - using an empty one
crontab: installing new crontab
"/tmp/crontab.C7Hy04/crontab":22: bad minute
errors in crontab file, can't install.


[IMG]https://i.ibb.co/qdN9b91/cant-edit-crontab-file.png[/IMG]


And the file path location "**/var/spool/cron/crontabs/**" folder is empty. Shouldn't there be a cron file of some type to edit?


So what I'm trying to do is create cron jobs to handle my Mautic cron tasks/jobs as shown below:


php /var/www/aaronsnewsletters.com/public_html/bin/console mautic:segments:update
php /var/www/aaronsnewsletters.com/public_html/bin/console mautic:campaigns:update
php /var/www/aaronsnewsletters.com/public_html/bin/console mautic:campaigns:trigger
php /var/www/aaronsnewsletters.com/public_html/bin/console mautic:iplookup:download
php /var/www/aaronsnewsletters.com/public_html/bin/console mautic:broadcasts:send
php /var/www/aaronsnewsletters.com/public_html/bin/console mautic:maintenance:cleanup --days-old=60 --no-interaction




Do I need to somehow reinstall the crontab setup or how do I get back to being able to edit with nano? At this point I'm not able to edit the main crontab file & nor do I know where it is located.


Thanks for any support.

---

### Post by TheFu on 2020-10-06
**crontab -e** is doing you a favor. It does some simple checks for valid crontab entries before allowing updates to the real files.  There are a number of different locations for cron files and at least 3 different formats for them.  When you use **crontab -e**, those crontabs end up in /var/spool/cron/crontabs/.  They are different from the master crontab in /etc/crontab.

Ok, so first tip. Never assume a PATH.  That means using "php" as the command isn't a good idea. Use the full path to the exact version of php you want used. Usually, it is bad to get the wrong version of a scripting interpreter, so this is a really good idea.  

For the /var/spool/cron/crontabs/ entries, here is the format. I put this into the top of the crontab file as a reminder, so I don't screw it up: 
```
# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  /path/to/command --arg1 --arg2 file1 file2 2>&1
0 0 * * * /u/thefu/bin/push_keepass_db.sh
```

The last line is the only non-comment and has an example that runs daily at midnight to do something.  When finished, I get an email about it.  If you don't setup an MTA, then you'll want to do something with the output from cron. If you don't, then /var/ will fill up with local mail.  cron jobs always send email if there is any output.  I like getting the output, so I know something important was done.  Many people prefer for the email only to be send with stderr output (errors) and to be quiet otherwise.
Here's probably something like you want:
```
3 5 * * 1 /usr/bin/php /var/www/aaronsnewsletters.com/public_html/bin/console mautic:segments:update 2>&1
```
On Mondays, at 5:03am, run that command and send both stdout and stderr to the same email as the crontab userid.

```
3 5 * * 1 /usr/bin/php /var/www/aaronsnewsletters.com/public_html/bin/console mautic:segments:update 2>&1 > /dev/null
```
this command will block all output. No email will happen. That's almost always a bad idea.

**sudo crontab -e** <<<----- that will access the root crontab in /var/spool/.....
**crontab -e** <<<----- that will access my crontab in /var/spool/.....

---

### Post by TheFu on 2020-10-06
Please don't post images for text. We aren't using Windows. Text is 10000x smaller and helpers can copy/paste/modify text but not images.  At least I wouldn't bother to touch any image.

---

### Post by SeijiSensei on 2020-10-07
If the scripts you want to run look like this:

```

#!/usr/bin/php
<?php
your php code here
?>

```

Then you can put them in /etc/cron.hourly|daily|weekly|monthly where they will be run with root privileges.  Another option is to write a bash script that runs the various commands in order:
```

#!/bin/bash

php /var/www/aaronsnewsletters.com/public_html/bin/console mautic:segments:update
php /var/www/aaronsnewsletters.com/public_html/bin/console mautic:campaigns:update
php /var/www/aaronsnewsletters.com/public_html/bin/console mautic:campaigns:trigger
php /var/www/aaronsnewsletters.com/public_html/bin/console mautic:iplookup:download
php /var/www/aaronsnewsletters.com/public_html/bin/console mautic:broadcasts:send
php /var/www/aaronsnewsletters.com/public_html/bin/console mautic:maintenance:cleanup --days-old=60 --no-interaction

exit 0

```
and just put that script in, say, /etc/cron.daily.

---

### Post by aaronesteban on 2020-10-18
Thanks for you support guys! Sorry, but I've been away working.

---

