---
title: "crontab only working intermittently for main account"
date: 2013-06-10
forum: General Help
---

### Post by clueo8 on 2013-06-10
I've been going nuts trying to get my crontab entries to run consistently... It's very odd, it will work for that day when I first edit my user's crontab, but then will just stop working there on out... I think the issue may be somehow associated with my main account that was initially setup with ubuntu server (account has sudo to root; updated to latest version of ubuntu server), because I have another user which has no issue executing crontab entries on a daily basis.

When I go to test, I'll use the same entry, set the time to execute a minute or two after, tail the logs and it works!

But when I set it to run and then after time passes, the entries do not get executed... Here is my current crontab, any insight would be greatly appreciated... I don't believe its a syntax issue because it works initially when testing... I also tried adding an empty line to the bottom as well as the empty MAILTO as you will see below:

```

# Edit this file to introduce tasks to be run by cron.
MAILTO=""
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
0 17 * * 1 /home/clue/scripts/MySQLdump.sh > /home/clue/log/MySQLdump.log 2>&1
0 17 * * 5 /home/clue/scripts/MySQLdump.sh > /home/clue/log/MySQLdump.log 2>&1
0 23 * * * /home/clue/scripts/sync_ftp.sh > /home/clue/log/sync_ftp.log 2>&1
0 18 * * * /home/clue/scripts/updateDNS.sh > 2>&1


```

UPDATE:

I'm looking at my rolled over syslogs and it appears the entries are showing up, but the outcome of my scripts are not working as expected...

```

clue@Ubuntu-Server:~/log$ zcat /var/log/syslog.* | grep 'home/clue'

Jun  7 17:00:01 Ubuntu-Server CRON[27422]: (clue) CMD (/home/clue/scripts/MySQLdump.sh > /home/clue/log/MySQLdump.log 2>&1)
Jun  7 18:00:01 Ubuntu-Server CRON[27465]: (clue) CMD (/home/clue/scripts/updateDNS.sh > 2>&1)
Jun  7 23:00:01 Ubuntu-Server CRON[27697]: (clue) CMD (/home/clue/scripts/sync_ftp.sh > /home/clue/log/sync_ftp.log 2>&1)
Jun  6 18:00:01 Ubuntu-Server CRON[18297]: (clue) CMD (/home/clue/scripts/updateDNS.sh > 2>&1)
Jun  6 23:00:01 Ubuntu-Server CRON[18493]: (clue) CMD (/home/clue/scripts/sync_ftp.sh > /home/clue/log/sync_ftp.log 2>&1)
Jun  5 18:00:01 Ubuntu-Server CRON[11018]: (clue) CMD (/home/clue/scripts/updateDNS.sh > 2>&1)
Jun  5 23:00:01 Ubuntu-Server CRON[11224]: (clue) CMD (/home/clue/scripts/sync_ftp.sh > /home/clue/log/sync_ftp.log 2>&1)
Jun  4 18:00:01 Ubuntu-Server CRON[5801]: (clue) CMD (/home/clue/scripts/updateDNS.sh > 2>&1)
Jun  4 23:00:01 Ubuntu-Server CRON[9952]: (clue) CMD (/home/clue/scripts/sync_ftp.sh > /home/clue/log/sync_ftp.log 2>&1)
Jun  3 17:00:01 Ubuntu-Server CRON[758]: (clue) CMD (/home/clue/scripts/MySQLdump.sh > /home/clue/log/MySQLdump.log 2>&1)
Jun  3 18:00:01 Ubuntu-Server CRON[792]: (clue) CMD (/home/clue/scripts/updateDNS.sh > 2>&1)
Jun  3 23:00:01 Ubuntu-Server CRON[3805]: (clue) CMD (/home/clue/scripts/sync_ftp.sh > /home/clue/log/sync_ftp.log 2>&1)
Jun  2 18:00:01 Ubuntu-Server CRON[31673]: (clue) CMD (/home/clue/scripts/updateDNS.sh > 2>&1)
Jun  2 23:00:01 Ubuntu-Server CRON[32212]: (clue) CMD (/home/clue/scripts/sync_ftp.sh > /home/clue/log/sync_ftp.log 2>&1)

```

The entry I'm really concerned with is the MySQLdump.sh, which script is this:

