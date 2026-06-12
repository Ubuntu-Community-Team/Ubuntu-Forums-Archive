---
title: "Very large log directory?"
date: 2018-07-29
forum: General Help
---

### Post by faust99 on 2018-07-29
Hi guys,

I've noticed that my var/log directory is quite large; around 10GB. Is this a normal a size? I'm suddenly getting notifications that I have hardly any space left on my root partition. Please advise.

---

### Post by #&amp;thj^% on 2018-07-29
I would think so:
Mine is a 4 year old install:
```
du -s -h /var/log/
876K	/var/log/
```
Maybe check to see the bigest with:
```
du -s -h /var/log/*
4.0K	/var/log/btmp
4.0K	/var/log/btmp.1
24K	/var/log/cups
4.0K	/var/log/faillog
4.0K	/var/log/httpd
12K	/var/log/journal
4.0K	/var/log/lastlog
du: cannot read directory '/var/log/lightdm': Permission denied
4.0K	/var/log/lightdm
8.0K	/var/log/maldet
4.0K	/var/log/old
336K	/var/log/pacman.log
du: cannot read directory '/var/log/private': Permission denied
4.0K	/var/log/private
du: cannot read directory '/var/log/samba/cores': Permission denied
16K	/var/log/samba
4.0K	/var/log/tallylog
312K	/var/log/wtmp
36K	/var/log/Xorg.0.log
36K	/var/log/Xorg.0.log.old
32K	/var/log/Xorg.1.log
24K	/var/log/Xorg.1.log.old

```

---

### Post by faust99 on 2018-07-29
The largest one is syslog, at 8.5G:

12K	/var/log/alternatives.log
8,0K	/var/log/alternatives.log.1
8,0K	/var/log/alternatives.log.2.gz
360K	/var/log/apport.log
4,0K	/var/log/apport.log.1
4,0K	/var/log/apport.log.2.gz
4,0K	/var/log/apport.log.3.gz
4,0K	/var/log/apport.log.4.gz
4,0K	/var/log/apport.log.5.gz
4,0K	/var/log/apport.log.6.gz
4,0K	/var/log/apport.log.7.gz
324K	/var/log/apt
108K	/var/log/auth.log
56K	/var/log/auth.log.1
8,0K	/var/log/auth.log.2.gz
8,0K	/var/log/auth.log.3.gz
8,0K	/var/log/auth.log.4.gz
1,1M	/var/log/boot.log
56K	/var/log/bootstrap.log
0	/var/log/btmp
0	/var/log/btmp.1
76K	/var/log/cups
52K	/var/log/dist-upgrade
368K	/var/log/dpkg.log
220K	/var/log/dpkg.log.1
132K	/var/log/dpkg.log.2.gz
8,0K	/var/log/faillog
8,0K	/var/log/fontconfig.log
4,0K	/var/log/gdm3
4,0K	/var/log/gpu-manager.log
8,0K	/var/log/hp
1,3M	/var/log/installer
801M	/var/log/journal
2,3M	/var/log/kern.log
4,1M	/var/log/kern.log.1
396K	/var/log/kern.log.2.gz
344K	/var/log/kern.log.3.gz
200K	/var/log/kern.log.4.gz
40K	/var/log/lastlog
4,0K	/var/log/speech-dispatcher
8,5G	/var/log/syslog
344K	/var/log/syslog.1
100K	/var/log/syslog.2.gz
316K	/var/log/syslog.3.gz
196K	/var/log/syslog.4.gz
316K	/var/log/syslog.5.gz
84K	/var/log/syslog.6.gz
76K	/var/log/syslog.7.gz
12K	/var/log/tallylog
56K	/var/log/unattended-upgrades
136K	/var/log/wtmp
100K	/var/log/wtmp.1
72K	/var/log/Xorg.0.log
72K	/var/log/Xorg.0.log.old

---

### Post by #&amp;thj^% on 2018-07-29
Files in /var/log can often grow indefinitely, and may require cleaning at regular intervals. Something that is now normally managed via log rotation utilities such as 'logrotate'. This utility also allows for the automatic rotation compression, removal and mailing of log files. Logrotate can be set to handle a log file daily, weekly, monthly or when the log file gets to a certain size. Normally, logrotate runs as a daily cron job. 
See if it is installed:
```
apt policy logrotate
```

