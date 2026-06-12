---
title: "Cannot get cron to do anything"
date: 2007-10-21
forum: General Help
---

### Post by kaw22 on 2007-10-21
Hi there,

I've read loads of tutorials, but just cannot seem to make cron work at all.

This is what I'm trying just to get any response from Cron:
I've logged in as root and run crontab -e, this is the output:
[I][B]SHELL=/bin/sh
PATH=/usr/sbin:/usr/local/bin:/sbin:/bin:/us:/var/www
1 * * * * ls /var/www > /var/www/ls.log[/B][/I]

Nothing ever happens, what could I be doing wrong?

Thank you,
kaw22

---

### Post by kast on 2007-10-21
not sure what your trying to do, but here is a snip it of my Crontab

# m h  dom mon dow   command

0 * * * * cd /media/backup/cam && ./Cam_Cap >/dev/null 2>/dev/null

0 1 * * * cd /usr/bin && ./Backup >/dev/null 2>/dev/null

---

### Post by kaw22 on 2007-10-21
I just want to see if Cron works. I'm trying to do this my executing "ls /var/www" and adding it to a logfile.

I really don't care what command I have to run, I just need to see Cron actually do something.

---

### Post by kast on 2007-10-21
ok then just try 

**cat /var/log/user.log > /home/yourname/Desktop/user2.log**

---

### Post by kaw22 on 2007-10-21
Ok, I tried this:

[B]SHELL=/bin/sh
PATH=/usr/sbin:/usr/local/bin:/sbin:/bin:/us:/var/www:/p
1 * * * * cat /var/log/user.log > /tmp/user2.log[/B]

now it's creating the user2.log file. wohoo. :)
Now I need it to run this command every 5 minutes: "php /var/www/script.php"
When I execute it manually it works fine, but Cron doesn't do it. Could it have something to do with the directory it's in?

---

### Post by kaw22 on 2007-10-21
Ok, this is really odd.
Changing the logfilename doesn't work:

SHELL=/bin/sh
PATH=/usr/sbin:/usr/local/bin:/sbin:/bin:/us:/var/www
1 * * * * cat /var/log/user.log > /tmp/test.log

test.log doesn't get created, and the user2.log was never modified even though it should be updated every minute. I'm confused??

EDIT:
I see the problem, it is only created xx: x1 every hour. My bad. :)

---

### Post by kast on 2007-10-21
what is all this 
SHELL=/bin/sh
PATH=/usr/sbin:/usr/local/bin:/sbin:/bin:/us:/var/ www

your putting in there?

the command to run your php every 5 minutes should be
[B]
5 * * * *  cd /var/www/ && ./script.php[/B]

---

### Post by kast on 2007-10-21
if your looking to update your file and keep the existing info in there you have to use >> to append  just > will erase everything in there and add the new.

---

### Post by kast on 2007-10-21
sorry

5 * * * * cd /var/www && ./script.php

need to drop the following / i left at the end of the www directory

---

### Post by kaw22 on 2007-10-21
Thank you my friend! [-o<
Been strugling with this for over a week. :)

This is the only thing I have in my crontab -e now:
***/5 * * * * cd /var/www && ./on01.php > /tmp/php.log**

And it works, it's executing the phpscript and I can see with **ps** that it does what it's supposed to. However if I have to do it manually I have to run the script like this: **php on01.php**. If I just do ./on01.php it gives this error:
[B]./on01.php: line 1: ?php: No such file or directory
./on01.php: line 2: syntax error near unexpected token `('
./on01.php: line 2: `echo shell_exec('/var/www/hlds01 start');'[/B]

So I'm a bit confused how Cron pulls it off??

I am btw not getting anything in the logfile, I can just see on the timestamp that it gets updated.

---

### Post by HermanAB on 2007-10-21
Cron has a very limited environment, for security reasons.  Therefore, in order for cron to find a command, you have to supply the FULL path to everything: 
/bin/cat /etc/fstab > /tmp/fstab.copy

This is a common newb gotcha.

Cheers,

H.

---

### Post by kast on 2007-10-21
odd, do you mind posting the first few lines of that script?

---

### Post by kaw22 on 2007-10-21
This is the full script:
[B]<?php
echo shell_exec('/var/www/hlds01 start');
?>[/B]

and the output I recieve when I run it manually (php on01.php):
[B]root@server:/var/www# php on01.php
Server has been started![/B]

---

### Post by BackwardsDown on 2007-10-21
That means that Cron doesn't pull it off too.

So running:
*/5 * * * * cd /var/www && php on01.php > /tmp/php.log
should pull it off

---

### Post by kaw22 on 2007-10-21
Brilliant! \\:D/
Must have started it manually then and forgot to turn it off. #-o

Thank you very much for all your help, I appreciate it alot!! :)

---

