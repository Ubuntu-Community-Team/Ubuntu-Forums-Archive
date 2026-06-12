---
title: "Crontab issues"
date: 2008-05-21
forum: General Help
---

### Post by SuperCzar on 2008-05-21
I have created a server monitoring script that runs via cron and updates some logs every 15 minutes.  I plan to use it when I am having some server issues so I can track it.

I also have a web interface that works with the logs.

However, I want to rotate the logs every day just after midnight due to some complexities in the software and my poor date rollover handling.

here is the crontab line that should roll over the log:
```
05 00 * * * logrotate -f /usr/share/logrotate/memory.conf
```

I see this in syslog
```
syslog.0:May 21 00:05:01 thirdrate /USR/SBIN/CRON[21900]: (root) CMD (logrotate -f /usr/share/logrotate/memory.conf)
```

But it seems to do nothing.

however doing the following, does work
```
sudo 'logrotate -f /usr/share/logrotate/memory.conf'
```

I've searched but didnt come up with anything that seems to be a syntactical issue with the line.

Whats wrong?

---

### Post by lemming465 on 2008-05-21
If you put the line in /etc/crontab or /etc/cron.d, there is an extra 6th field for which user should run the command.  Try ```
05 00 * * * root logrotate -f /usr/share/logrotate/memory.conf
```

---

### Post by SuperCzar on 2008-05-23
I tried adding root in where you suggested, and it has no effect.

I have another cron line that works fine.

```
10-55/15 * * * * php -q /usr/script/memory.php
```

The only major difference is that one cron runs multiple times an hour, not once per day. Syntactically they seem to be the same.

---

### Post by SuperCzar on 2008-05-27
Bump for the problem still existing.

---

### Post by Monicker on 2008-05-27
Cron jobs generate emails for any output from the job, which may contain useful error messages.  These messages go to the local user whose account rant the cron job.

I would suggest configuring your email client to check mail at localhost for your username, and seeing if you can view those messages.

I usually do it via the console using mutt, but evolution or thunderbird will work just as well.

---

### Post by SuperCzar on 2008-05-27
> **Monicker said:**
> These messages go to the local user whose account rant the cron job.

I would suggest configuring your email client to check mail at localhost for your username, and seeing if you can view those messages.

I have read this, and unfortunately, I am chasing down another issue with my local email server that is bouncing emails to root at the local hostname.

Is there a way to redirect this output to a logfile? ( I would prefer this anyways, as parsing text is easier to me than relying on email messages )

---

### Post by Monicker on 2008-05-27
Try this

```
10-55/15 * * * * php -q /usr/script/memory.php > /home/username/cron.txt 2>&1 
```

---

### Post by SuperCzar on 2008-05-27
No output.

I used the following line in crontab
```
39 22 * * * logrotate -f /usr/share/logrotate/memory.conf > /home/username/logrotate.log 2>$1
```

The following outputs "mark" successfully into the file.
```
39 22 * * * echo "mark" > /home/username/logrotate.log
```

---

### Post by andrew.46 on 2008-05-27
Hi,

Rotation of logfiles might be better done from the file /etc/logrotate.conf and then run as cron. Do you have any settings in there for your logs? My apologies if you have already looked at this option :-).

          Andrew

---

### Post by SuperCzar on 2008-05-27
> **andrew.46 said:**
> Rotation of logfiles might be better done from the file /etc/logrotate.conf. My apologies if you have already looked at this option

I have looked at this option, and would prefer it for simplicity's sake, but using it was rotating my logs at a time other than just after midnight.

If there is a way to control the time that the log is rotated, I would much prefer to handle the rotation this way.

---

### Post by andrew.46 on 2008-05-27
Hi:

> **SuperCzar said:**
> I have looked at this option, and would prefer it for simplicity's sake, but using it was rotating my logs at a time other than just after midnight.

It is possibly not the best solution but you could change the time that /etc/cron.daily runs by altering /etc/crontab. 

           Andrew

---

### Post by SuperCzar on 2008-05-27
> **andrew.46 said:**
> It is possibly not the best solution but you could change the time that /etc/cron.daily runs by altering /etc/crontab. 

No, probably not the best solution, I believe it is generally advised to reduce the number of operations that occur at midnight, unfortunately, this is the best way that I can find to execute this log rollover.

I remedied my local mail delivery issue (a problem with /etc/mailname and my /etc/aliases files) and will wait to see what logs appear when the script is due to run.

Eventually I found that for some reason it was not executing due to a path issue.

/usr/sbin is not in the default path. I had tried editing the cron line to use /usr/bin/logrotate, but did not realize that this is not the real location of logrotate.

It appears that the problem is solved. I will know for sure in 17 minutes.

---

