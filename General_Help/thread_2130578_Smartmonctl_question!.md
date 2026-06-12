---
title: "Smartmonctl question!"
date: 2013-03-29
forum: General Help
---

### Post by streat on 2013-03-29
I have configured an automated test cycle but I can't think of a way to confirm that it's adhereing to the cycle. Does anyone know of a way to confirm this? Perhaps maybe a log (other than the error log) of the past tests performed or their times? Thank you!

---

### Post by tgalati4 on 2013-03-29
Most modern disks store the *smartctl* tests (short or long) in the drive itself.

tgalati4@Mint14-Extensa ~ $ sudo smartctl -a /dev/sda
.
.
.

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       266         -

----------------------------

You can pipe the command to grep (or sed or gawk or perl) and pull out the test data that you want.

If you have a script that is run in a cronjob, then a CRON entry will be put in syslog.

tgalati4@Mint14-Extensa ~ $ cat /var/log/syslog | grep CRON
Mar 29 08:09:01 Mint14-Extensa CRON[30933]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Mar 29 08:17:01 Mint14-Extensa CRON[30947]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 29 08:39:01 Mint14-Extensa CRON[31035]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Mar 29 09:09:02 Mint14-Extensa CRON[31126]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -ignore_readdir_race -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)

You can user *logger* to capture the important data from the test and send it to syslog where it will be stored and log-rotated.

---

### Post by streat on 2013-03-30
Still a bit of a newbie, how would I go about configuring logger to log the smartctl test information?

---

### Post by tgalati4 on 2013-03-30
tgalati4@Mint14-Extensa ~ $ man logger
tgalati4@Mint14-Extensa ~ $ logger This is my cheesy message at 0717 hours
tgalati4@Mint14-Extensa ~ $ grep cheesy /var/log/syslog
Mar 30 07:17:25 Mint14-Extensa tgalati4: This is my cheesy message at 0717 hours

tgalati4@Mint14-Extensa ~ $ sudo smartctl -a /dev/sda | grep Completed
# 1  Short offline       Completed without error       00%       266         -
tgalati4@Mint14-Extensa ~ $ sudo smartctl -a /dev/sda | grep Completed | logger
tgalati4@Mint14-Extensa ~ $ grep Completed /var/log/syslog
Mar 30 07:20:20 Mint14-Extensa logger: # 1  Short offline       Completed without error       00%       266         -

I'm sure there is a better way to do this.  I just haven't found it yet.

---

