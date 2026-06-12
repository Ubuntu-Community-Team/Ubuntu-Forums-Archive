---
title: "Need help trouble shooting why cron job is not running."
date: 2015-12-18
forum: General Help
---

### Post by nzdreamer55 on 2015-12-18
Hello everyone,

I am using ubuntuMate on a raspberry pi.  I have a script that I created and is stored at /usr/bin/script.  This script runs rsync and fetches files from a server.  I can run the script from anywhere without su rights.  When I entered it into the crontab it looks like this

```
*/15 * * * * rscript
```

When I check the /var/log/syslog I see entries every 15 minutes that say something like this

```
Dec 18 09:00:01 raspberry CRON [7599]: (pi) CMD (rscript)
Dec 18 09:00:01 raspberry CRON [7592]: (CRON) info (No MTA installed, discarding output)
```

So it looks like it thinks it is running the script but I am not getting any files transferred.  If I run the script manually, files get transferred down.

So why does cron think that it is running the script but it really isn't?

---

### Post by QDR06VV9 on 2015-12-18
The [COLOR=#000000][FONT=Ubuntu Mono](No MTA installed, discarding output) might give you some insight to this..
[/FONT][/COLOR]Linux uses mail for sending notifications to the user. Most Linux distributions have an mail service (including an MTA) installed. Ubuntu doesn't though.
You can install a mail service, postfix for example, to solve this problem.
```
sudo apt-get install postfix

```
postfix is the most widely used mail server for linux.
More Info on postfix
[https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-12-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-12-04)

---

### Post by sandyd on 2015-12-18
> **nzdreamer55 said:**
> Hello everyone,

I am using ubuntuMate on a raspberry pi.  I have a script that I created and is stored at /usr/bin/script.  This script runs rsync and fetches files from a server.  I can run the script from anywhere without su rights.  When I entered it into the crontab it looks like this

```
*/15 * * * * rscript
```

When I check the /var/log/syslog I see entries every 15 minutes that say something like this

```
Dec 18 09:00:01 raspberry CRON [7599]: (pi) CMD (rscript)
Dec 18 09:00:01 raspberry CRON [7592]: (CRON) info (No MTA installed, discarding output)
```

So it looks like it thinks it is running the script but I am not getting any files transferred.  If I run the script manually, files get transferred down.

So why does cron think that it is running the script but it really isn't?

If you don't want to install a mailserver, you can use
```

*/15 * * * * rscript >> /tmp/rscript.log 2>&1

```

The output of rscript will be logged into /tmp/rscript.log where you can check the output.

---

### Post by nzdreamer55 on 2015-12-18
> **runrickus said:**
> The [COLOR=#000000][FONT=Ubuntu Mono](No MTA installed, discarding output) might give you some insight to this..
[/FONT][/COLOR]

Thanks runrickus.  So the issue is that my script isn't running not that I don't have a mail server setup on my raspberry pi.  Can you help me with why my script won't run?  If you think it is because of the mail server then I can install that, but that seems weird.

---

### Post by nzdreamer55 on 2015-12-18
> **sandyd said:**
> 
The output of rscript will be logged into /tmp/rscript.log where you can check the output.

Great.  Will do this and see what happened.  Thanks.

Can you tell me what the &1 means?

2>&1

---

### Post by QDR06VV9 on 2015-12-18
> **sandyd said:**
> If you don't want to install a mailserver, you can use
```

*/15 * * * * rscript >> /tmp/rscript.log 2>&1

```

The output of rscript will be logged into /tmp/rscript.log where you can check the output.
Thanks sandyd :D 
I Blame lack of Caffeine..I should have offered that option..but thanks for picking up my lack of options.;)
Best Regards

---

### Post by QDR06VV9 on 2015-12-18
> **nzdreamer55 said:**
> Great.  Will do this and see what happened.  Thanks.

Can you tell me what the &1 means?

2>&1
**2>&1** says to send standard error to where ever standard output is being redirected as well.

---

### Post by nzdreamer55 on 2015-12-18
OK so I got the output which says

```
/usr/bin/scripts/rscript1: Line 4: rsync: command not found
```

The scrips looks like this

```
#!/bin/bash
#rscript
PATH=/usr/bin/scripts
rsync -vsHAXxr --progress --...................
```

Is it that I have specified a path that does not include where rsync is located?

---

### Post by sandyd on 2015-12-18
> **nzdreamer55 said:**
> OK so I got the output which says

```
/usr/bin/scripts/rscript1: Line 4: rsync: command not found
```

The scrips looks like this

```
#!/bin/bash
#rscript
PATH=/usr/bin/scripts
rsync -vsHAXxr --progress --...................
```

Is it that I have specified a path that does not include where rsync is located?

Yes, bash searches in the folders specified by the $PATH variable for the programs that you do not call with a full path. If you absolutely need to set that path, use "/usr/bin/rsync" instead of "rsync"

---

### Post by QDR06VV9 on 2015-12-18
I am tied up for just few minutes(Very Sorry but Important)
See if you can make use of this in the meantime  [http://www.linuxcommand.org/man_pages/rsync1.html](http://www.linuxcommand.org/man_pages/rsync1.html)
Be back to check in about 40 mins..

---

### Post by nzdreamer55 on 2015-12-18
So having the path in the script is what was the issue.  Thanks for the help :-)

---

### Post by sandyd on 2015-12-18
Glad to see its working :)

---

