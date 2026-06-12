---
title: "[SOLVED] 1 cron job won't run (n00b question)"
date: 2008-04-20
forum: General Help
---

### Post by bronkeydain on 2008-04-20
Sorry for the n00b question.

I have made this script to dump my mysql tables. 
It resides in /root/scripts, like all my scripts, and I copied a symbolic link into /etc/cron.daily (using cp -l command). 

[email]root@ubuntu:/etc/cron.dail[/email]y# ls -la
-rwxr-xr-x   2 root root   432 2008-04-17 00:11 sqldatabackup (<--- does not run)
-rwxr--r--   2 root root  1484 2008-03-22 02:18 BackupAll (<--- another one of mine, does run)

if I go to /etc/cron.daily and type ./sqldatabackup the script does the job fine, but cron won't run it, yet it does run BackupAll every night fine. I have followed the same procedure to schedule both scripts (which is copy a symbolic link into cron.daily nothing else). 

Does anyone have a suggestion where to look next? Thanks in advance.

---

### Post by squaregoldfish on 2008-04-20
Have a look in /var/log/syslog - all cron events get logged in there, so there might be an error logged.

Steve.

---

### Post by bronkeydain on 2008-04-20
Thanks for your reply.

I have taken a look but I can't really find any reference to neither of the above mentioned jobs....

Syslog:
Apr 20 07:35:01 ubuntu anacron[31164]: Job `cron.daily' started
Apr 20 07:35:02 ubuntu anacron[31174]: Updated timestamp for job `cron.daily' to 2008-04-20
Apr 20 07:39:02 ubuntu /USR/SBIN/CRON[31214]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr 20 07:40:02 ubuntu /USR/SBIN/CRON[31224]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Apr 20 07:40:02 ubuntu /USR/SBIN/CRON[31225]: (www-data) CMD (php -qC /usr/share/egroupware/phpgwapi/cron/asyncservices.php default)
Apr 20 07:45:02 ubuntu /USR/SBIN/CRON[31228]: (www-data) CMD (php -qC /usr/share/egroupware/phpgwapi/cron/asyncservices.php default)
Apr 20 07:50:02 ubuntu /USR/SBIN/CRON[31232]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Apr 20 07:50:03 ubuntu /USR/SBIN/CRON[31233]: (www-data) CMD (php -qC /usr/share/egroupware/phpgwapi/cron/asyncservices.php default)
Apr 20 07:55:01 ubuntu /USR/SBIN/CRON[31236]: (www-data) CMD (php -qC /usr/share/egroupware/phpgwapi/cron/asyncservices.php default)
Apr 20 08:00:02 ubuntu /USR/SBIN/CRON[31240]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Apr 20 08:00:02 ubuntu /USR/SBIN/CRON[31241]: (www-data) CMD (php -qC /usr/share/egroupware/phpgwapi/cron/asyncservices.php default)
Apr 20 08:05:01 ubuntu /USR/SBIN/CRON[31244]: (www-data) CMD (php -qC /usr/share/egroupware/phpgwapi/cron/asyncservices.php default)
Apr 20 08:09:02 ubuntu /USR/SBIN/CRON[31247]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Apr 20 08:09:35 ubuntu named[29329]: unexpected RCODE (REFUSED) resolving 'dns.dunnewind.net/AAAA/IN': 193.34.16.167#53
Apr 20 08:09:44 ubuntu cracklib: updated dictionary (read/written words: 87547 87547).
Apr 20 08:10:04 ubuntu /USR/SBIN/CRON[31359]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Apr 20 08:10:04 ubuntu /USR/SBIN/CRON[31361]: (www-data) CMD (php -qC /usr/share/egroupware/phpgwapi/cron/asyncservices.php default)
Apr 20 08:10:30 ubuntu syslogd 1.4.1#21ubuntu3: restart.
Apr 20 08:10:30 ubuntu anacron[31164]: Job `cron.daily' terminated (exit status: 1) (mailing output)
Apr 20 08:10:30 ubuntu anacron[31164]: Job `cron.weekly' started
Apr 20 08:10:30 ubuntu nbSMTP[31448]: nbSMTP does not support the -o arguments from sendmail, ignoring them
Apr 20 08:10:30 ubuntu anacron[31164]: Tried to mail output of job `cron.daily', but mailer process (/usr/sbin/sendmail) exited with ststus 1

---

### Post by squaregoldfish on 2008-04-20
> Apr 20 08:10:30 ubuntu anacron[31164]: Job `cron.daily' terminated (exit status: 1) (mailing output)

This looks like the important bit - something failed when the cron.daily was run, and I'd be willing to place a bet that it's an error in your sqldatabackup script. It also seemed that CRON tried to email the error, but failed.

If you run the cron.daily manually:

```
sudo run-parts /etc/cron.daily/
```

you should see the output (and hopefully the error) logged to the console. Give it a go and see what you can see.

Steve.

---

### Post by mike2357 on 2008-04-20
You could also change the cron entry so it sends output and error messages to a file.  Instead of 
sqldatabackup
Make the command in your cron entry
sqldatabackup > /home/whatever/OUT_CRON  2>&1

The "2>&1" means "send error messages to the same output file that regular output is going to", which in this case is "OUT_CRON".  Many commands required certain environment variables to be set in order to run, such as PATH.  Sometimes "cron" runs without these being set.  You can set them in your sqldatabackup script once you figure out which ones are missing.

Good luck.

---

### Post by bronkeydain on 2008-04-21
Thanks so much for your input. I always so much apreciate other peoples time and efford to help out others.

I have fixed the problem with your directions. 

It seems it wasn't actually a problem with my script, it was the logrotate script that was exiting with an error because it thought that zope was still installed. I had removed zope but not purged it so the config files were still there. 

I suppose that means that cron exits as soon as it hits an error of one of the scripts?
I had removed zope weeks ago so this error must have gone unnoticed for a while :)

---

### Post by bronkeydain on 2008-04-22
Ok this wasn't actually solved... 

The cron job worked when I ran them manually by typing "run-parts /etc/cron.daily"
But this morning I noticed it again had not run. 

SInce I fixed sendmail in the process of trying to sort this problem out, all I had to do is check out the error in my mail. I had forgotten to put in a path when calling another script, just like Mike suggested. I have fixed this and I assume it works now.

Thanks again for your input.

---

