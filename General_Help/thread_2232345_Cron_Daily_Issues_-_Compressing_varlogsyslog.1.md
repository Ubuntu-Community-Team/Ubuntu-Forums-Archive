---
title: "Cron Daily Issues - Compressing /var/log/syslog.1"
date: 2014-07-01
forum: General Help
---

### Post by wewantutopia on 2014-07-01
Hello,

Everyday my computer virtually freezes for a few minutes with I/O at near 100%

I've figured out that it is caused by cron running its daily job.  

This is the email that cron sends:

```
/etc/cron.daily/logrotate:

gzip: stdin: Input/output error
error: failed to compress log /var/log/pm-powersave.log.1

gzip: stdin: Input/output error
error: failed to compress log /var/log/syslog.1
run-parts: /etc/cron.daily/logrotate exited with return code 1

```

What is this error and does anyone have any ideas how to fix it? 

Thanks!!!

---

### Post by SeijiSensei on 2014-07-01
It's from the logrotate command.   The configuration files are in /etc/logrotate.d/.  The configuration for /var/log/syslog is in the file "rsyslog" in that directory. On my 14.04 machine, it is set to rotate syslog nightly and compress the files with gzip.

The more important question is why the program cannot complete.  Perhaps you're running out of disk space?

If you want to disable logrotate entirely, delete the file /etc/cron.daily/logrotate.

---

### Post by wewantutopia on 2014-07-01
Thanks for the reply.  I'm definitely no where near running out of disk space.  Why else could it not complete?  

Is it beneficial to rotate logs?  Is there a reason not to delete /etc/cron.daily/logrotate?

---

### Post by Karlchen on 2014-07-01
Hello, wewantutopia.

The logrotate jobs do make a lot of sense. They rotate the active logfiles in order to prevent the active logfiles from growing indefinitely thus making them unreadable. logrotate also makes sure that archived (gzipped) logfiles will be deleted from the disk after a preconfigured period of time thus making sure that the filesystem does not run out of disk space because the logfiles keep on eating up the disk space.
As SeijiSensei rightly advised you should determine why gzip fails and solve the issue.

You might start your analysis by posting the ouptput of these commands: ```
cd /var/log
ls -al
sudo du -ks .
df -k .
```
Kind regards,
Karl

---

### Post by SeijiSensei on 2014-07-01
One thing you can try is running logrotate from the command line using its debug function like this:

```
sudo logrotate -d /etc/logrotate.d/rsyslog
```

will test the configuration in that file.  If logrotate says nothing needs to be done, run the command with the "-f" ("force") parameter as well as "-d".

---

