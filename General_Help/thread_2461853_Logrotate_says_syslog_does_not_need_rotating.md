---
title: "Logrotate says syslog does not need rotating"
date: 2021-05-08
forum: General Help
---

### Post by johnrb68 on 2021-05-08
[COLOR=#1A1A1B][FONT=&amp]Hello:
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]syslog is now 16 days old (age of new build - Ubuntu 20.04.2 LTS )
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]This is a new clean stock build, no changes have been made to default logrotate config.
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]logrotate 3.14.0
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]If I run logrotate manually:
[/FONT][/COLOR]
```
sudo logrotate -d /etc/logrotate.conf

```
[COLOR=#1A1A1B][FONT=&amp]or[/FONT][/COLOR]
```
sudo logrotate -v /etc/logrotate.conf

```
[COLOR=#1A1A1B][FONT=&amp]It goes through all the log files, and says this for syslog:[/FONT][/COLOR]
```
rotating pattern: /var/log/syslog
 after 1 days (7 rotations)
empty log files are not rotated, old logs are removed
switching euid to 0 and egid to 4
considering log /var/log/syslog
Creating new state
  Now: 2021-05-08 09:34
  Last rotated at 2021-05-08 09:00
  log does not need rotating (log has been already rotated)
switching euid to 0 and egid to 0

```
[COLOR=#1A1A1B][FONT=&amp]But the file is not being rotated an still shows 16 days worth of content.
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Same thing for apache2 - not being rotated and says it already has been, files have 16 days worth in each:[/FONT][/COLOR]
```
rotating pattern: /var/log/apache2/*.log  after 1 days (14 rotations)
empty log files are not rotated, old logs are removed
switching euid to 0 and egid to 4
considering log /var/log/apache2/access.log
Creating new state
  Now: 2021-05-08 09:23
  Last rotated at 2021-05-08 09:00
  log does not need rotating (log has been already rotated)
considering log /var/log/apache2/error.log
Creating new state
  Now: 2021-05-08 09:23
  Last rotated at 2021-05-08 09:00
  log does not need rotating (log has been already rotated)
considering log /var/log/apache2/other_vhosts_access.log
Creating new state
  Now: 2021-05-08 09:23
  Last rotated at 2021-05-08 09:00
  log does not need rotating (log has been already rotated)
not running prerotate script, since no logs will be rotated
not running postrotate script, since no logs were rotated
switching euid to 0 and egid to 0

```
[COLOR=#1A1A1B][FONT=&amp]I tried manual with a force, and that was the first time files actually were rotated.
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Also in the syslog file at the time cron.daily runs, I see this for almost every day:[/FONT][/COLOR]
```
systemd[1]: Condition check resulted in Rotate log files being skipped.

```
[COLOR=#1A1A1B][FONT=&amp]Not sure why files are being skipped, the default is daily with no file size setting, so these should rotate every day. 

They syslog file was almost 25MB before I did the manual logrotate with the -f switch.
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Has anyone ran into this before?
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Any ideas?
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Thank you![/FONT][/COLOR]

---

### Post by TheFu on 2021-05-08
I'm on 20.04.2, 
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:        20.04
Codename:       focal
```
with these files:
```
/etc/logrotate.d$ ll /var/log/syslog*
-rw-r----- 1 syslog adm 157120 May  8 18:34 /var/log/syslog
-rw-r----- 1 syslog adm 180340 May  8 00:00 /var/log/syslog.1
-rw-r----- 1 syslog adm  16239 May  7 00:00 /var/log/syslog.2.gz
-rw-r----- 1 syslog adm  17900 May  6 00:00 /var/log/syslog.3.gz
-rw-r----- 1 syslog adm  14883 May  5 00:00 /var/log/syslog.4.gz
-rw-r----- 1 syslog adm  19908 May  4 00:00 /var/log/syslog.5.gz
-rw-r----- 1 syslog adm  16385 May  3 00:00 /var/log/syslog.6.gz
-rw-r----- 1 syslog adm  18521 May  2 00:00 /var/log/syslog.7.gz
```

Here's the rsyslog file: 
```
/etc/logrotate.d$ more rsyslog 
/var/log/syslog
{
        rotate 7
        daily
        missingok
        notifempty
        delaycompress
        compress
        postrotate
                /usr/lib/rsyslog/rsyslog-rotate
        endscript
}

/var/log/mail.info
/var/log/mail.warn
/var/log/mail.err
/var/log/mail.log
/var/log/daemon.log
/var/log/kern.log
```

Seems to be working.
```
/etc/cron.daily/logrotate
``` is the file that gets called daily at midnight on that system.
So, perhaps try:
```
sudo /etc/cron.daily/logrotate
```
for your troubleshooting?  Could modify the first line to have ***-x*** option for more details about the script.  May want to force a root environment and not inherit yours for a more realistic test.  sudo -i forces a real root environment:
```
sudo -i 
/etc/cron.daily/logrotate
```

---

