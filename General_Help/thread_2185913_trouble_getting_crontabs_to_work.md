---
title: "trouble getting crontabs to work"
date: 2013-11-04
forum: General Help
---

### Post by bphillips2 on 2013-11-04
I am attempting to get some crontabs to work.  I installed zurmo (zurmo.org) on a test server with Ubuntu 12.04 and had everything working, even the crontabs.  I then reinstalled Zurmo on a different ubunut server and can no longer get them to work.  I copied and pasted them from the original server and then just changed the username.

I originally followed this guide
[http://zurmo.org/wiki/how-to-set-up-job-manager](http://zurmo.org/wiki/how-to-set-up-job-manager)

After having a bunch of problems I simplified it and tried just one of the Zurmo commands, I then added a test cron job to see how it would work, as you can see below.

current settings using "crontab -e" - none of these work

```

# Edit this file to introduce tasks to be run by cron.
#
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
 
 
*/1 * * * * cd /home/justin/zurmo/app/protected/commands && ./zurmoc jobManager super Monitor &> /dev/null
*/1 * * * * echo "Cron Worked2 $(date)" >> cd /home/justin/zurmo/app/protected/commands/cronworked.txt


```

I had originally added a test line like this
```

*/1 * * * * echo "Cron Worked2 $(date)" >>  /tmp/cronworked.txt

```
That code worked, it created the "cronworked.txt" file and placed the echo command in it.

So my thought is somehow the cron job isn't working within the user (justin) account.

I have done a chomd 777 on /home/justin/zurmo/app/protected/commands

Anyone have any ideas? I'm running out of options.

---

### Post by tgalati4 on 2013-11-04
Cronjobs are either owned by root or by individual users.  Normally you would use *crontab -e* to edit a cron table for the current user.  That sets up both the job and the permissions to run the job.  This prevents moving the job to a different user--perhaps as a security measure.

```
man crontab
```

Pay attention to /etc/cron.allow and /etc/cron.deny.

---

### Post by bphillips2 on 2013-11-04
Appreciate the reply.

I don't have a /etc/cron.allow or /etc/cron.deny

I think the user justin has permission to run cron jobs, because the first test I did:

```
[COLOR=#000000][FONT=Ubuntu Mono]*/1 * * * * echo "Cron Worked2 $(date)" >>  /tmp/cronworked.txt[/FONT][/COLOR]
```

Was done using the user "justin".  In fact it was in the same cron entry just under my Zurmo cron entry.  So it's like I can run crons that affect root directories but not the user directories.

If it helps, here are my permissions:

```
[COLOR=black]justin@ubuntu:~/zurmo/app/protected/commands$ ls -l
[/COLOR][COLOR=black]total 108
[/COLOR][COLOR=black]-rw-r--r-- 1 justin justin  3145 Oct 31 23:02 bootstrap.php
[/COLOR][COLOR=black]-rw-r--r-- 1 justin justin 12051 Oct 31 23:02 DatabaseCommand.php
[/COLOR][COLOR=black]-rw-r--r-- 1 justin justin  9949 Oct 31 23:02 EmailCommand.php
[/COLOR][COLOR=black]-rw-r--r-- 1 justin justin  4113 Oct 31 23:02 ImportCommand.php
[/COLOR][COLOR=black]-rw-r--r-- 1 justin justin  5068 Oct 31 23:02 InstallCommand.php
[/COLOR][COLOR=black]-rw-r--r-- 1 justin justin  7959 Oct 31 23:02 InstallLanguageCommand.php
[/COLOR][COLOR=black]-rw-r--r-- 1 justin justin  4851 Oct 31 23:02 JobManagerCommand.php
[/COLOR][COLOR=black]-rw-r--r-- 1 justin justin  6751 Oct 31 23:02 ManageMetadataCommand.php
[/COLOR][COLOR=black]-rw-r--r-- 1 justin justin  2256 Oct 31 23:02 roots.php
[/COLOR][COLOR=black]drwxr-xr-x 3 justin justin  4096 Oct 31 23:02 tests
[/COLOR][COLOR=black]-rw-r--r-- 1 justin justin  5187 Oct 31 23:02 UpdateSchemaCommand.php
[/COLOR][COLOR=black]-rw-r--r-- 1 justin justin  8069 Oct 31 23:02 UpgradeZurmoCommand.php
[/COLOR][COLOR=black]-rwxr-xr-x 1 justin justin    73 Oct 31 23:02 zurmoc
[/COLOR][COLOR=black]-rwxr-xr-x 1 justin justin   380 Oct 31 23:02 zurmoc.bat
[/COLOR][COLOR=black]-rwxr-xr-x 1 justin justin  2193 Oct 31 23:02 zurmoc.php
[/COLOR][COLOR=black]-rw-r--r-- 1 justin justin  2267 Oct 31 23:02 zurmocTest.php[/COLOR]
```

---

### Post by tgalati4 on 2013-11-04
I'm not familiar with zurmo, but I am familar with [http://sugarcrm.org](http://sugarcrm.org) which is also a php-based CRM.  Normally those php files would have root ownership or www-data ownership, since they run under the apache web server.  I'm not sure if the ownership by a single user would create an execution problem, but if *justin* does not have admin privileges, there is a good chance that is the issue.

You can try adding *justin* to /etc/cron.allow or do some more research in how the ownerships are supposed to be set up.  I remember having similar problems getting sugarcrm cronjobs to run properly, but that was a few years ago and I would have to go through my notes to see what hoops I had to jump through to get them to work.  Have you searched through the zurmo forums for *cronjob*?

---

### Post by bphillips2 on 2013-11-04
Yes, I have looked through the zurmo forums, they haven't been much help.

Is there a way to see if *justin* has admin privileges? Or if I give him admin privileges to test if it works, can I remove those privileges later?

---

### Post by bphillips2 on 2013-11-04
If it helps, I tried giving these cron jobs sudo privileges by using the command "sudo crontab -e" and placing the same jobs there.  That also didn't work.  Wouldn't that be the same as giving j*ustin *&#8203;admin privileges?

---

### Post by Dave_L on 2013-11-04
Does the directory /home/justin/zurmo/app/protected/commands exist?

---

### Post by bphillips2 on 2013-11-05
Yes. Home/justin/zurmo/app/protected/commands exists.  I also gave it permissions using "chmod 777"

---

### Post by bphillips2 on 2013-11-05
I appreciate all the help, I figured out the problem.  I was trying to run the cron job as the Zurmo user *super *but I had changed that a different name.

Thanks for the help!

---

