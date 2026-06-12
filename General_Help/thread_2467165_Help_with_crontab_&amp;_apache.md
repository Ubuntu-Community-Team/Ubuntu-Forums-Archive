---
title: "Help with crontab &amp; apache"
date: 2021-09-17
forum: General Help
---

### Post by dgpeter on 2021-09-17
Hi 

I'm running ubuntu 20.04 and apache web server. I have this python script which collects some data and generates a report (html). The script execute fine "./script.py". The script has root ownership. I have entered in crontab -e a line to run the script. I see cron runs it by looking at the syslog. Though the script does not  create the files as it does when ran via the command line. 

I must be doing something wrong and/or not know something. looking for some help and pointers

Thanks

---

### Post by dragonfly41 on 2021-09-17
Add a shebang at top of pt script ..
#!/usr/bin/env/ python3
and also make it executable ?

---

### Post by TheFu on 2021-09-17
Which crontab did you edit - your userid's or root's?

If you edited your own, then it will run with that userid and permissions. Typically, a normal login userid cannot write (and shouldn't be allowed to write) so anywhere that apache would read. Call it a security thing.

If you edited the root crontab, then it will run as root, with root's environment (which is much different from a normal userid) and has a limited PATH for security reasons.  

BTW, there are multiple crontabs. There are 2 different formats.  It is also possible to just drop a script into /etc/cron.hourly/ to have that script run as root, every hour.  That's pretty automatic.  There are daily, weekly, monthly and yearly cron.{whatever}/ directories for those periods too.  For example, I use logwatch to have system logfiles searched for strange things that an admin needs to know.  It runs daily from the /etc/cron.daily/ directory.  The output can be an HTML file or, as I prefer, a text email sent to my email server.  Each system I run does that, so every morning I get to scan the reports from each - takes about 3 minutes.  Sometimes there are thousands of attempted logins from bogus locations - even though only 3 attempts from any single IP are tolerated before the firewall blocks an IP.  I used to see thousands of IMAPS login attempts, before we pulled the email server off the internet and made it only accessible for clients when connected to our VPN.  Logwatch - nice tool.

Anyway, if you use **crontab -e** to edit a crontab, then this comment will be helpful:
```
# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  /full/path/to/command --arg1 --arg2 file1 file2  > /tmp/log.file  2>&1
```

I put that comment into all my crontabs, to help prevent dumb mistakes by myself.  the /etc/crontab file doesn't have the same format, beware. It is close, but has more fields.  Also, be certain to backup your crontabs that are created using crontab -e. They aren't in a place that normally gets backed up - they are buried under /var/spool/... 

To get more/better help, show your EXACT commands, exact crontab, and the script.  Try a simple script first - does that work or not in the crontab? Depending on the answer, you'll know if it is an misunderstand about cron and crontabs or a problem with the script.

When creating scripts and using cron, it is important to always specify the full path to all external commands used. Never trust the PATH environment variable, if you don't set it in your script.  Same for LD_LIBRARY_PATH and other environment variables.  Cron won't have any GUI environment variables set either and shouldn't be used to attempt to interact with any desktop. Cron programs should only be coded to work on headless systems - no GUI.

---

### Post by rsteinmetz70112 on 2021-09-19
Just a minor point Apache usually runs under it's own user ID I think www-data or something similar. Placing your crontab there is probably a better locations, assuming the data it's collecting has to do with apache2

---