```

#!/bin/sh
/usr/bin/mysqldump -u root db_name | /bin/gzip > /home/clue/cL-backups/cL_`date +"%m_%d_%Y"`.sql.gz

```

```

clue@Ubuntu-Server:~/cL-backups$ ls -lrt
total 2688
-rw-rw-r-- 1 clue clue 382898 May  8 09:45 cL_05_08_2013.sql.gz
-rw-rw-r-- 1 clue clue 383107 May 14 13:02 cL_05_14_2013.sql.gz
-rw-rw-r-- 1 clue clue 383243 May 17 17:00 cL_05_17_2013.sql.gz
-rw-rw-r-- 1 clue clue 383406 May 20 17:00 cL_05_20_2013.sql.gz
-rw-rw-r-- 1 clue clue 383514 May 29 06:58 cL_05_29_2013.sql.gz
-rw-rw-r-- 1 clue clue 383562 May 31 10:51 cL_05_31_2013.sql.gz
-rw-rw-r-- 1 clue clue 383750 Jun 10 06:37 cL_06_10_2013.sql.gz

```

From the above ls, you should see a file for Jun  7, but it did not show up... I manually ran it today.  The only time it worked was on May 17 and May 20, as you can see the timestamp of 17:00... I thought I was in the clear until I started checking and it stopped working... I didn't change anything.

---

### Post by The Cog on 2013-06-10
sudo may well be the issue here. I assume that /home/clue/scripts/MySQLdump.sh includes a line that uses sudo.

When you use sudo, it asks for a password. However, it also starts a timer and won't ask for a password again for (I think it's 15 minutes). If you schedule a script that uses sudo, it may well work within that 15 minute window but not later.

I think you should pass the script to root, and schedule the script as root. But for security, you should make sure that only root can edit the script since it will run under root's id. I would probably put the script in /root and change the owner and group to root:root. The script can dump the backup files wherever you want, and change the ownership to whoever you want.

---

### Post by clueo8 on 2013-06-10
Thanks for your speedy reply, I made some updates to my original post.

I mentioned that my main account has sudo to root as it was the first account ubuntu setup during the install, which I believe is the only way to get to root as root account is disabled by default for security purposes...

My script should not need sudo to run.

---

### Post by The Cog on 2013-06-10
I apologise. I think I was confusing myself - it's the mysql root account you need, not the linux root account. 

I see you are overwriting /home/clue/log/MySQLdump.log from the cron command. It might be interesting to know if that gets overwritten on days where the command fails, to indicate if the command actually ran.

I might be inclined to remove that redirect in the cron line, and make a new wrapper script to do something like this:
```
#!/bin/sh
logfile=/home/clue/log/MySQLdump.log
echo $(date) Start dump... >> $logfile
/home/clue/scripts/MySQLdump.sh >> $logfile 2>&1
echo $(date) Finish dump... >> $logfile

```

---

### Post by clueo8 on 2013-06-10
I meant to append to the logs (>>), not overwrite (>), must of tried changing that during one of my tests, but I can't imagine that being the issue, I'm thinking maybe a scripting issue now?  I will try the wrapper script next.

I tried adding this crontab to the root user's cron, it executed, but the backup file does not exist for the time of 9:00.

root's cron:
```

0 9 * * * /home/clue/scripts/MySQLdump.sh

```

```

clue@Ubuntu-Server:~/cL-backups$ cat /var/log/syslog | grep 'MySQLdump'
Jun 10 09:00:01 Ubuntu-Server CRON[2574]: (root) CMD (/home/clue/scripts/MySQLdump.sh)

```

```

clue@Ubuntu-Server:~/cL-backups$ ls -lrt
total 2688
-rw-rw-r-- 1 clue clue 382898 May  8 09:45 cL_05_08_2013.sql.gz
-rw-rw-r-- 1 clue clue 383107 May 14 13:02 cL_05_14_2013.sql.gz
-rw-rw-r-- 1 clue clue 383243 May 17 17:00 cL_05_17_2013.sql.gz
-rw-rw-r-- 1 clue clue 383406 May 20 17:00 cL_05_20_2013.sql.gz
-rw-rw-r-- 1 clue clue 383514 May 29 06:58 cL_05_29_2013.sql.gz
-rw-rw-r-- 1 clue clue 383562 May 31 10:51 cL_05_31_2013.sql.gz
-rw-rw-r-- 1 clue clue 383750 Jun 10 06:37 cL_06_10_2013.sql.gz

```

