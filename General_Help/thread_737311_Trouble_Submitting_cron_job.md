---
title: "Trouble Submitting cron job"
date: 2008-03-27
forum: General Help
---

### Post by hvshah69 on 2008-03-27
I have 7.10 Server edition installed (LAMP). I would like to execute a perl script every minute on this server. 

My crontab file looks like this

*/1 * * * * cd /usr/lib/cgi-bin/xxx/;./yyy.pl

When I try to submit the job, I get the following error
[B]
cron: can't open or create /var/run/crond.pid: Permission denied[/B]

If I try to submit as a root (sudo), I don't get any errors and the job starts in the background

However, the script is not being executed

:confused:

What am I doing wrong ??

---

### Post by pointone on 2008-03-27
crontab has a username field, so it should probably read:

```
*/1 *    * * *    root     cd /usr/lib/cgi-bin/xxx/;./yyy.pl
```

Also, cd'ing to run the command is a bit strange. Try just using the absolute path of the file, so it reads:

```
*/1 *    * * *    root     /usr/lib/cgi-bin/xxx/yyy.pl
```

---

