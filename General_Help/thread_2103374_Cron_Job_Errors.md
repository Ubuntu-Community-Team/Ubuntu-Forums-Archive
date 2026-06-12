---
title: "Cron Job Errors"
date: 2013-01-10
forum: General Help
---

### Post by Rahul Chetwani on 2013-01-10
Hi I am getting cron logs but only for CMD and INFO not for errors.
What should i do to get the error logs of cronjobs.
I purposely created a cronjob in crontab which will run a shell script which does not exist..it should log error in cron logs but it is not doing so..:(

---

### Post by Cheesehead on 2013-01-10
Error options are described in man cron.

Briefly, when root starts cron (in /etc/init/cron.conf), the -L flag sets the logging level. The default logging level is to log as much as possible.

Cron won't forward child process error messages to syslog. It receives the child's exit status, and logs any result that is not 0 (success). It's the responsibility of the child process to log error details directly.

Things to look for:

1) Does your script really produce an error that cron recognizes as an error? If it produces an exit status 0, cron won't recognize that as an error. This is, by far, the most common problem when users look for cron error messages that don't seem to exist.

For example, the following crontab...
```
* * * * * /bin/sh /tmp/no-such-file
```

...should produce an error in /var/log/syslog:
```
Jan 10 06:04:01 my-system CRON[9945]: (me) CMD (/bin/sh /tmp/no-such-file)
Jan 10 06:04:01 my-system CRON[9944]: (CRON) info (No MTA installed, dis
carding output)
```

The second line means that cron tried to e-mail me more information about the failure, usually including error or debug messages returned by the script, but it failed because my system has no Mail Transfer Agent (MTA) installed to forward the message to my e-mail.

2) Check /etc/init/cron.conf . This is the file that launches cron upon boot. The last line of the file should read:
```
exec cron
```
If it says *anything* else, post it here.
If it adds a -L flag, post it here.

3) Check for the existence of a /etc/init/cron.override file. Generally, there shouldn't be one. If the file exists, post it here.

4) Message redirection: After cron creates a message, perhaps you wrote a rule that redirects it into a different log, or discards it. Check your manually-created rules in /etc/rsyslog.conf, or any manually-created /etc/rsyslog.d/* files.

If you have never created any rsyslog rules (most people haven't), then don't try to create one now, nor should you change any existing rules.

---

### Post by TheFu on 2013-01-10
> **Rahul Chetwani said:**
> Hi I am getting cron logs but only for CMD and INFO not for errors.
What should i do to get the error logs of cronjobs.
I purposely created a cronjob in crontab which will run a shell script which does not exist..it should log error in cron logs but it is not doing so..:(

I always get an email with the errors.  Do you have local email working on the system at least?  You can set email up to forward to other email servers too.

---

### Post by rob2468 on 2013-01-10
> **TheFu said:**
> I always get an email with the errors.  Do you have local email working on the system at least?  You can set email up to forward to other email servers too.

Jobs invoked by cron do not associate with any print screen. That is, Linux will submit the user's Email address as the STDOUT and STDERR. Any output contents sent to STDOUT and STDERR will be sent to user by email system.

---

### Post by TheFu on 2013-01-10
> **rob2468 said:**
> Jobs invoked by cron do not associate with any print screen. That is, Linux will submit the user's Email address as the STDOUT and STDERR. Any output contents sent to STDOUT and STDERR will be sent to user by email system.

Exactly. Well, unless you redirect all STD* to /dev/null, which is fairly common in crontabs.

I prefer getting emails for every cron-job, so I don't forget about them.
* load an MTA - I use **postfix**
* during install, I use a satellite system setup and redirect all email to our mail server running on the same LAN. Some ISPs block all SMTP traffic unless it gets sent to their email proxies.
* Edit the** /etc/aliases **file to redirect local email to your real, email address. Basically, to get it off that single machine.  You could load up a mail or **Mail** elm or pine or other email program on the local machine that will read email from /var/spool/mail/* directories. **man aliases** will explain the file format.
* run **newaliases **to rebuild the DB for postfix. I believe all MTAs use this, so if you use sendmail or Exim it is still necessary.

Whenever I install a new system, I
* purge nano
* update the system
* install ntp, postfix, cron ... postfix needs to be installed before cron to avoid exim installation.
* edit /etc/aliases to forward all root, postmaster and other local accounts to my real email admin account - administrative emails are **heavily filtered.**
* edit the /etc/ntp.conf to use our NTP server(s), not the internet ones.

This all happens before I drop my .bashrc file onto the machine. Most machines do not have end-users after all here. The machines provide a service for users, but not direct logins.

I suppose for people with very large networks, remote logging is much better and using something like **Splunk** to make log reviewing easier is 100% mandatory.

---

### Post by Rahul Chetwani on 2013-01-11
Hi ,

There is not -L flag and no /etc/init/cron.override file.
Basically I want know the lastresult of the cronjob as we get in schedule tasks in windows.

---

### Post by Cheesehead on 2013-01-12
If you need more of a lastresult than cron's e-mail and logging facilities provide, then your cronjob should launch a script (child) that executes the job you need (grandchild), catches the result, and sends the result to you in whatever format you wish.

---

