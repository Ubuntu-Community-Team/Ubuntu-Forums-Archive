---
title: "Need logrotate help"
date: 2015-06-23
forum: General Help
---

### Post by Robing Goodfellow on 2015-06-23
I have a log that needs to be compressed at a 1130, am currently using:

```
#!/bin/bash

input=/var/opt/SVP/svp-server/log/se.log
output=/var/opt/SVP/svp-server/log/
logfile=""
cd $input
name=$(date '+%y-%m-%d')
filename=se.log
filename2=se2.log
logfile=$output$filename$name".tar.gz"
mv $filename $filename2 
# touch $filename
tar -cvzpf $logfile $filename2
rm $filename2
exit 0
```

and a crontab entry of "30 11 * * * /path to script/script" because I just can't seem to get my head wrapped around the logrotate function and I needed a quick fix while I figured it out.

I've read numerous tutorials and discussions on logrotate on the web, but still haven't quite got it. The above script is working fine, but now I want to delete the tars that are greater than 10 days old as part of it, and everything says I should be using logrotate. Hummph. The key is it can't delete other log.tar files besides the se.log tars, and all other log files are rotated using a java function at different times, which I can't mess with. So to get the se.log to be rotated each day at 1130 and have the older than 10 day tars deleted, would I:

add the following to logrotate.conf:

```
/var/opt/SVP/svp-server/log/se.log {
    missingok
    daily
    rotate 10
    dateext
    compress
    maxage 10
}
```

and then just add the following to crontab:

```
30 11 * * * 
```

and this is where I get lost. I know I'm supposed to put the path to a script and the script name at the end of the crontab line, but if I'm using logrotate, and only want to execute the rotate on the se.log at 1130, what the heck should I put here? Was I better off with the bash script, and if so, how would you recommend I write so that it only deletes the se.log.tar's greater than 10 days? I suspect it would be something along the lines of find with mtime, but sure could use a nudge in the direction of the right way to go on this.

regards, Richard

---

### Post by TheFu on 2015-06-23
I think you want ```

/var/opt/SVP/svp-server/log/*.log {
```

Also, you may need a pre-logrotate/post-logrotate settings. Should be plenty of examples in /etc/logrotate.d/

For example, nginx needs to be kill -HUP'd to get it to switch to the new logfile. Otherwise, it will keep writing to nginx.log.1 after the rotation happens.

As to when the rotation happens ... there are about 4 different places that control cron. Be certain that your new setup doesn't conflict the any existing setting.

---

### Post by Robing Goodfellow on 2015-06-23
But if I use .../log/*.log {

won't that run it on every .log in the directory? That's exactly what I don't want to do, this is kind of a shared system and I can't touch anything but se.log.

---

### Post by matt_symes on 2015-06-23
Hi

You can editb the file

```
/etc/crontab
```

to run log rotate and*, *consequently*, all **other **daily cron tasks* at 11.30.

Look for the line that says...

```
**25 6**    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
```

...and edit the numbers in bold to the time that you require. 

As you can see, they default to 6.25am.

As long as running *all* *the daily cron* tasks at 11.30 is not a problem then this should work for you.

Kind regards

---

### Post by Robing Goodfellow on 2015-06-23
Thanks, but again, I can't do that, I'm only allowed to manipulate that one log. From the guidance I'm getting here I suspect it's going to have to be an addition to the existing bash script as opposed to using logrotate.

---

### Post by matt_symes on 2015-06-23
Hi

> **Robing Goodfellow said:**
> Thanks, but again, I can't do that, I'm only allowed to manipulate that one log. From the guidance I'm getting here I suspect it's going to have to be an addition to the existing bash script as opposed to using logrotate.

You should be able to use log rotate on that log.

From /etc/crontab, if it's not going to run anacron it runs all the scripts in /etc/cron.daily.

```
( cd / && run-parts --report /etc/cron.daily)
``` 

One of those scripts is /etc/cron.daily/logrotate.

```

root@matthew-laptop:~# cat /etc/cron.daily/logrotate 
#!/bin/sh

# Clean non existent log file entries from status file
cd /var/lib/logrotate
test -e status || touch status
head -1 status > status.clean
sed 's/"//g' status | while read logfile date
do
    [ -e "$logfile" ] && echo "\"$logfile\" $date"
done >> status.clean
mv status.clean status

test -x /usr/sbin/logrotate || exit 0
**/usr/sbin/logrotate /etc/logrotate.conf**
root@matthew-laptop:~#
```

Why not create your own logrotate configuration file specifically for that file (as you have done) you need to rotate and call it from cron using /usr/sbin/logrotate.

Kind regards

---

### Post by Robing Goodfellow on 2015-06-23
Now that's one I didn't think of. Sounds like just the ticket, thanks Matt.

regards, Richard

---

### Post by Robing Goodfellow on 2015-06-23
Does this look like it would work? This is my logrotate file commented like crazy so that if I get hit by a bus my co-worker knows what to do:

```
#!/bin/sh

