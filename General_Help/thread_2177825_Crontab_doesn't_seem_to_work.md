---
title: "Crontab doesn't seem to work"
date: 2013-09-30
forum: General Help
---

### Post by JNied on 2013-09-30
I've searched the forums and didn't find what I was looking for.  Sorry in advance if I simply missed it.

My problem is simple: cron doesn't work.  It doesn't matter which command I try, and I've read through several tutorials to no avail.

I've tried using crontab -e as well as manually editing /etc/crontab.

This is my entire crontab file:```
# /etc/crontab: system-wide crontab# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.


SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin


# m h dom mon dow user    command
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

* * * * * touch /tmp/touchtest.txt
* * * * * root echo 'it works' > /tmp/works.txt

```

And crontab -l:```
# Edit this file to introduce tasks to be run by cron.# 
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
# 
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').# 
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
# 
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8)
# 
# m h  dom mon dow   command
* * * * * date > /logs/date.log

```

Please note that in both cases, the file ends with a new line.  In both cases, I'm editing the tables as root (I know, I know, it's not a good idea, but I wanted to make sure I had permission to do whatever I was trying to do)

I normally have a few more commands that are set to run, but since nothing works, I took it down to the basics and I still get nothing.  I've tried restarting cron as well as cold-rebooting the whole system.  I haven't found any guides that have worked for me, so I would really appreciate any help or advice anyone may have.  Thanks in advance.

In case it helps:```
Linux MediaServer 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 19:56:49 UTC 2013 i686 athlon i686 GNU/Linux
```

---

### Post by Kirk Schnable on 2013-09-30
Please try using direct paths to the binaries, such as for example: (based on your example)
```
[COLOR=#000000]** * * * * root /bin/echo 'it works' > /tmp/works.txt*[/COLOR]
```[COLOR=#000000]I've found that crontab sometimes can't handle indirect paths because of the nature of the cron environment.[/COLOR]

---

### Post by JNied on 2013-10-01
Thanks Kirk, but no luck.  This is now my exact crontab file:```
# /etc/crontab: system-wide crontab# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.


SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin


# m h dom mon dow user    command
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )


* * * * * root /bin/echo 'it works' > /tmp/works.txt

```

But even after several minutes:```
root@ForumFriendlyHostName:~# ls /tmp
delugeweb-LI3Z8M  delugeweb-ySKFDH  pulse-PKdhtXMmr18n  ssh-YcjgfZEHUxOZ
```

---

### Post by Habitual on 2013-10-01
n/m. I'm an old guy.

---

### Post by Bashing-om on 2013-10-01
JNied; Hey !

Has "cron" ever worked ? Is this a minimalistic install ?

On my install I found in trouble shooting that situation that "anacron" is not installed by default. (required for several things)

```

dpkg -l anacron

```

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