Only the one I did manually today at 6:37 showed up... It should have overwrote that file for today... I know I didn't move the script out of my user's home directory, but this is root we're talking about, shouldn't that user be able to do anything it wants?

UPDATE:

My attempt at the wrapper script running as the root's crontab did not work.

```

clue@Ubuntu-Server:~/log$ cat /var/log/syslog | grep 'MySQLdump_wrapper'
Jun 10 12:00:01 Ubuntu-Server CRON[3678]: (root) CMD (/home/clue/scripts/MySQLdump_wrapper.sh)

```

But the log file was not written to...

```

clue@Ubuntu-Server:~/log$ cat MySQLdump.log
clue@Ubuntu-Server:~/log$

```

---

### Post by The Cog on 2013-06-10
If the wrapper script is not writing to the log file, I would concentrate on that. Ignore (comment out) the call to mysql-dump until the wrapper script is writing the timestamps to the log file OK.

The only thing I can see that is odd is that you don't give a password to the mysqldump program. Is it possible that it's still there in the background waiting for a password on its stdin? But if that's the case, why does it work manually (I presume you don't type a password then)? I am confused too.

---

### Post by clueo8 on 2013-06-10
I ended up moving everything to a /var/mysql/ directory which contains my scripts, log, and backup directory... From my initial tests, it appears to be working, but I was in this boat before where it would work the day I test, but as time passes, it wouldn't.  I'll continue to monitor it for the Mondays and Fridays I'd expect the backup to occur.  I'm starting to think that the home directory is a bad place to try and run things from because its encrypted... which may be the culprit here...

One thing I thought it may be was the 'date'.  I read on another post that you also need to fully qualify that as '/bin/date'.

You can get around providing the password to the mysqldump command by adding the password to your my.cnf file. (either in your ~ or in /etc/mysql/my.cnf).  It's stored as clear text, not the greatest, but you can at least change read permissions on the cnf file.

---

### Post by The Cog on 2013-06-10
> One thing I thought it may be was the 'date'. I read on another post that you also need to fully qualify that as '/bin/date'.
Stupid stupid stupid. I missed that, even though I looked to make sure everything was fully qualified. That's probably the problem. Very likely.

---

### Post by clueo8 on 2013-06-11
Thanks for your help!

Now If I could get an rsync to work within the wrapper script to copy my backup files over to another server, we would be in business... But I think the encrypted home directory is not going to allow it... Found this post which is the issue I'm having, the only resolution it gave was ":-(".  I have ssh rsa keys shared for passwordless login but it appears the cron job cannot read my users .ssh directory to check the key and it just kills it...

[http://guru.r00t.gr/kb/viewanswer/28146778/]("http://guru.r00t.gr/kb/viewanswer/28146778/")

---

### Post by Cheesehead on 2013-06-11
> **clueo8 said:**
> I have ssh rsa keys shared for passwordless login but it appears the cron job cannot read my users .ssh directory to check the key and it just kills it...

That's right.
Cron uses a (very) limited environment and limited permissions to run the specific tasks assigned.
Cron does not login-pretending-to-be-you to run jobs. So it does not have any knowledge of your environment or encryption or settings or other user-level customizations. If you use encryption, your script must explicitly obtain the key and decrypt what you need (but that means leaving your key laying around in the open)...or you must move the relevant encrypted data to a non-encrypted directory.

Remember, you encrypted the directory in the first place to prevent just such automated tools from reading the data without your consent.

---

### Post by clueo8 on 2013-06-11
Is there a recommended way of cron'ing an rsync to a remote server?  Like a "cron" account that I could setup the trust with?

---

### Post by Cheesehead on 2013-06-11
One right way is to use ssh-agent. This will enable a cron-triggered script to access your ssh key.

This exact problem was asked and answered at [http://serverfault.com/questions/92683/execute-rsync-command-over-ssh-with-an-ssh-agent-via-crontab](http://serverfault.com/questions/92683/execute-rsync-command-over-ssh-with-an-ssh-agent-via-crontab)

---

