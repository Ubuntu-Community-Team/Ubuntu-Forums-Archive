---
title: "How do I make Crontabs actually run?"
date: 2008-05-16
forum: General Help
---

### Post by wh33t on 2008-05-16
I have a crontab that looks like

```
tristan@MrBackup:~/currentBackup/Tristan$ crontab -l
# m h  dom mon dow   command
01 * * * * php /home/tristan/backupScript/backupCHBA.php

```

Do I not understand crontabs? To me that says it should run every hour at :01 minutes. 

If I run 
```
php /home/tristan/backupScript/backupCHBA.php
```
by itself, it works correctly. But the cron job never seems to run?

Both the sudo crontab, and the crontab both have the same contents. Neither works. Please help!

---

### Post by Monicker on 2008-05-16
It may be that cron is running using a different $PATH variable than your normal user account.  Try specifying the full path to the php binary.  You can also install the mutt console mail client, and check your local email.  Any output from a cron job, including errors, is automatically emailed to your local account.

---

### Post by wh33t on 2008-05-16
OOOH, that's a good suggestion. How do I check the $Path thingy.

---

### Post by Monicker on 2008-05-16
I think the default path is specified in the file /etc/crontab.  You could also do a test cron job of "echo $PATH > /tmp/cronpath.txt".  The path shouldn't matter if you explicity tell it the full path to your binary: /path/to/php /home/username/foo.php.

---

### Post by wh33t on 2008-05-16
> **Monicker said:**
> I think the default path is specified in the file /etc/crontab.  You could also do a test cron job of "echo $PATH > /tmp/cronpath.txt".  The path shouldn't matter if you explicity tell it the full path to your binary: /path/to/php /home/username/foo.php.

Don't suppose you know the path of the PHP binary do you?

---

### Post by Monicker on 2008-05-16
> **wh33t said:**
> Don't suppose you know the path of the PHP binary do you?

Not offhand.

Run this from terminal:

```
which php
```

---

### Post by wh33t on 2008-05-16
Sweet. Didn't know about which.

```

tristan@MrBackup:/$ which php
/usr/bin/php

```

Thanks.

---

### Post by wh33t on 2008-05-16
Ok... it appears to have run once and once only. This is driving me nuts. The crontab looks as follows.

```

tristan@MrBackup:~/currentBackup/Tristan$ crontab -l
# m h  dom mon dow   command
01 * * * * /usr/bin/php /home/tristan/backupScript/backupCHBA.php

```

---

### Post by amingv on 2008-05-16
Something I find useful to squash crontab errors is to dump the command output to a file to check how it went, your line would go something like this:

```
01 * * * * /usr/bin/php /home/tristan/backupScript/backupCHBA.php > /home/tristan/cron.log
```

After the minute is over, check the cron.log file and it should be easy to know what's going on.

---

### Post by wh33t on 2008-05-16
Good idea. Ill try that.

---

### Post by wh33t on 2008-05-16
```
Warning: fopen(/home/tristan/backupScript/1210989661.Friday.May.16.7.01pm.txt): failed to open stream: Permission denied in
/home/tristan/backupScript/backupCHBA.php on line 7

can't open file

```

So... the script is failing upon trying to create my timestamp file.. So maybe the crontab is being run as low privledged user..?

---

### Post by amingv on 2008-05-17
Your script only runs with as many privileges the user to which the crontab file belongs has.

Does your script need root privileges for anything?

If so, you can create cron jobs for root like this:

```
sudo crontab -uroot -e
```

Consider the security risks you may stumble with first.
If you decide to go for this approach, then make root the owner of your script and remove read/write/execute privileges to all other users, you don't want anyone putting nasty stuff in such a code.

---

### Post by wh33t on 2008-05-17
Make root the owner? Isn't root the owner of the entire machine?

---

### Post by wh33t on 2008-05-19
Just wanted to say it works now becuase of chown.

Thanks for all your help.

---

### Post by kevdog on 2008-05-19
When using chown -- which owner or group did you give permissions to?

---