---

### Post by faust99 on 2018-07-29
Yes, it is: 

> logrotate:
  Installed: 3.11.0-0.1ubuntu1
  Candidate: 3.11.0-0.1ubuntu1
  Version table:
 *** 3.11.0-0.1ubuntu1 500
        500 [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
        100 /var/lib/dpkg/status


---

### Post by #&amp;thj^% on 2018-07-29
Something is not right then.
as seen via "man logrotate":
```
NAME
       logrotate &#8208; rotates, compresses, and mails system logs

SYNOPSIS
       logrotate  [--debug]  [--verbose] [--log file] [--force] [--state file]
       [--mail command] config_file [config_file2 ...]

DESCRIPTION
       logrotate is designed to ease administration of systems  that  generate
       large numbers of log files.  It allows automatic rotation, compression,
       removal, and mailing of log files.  Each log file may be handled daily,
       weekly, monthly, or when it grows too large.

       Normally,  logrotate  is run as a daily cron job.  It will not modify a
       log more than once in one day unless the  criterion  for  that  log  is
       based  on the log's size and logrotate is being run more than once each
       day, or unless the -f or --force option is used.

       Any number of config files may be given on the command line. Later con&#8208;
       fig files may override the options given in earlier files, so the order
       in which the logrotate config files are listed is important. 
       Normally, a  single  config  file which includes any other config files 
       which are
       needed should be used.  See below for more information on  how  to  use
       the  include  directive to accomplish this.  If a directory is given on
       the command line, every file in that directory  is  used  as  a  config
       file.

       If  no  command  line arguments are given, logrotate will print version
       and copyright information, along with a short usage  summary.   If  any
       errors  occur  while  rotating  logs, logrotate will exit with non-zero
       status.
```
I hesitate to tell you which are needed and not needed.
**If you are certain that none of the logs is useful for you**, you can always clear them, just try this.
```

echo 0 > /var/log/log_file_name
```
be sure to use the proper path "log_file_name" is just an example, and **I will take no responsibility for breakage**. :)
Maybe have a look here for some idea: [https://askubuntu.com/questions/436051/i-cannot-clear-syslog-but-i-can-remove-it](https://askubuntu.com/questions/436051/i-cannot-clear-syslog-but-i-can-remove-it)

I use bleachbit also and have done that for years so I have a feel for how it works on my systems.
Bleach:
```
Delete 4.1kB /var/log/btmp.1
Delete 4.1kB /var/log/samba/smbd.log.1
Delete 4.1kB /var/log/samba/nmbd.log.1
Delete 4.1kB /var/log/cups/error_log.2
Delete 4.1kB /var/log/cups/error_log.4
Delete 4.1kB /var/log/cups/error_log.3
Delete 4.1kB /var/log/cups/error_log.1
Delete 4.1kB /var/log/lightdm/x-0.log.old
Delete 4.1kB /var/log/lightdm/seat0-greeter.log.old
Delete 4.1kB /var/log/lightdm/x-1.log.old
Delete 8.2kB /var/log/lightdm/lightdm.log.old
Delete 36.9kB /var/log/Xorg.0.log.old
Delete 24.6kB /var/log/Xorg.1.log.old
```

---

### Post by faust99 on 2018-07-29
Thanks for your help. Will clearing syslog affect the system in some way, or is it useful literally as a log by which to asses what has gone wrong etc?

---

### Post by #&amp;thj^% on 2018-07-29
Normally you don't want to clear all the logs away since they are your starting point in all troubleshooting.

---

### Post by faust99 on 2018-07-29
That makes sense. In that case, can you just clear them for a particular date range?

---

### Post by #&amp;thj^% on 2018-07-29
That is what I do with bleachbit.
But I have never let mine get that big>>>I guess I just don't know how to advise you with this one "8,5G /var/log/syslog"
You could always back that up to another location IE: Re moveable USB/Storage of some type..to have if needed. :)
After I just used bleachbit again:
```
du -s -h /var/log/
788K	/var/log/
```
Which was previously "876K	/var/log/"
I can just see newer user's running into problems with Bleachbit so I use a Warning here for Lookers to tread lightly with Bleachhbit as it will remove stuff that is needed and leave you with a broken system.
So make sure you know how to use Bleachbit in a safe manner.
This is something not necessarily pointed @faust99 I just know someone will see this thread and overly use bleachbit to break their system. So now you have been warned. :p

