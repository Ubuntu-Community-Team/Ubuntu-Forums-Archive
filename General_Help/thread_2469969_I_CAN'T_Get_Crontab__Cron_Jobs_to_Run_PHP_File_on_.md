---
title: "I CAN'T Get Crontab / Cron Jobs to Run PHP File on Sever"
date: 2021-12-15
forum: General Help
---

### Post by aaronesteban on 2021-12-15
I am able to run the php script and the script will send bulk email as it's supposed to when I manually load the script in my browser by visiting the URL, but after setting the Crontab file to run the directory, it just can't run any cron job on it.


I have tried the following commands in my crontab file:


*/1 * * * * /var/www/mywebsite.com/autoresponder/inc/crons/aarons_autoresponder_1_send.php


*/1 * * * * php /var/www/mywebsite.com/autoresponder/inc/crons/aarons_autoresponder_1_send.php


*/1 * * * * /user/bin/php /var/www/mywebsite.com/autoresponder/inc/crons/aarons_autoresponder_1_send.php


*/1 * * * * /user/bin/php -f /var/www/mywebsite.com/autoresponder/inc/crons/aarons_autoresponder_1_send.php > /tmp/result


etc.


NONE of them will run! But I find this to be rather strange because I've been able to run other files that query the mysql database and send emails when I tested it before on this same server around a month ago. I don't know exactly what's so different this time around.


I have all permissions set correctly I believe. I've set the directory to CHMOD 755 to read, write, & execute in this file directory/path, but still, to no avail.

---

### Post by TheFu on 2021-12-16
The file permissions must be correct - for scripts, they must be readable and have execute permissions. The directory permissions only matter to allow read access to the files, nothing more.
**AND**
the environment must be correct.  cron doesn't bring much environment with it. It is very different from an interactive session with a userid.

To troubleshoot the difference in the environment, create to files, each holding the environment.
```
env > /tmp/session.env
```
and put this command into a crontab task:
```
env > /tmp/cron.env
```

Now, compare those two files.  What's different that your php stuff needs? That is what needs to be set in the php programs before they will work.  Don't just set everything, since that will be bad too. Set only the things required.

---

### Post by aaronesteban on 2021-12-16
Well, I got it to work using the 'wget -O /dev/null', but this seems to be the only other way to get the cron to trigger the file. It seems to be some sort of permissions while trying to execute the usual ways. Is 'wget' less secure and what about performance wise? Should I just stick to the 'wget' command or continue trying to get the usual way for triggering?
 


> **TheFu said:**
> The file permissions must be correct - for scripts, they must be readable and have execute permissions. The directory permissions only matter to allow read access to the files, nothing more.
**AND**
the environment must be correct.  cron doesn't bring much environment with it. It is very different from an interactive session with a userid.

To troubleshoot the difference in the environment, create to files, each holding the environment.
```
env > /tmp/session.env
```
and put this command into a crontab task:
```
env > /tmp/cron.env
```

Now, compare those two files.  What's different that your php stuff needs? That is what needs to be set in the php programs before they will work.  Don't just set everything, since that will be bad too. Set only the things required.

---

### Post by TheFu on 2021-12-16
> **aaronesteban said:**
> Well, I got it to work using the 'wget -O /dev/null', but this seems to be the only other way to get the cron to trigger the file. It seems to be some sort of permissions while trying to execute the usual ways. Is 'wget' less secure and what about performance wise? Should I just stick to the 'wget' command or continue trying to get the usual way for triggering?

No clue what wget has to do with anything.

---