# put this as logrotate in /home/engineering/TEAM/scripts


# add the following to /etc/logrotate.conf:
# /var/opt/SVP/svp-server/log/se.log {
#   copytruncate
#   rotate 10
#   compress
#   maxage 10
#   missingok
#}
#
# do crontab -e
# i
# at bottom of file, insert the following:
# 30 11 * * * /home/engineering/TEAM/scripts/logrotate
#
# then:esc, :wq




/usr/sbin/logrotate /etc/logrotate.conf


EXITVALUE=$?


if [ $EXITVALUE != 0 ]; then
    /usr/bin/logger -t logrotate "ALERT exited abnormally with [$EXITVALUE]"
fi
exit 0
```

---

### Post by TheFu on 2015-06-23
> **Robing Goodfellow said:**
> But if I use .../log/*.log {

won't that run it on every .log in the directory? That's exactly what I don't want to do, this is kind of a shared system and I can't touch anything but se.log.

My mistake.  We put multiple log files for the same overall system into the same directory and want **all** the log files there rotated together. Because of the location of example log file, I'd made the same assumption. Sorry.

---

### Post by matt_symes on 2015-06-23
Hi

> **Robing Goodfellow said:**
> Does this look like it would work? This is my logrotate file commented like crazy so that if I get hit by a bus my co-worker knows what to do:

```
#!/bin/sh

# put this as logrotate in /home/engineering/TEAM/scripts


# add the following to /etc/logrotate.conf:
# /var/opt/SVP/svp-server/log/se.log {
#   copytruncate
#   rotate 10
#   compress
#   maxage 10
#   missingok
#}
#
# do crontab -e
# i
# at bottom of file, insert the following:
# 30 11 * * * /home/engineering/TEAM/scripts/logrotate
#
# then:esc, :wq




/usr/sbin/logrotate /etc/logrotate.conf


EXITVALUE=$?


if [ $EXITVALUE != 0 ]; then
    /usr/bin/logger -t logrotate "ALERT exited abnormally with [$EXITVALUE]"
fi
exit 0
```

I was thinking something more along the lines of this but you will have to test this to make sure that it works.

```
sudo vim /home/engineering/TEAM/scripts/se_logrotate.conf
```

I'm using sudo above to ensure it's owned by root.

Add this to the file.

```
/var/opt/SVP/svp-server/log/se.log {
   copytruncate
   rotate 10
   compress
   maxage 10
   missingok
}
```

Save as normal. I have not checked your syntax above or that anything else needs to be added.

Edit root's crontab file.

```
sudo crontab -e
```

Add the line

```
30 11 * * * /usr/sbin/logrotate /home/engineering/TEAM/scripts/se_logrotate.conf
```

That was my basic thought but you will want to check that i have not missed anything as i am not in the office or at home.

**edit:**

Some thoughts. I think if you put it in /etc/logrotate.d then it will also be called at 6.25am; not what you want.

Kind regards

---

### Post by Robing Goodfellow on 2015-06-23
I'll give that a try. Obviously won't know until tomorrow.

regards, Richard

---