---

### Post by faust99 on 2018-07-29
That's what I was thinking of doing too. However, the command "echo 0 > /var/log/log_file_name" doesn't seem to work, with or without root privileges, returning, "bash: /var/log/syslog: Permission denied"....?

---

### Post by faust99 on 2018-07-29
Of course, it's a matter of permissions, duh...

---

### Post by Doug S on 2018-07-29
> **faust99 said:**
> That's what I was thinking of doing too. However, the command "echo 0 > /var/log/log_file_name" doesn't seem to work, with or without root privileges, returning, "bash: /var/log/syslog: Permission denied"....?Do either this:
```
sudo su
echo 0 > /var/log/log_file_name
exit
``` or this:
```
echo 1 | sudo tee /var/log/log_file_name
```
Of course, the disclaimers from 1fallen still apply.

---

### Post by faust99 on 2018-07-29
I just changed the permissions as root and it worked out. Thank you for your tips and help.

---

### Post by #&amp;thj^% on 2018-07-29
> **faust99 said:**
> Of course, it's a matter of permissions, duh...

Did you get it then? I mean did it work?
Ok I see from you above post you did.
Glad to be of help. :)
It is also good to see Doug S I seldom get to hear from him lately. ;)

---

### Post by faust99 on 2018-07-29
Yes, it has worked out. Thank you both :)

---

### Post by Impavidus on 2018-07-30
A syslog of 8.5GB is really a problem. The problem appears to be recent, as the older versions of syslog are normal size. Look for repeating messages in syslog. Just clearing the file doesn't solve the problem.

---

### Post by faust99 on 2018-07-30
> **Impavidus said:**
> A syslog of 8.5GB is really a problem. The problem appears to be recent, as the older versions of syslog are normal size. Look for repeating messages in syslog. Just clearing the file doesn't solve the problem.

Yes, words of wisdom. Thank you.

---

### Post by Paddy Landau on 2018-08-07
> **Doug S said:**
> ```
echo 1 | sudo tee /var/log/log_file_name
```
To clear the file completely, don't echo anything. You can do it simpler (though this still leaves one byte):
```
echo | sudo tee /var/log/log_file_name
```
or empty it completely:
```
echo -n | sudo tee /var/log/log_file_name
```
or, best of all, get rid of echo and use an empty file:
```
sudo tee /var/log/log_file_name </dev/null
```
Just for completeness :)

---

### Post by HermanAB on 2018-08-07
In my experience, one can delete everything in /var/log.  Important log files will be recreated automagically.  Unimportant things will stop logging, which is not a loss anyway.  Most things will start logging again after a reboot.

---

### Post by faust99 on 2018-08-07
Thanks :)

---

### Post by faust99 on 2018-08-07
> **Paddy Landau said:**
> To clear the file completely, don't echo anything. You can do it simpler (though this still leaves one byte):
```
echo | sudo tee /var/log/log_file_name
```
or empty it completely:
```
echo -n | sudo tee /var/log/log_file_name
```
or, best of all, get rid of echo and use an empty file:
```
sudo tee /var/log/log_file_name </dev/null
```
Just for completeness :)

Thanks :)

---

### Post by HermanAB on 2018-08-07
For complete completeness:
# truncate -s 0 logfile1 logfile2 logfile3...

If the problem with growing log files continue, then you need to modify /etc/logrotate.conf:
[https://linuxconfig.org/setting-up-logrotate-on-redhat-linux](https://linuxconfig.org/setting-up-logrotate-on-redhat-linux)

---

### Post by Paddy Landau on 2018-08-08
> **HermanAB said:**
> ```
truncate -s 0 logfile1 logfile2 logfile3...
```
Excellent, thank you!

---

