---
title: "cron (and logs)"
date: 2018-02-09
forum: General Help
---

### Post by ivo-welch on 2018-02-09
I am trying to figure out how cron works on ubuntu 17.10, and where program output goes.  I uncommented the relevant line in /etc/rsyslog.d/50-default.conf, and saw /var/log/cron* appear.  all good.

now, `man cron` tells me that I am running  Vixie cron, but my log tells me that it is anacron.  ok, maybe cron is cron.

then I created a script

```
#!/usr/bin/perl
use strict;
use warnings;
my $basetext="$0: from perl script at ".time(). ":".localtime().": run as ".$<." : ";
print "$basetext stdout\n";
print STDERR "$basetext stderr\n";
open(my $FOUT, ">", "/tmp/testcron.ran"); print $FOUT "$basetext file\n"; close($FOUT);
```

but I am surprised not to find the stdout or stderr output in /var/log/cron.log.  can whatever cron is running on 17.10 (and which is it??) direct this to the cron log, too.  (I know the script is running, because I see the output in /tmp/testcron.ran.

---

### Post by btindie on 2018-02-10
On 16.04, and I suspect all later versions, cron runs as a _foreground_ process under *systemd*.
```

$ ps -C cron -f
UID        PID  PPID  C STIME TTY          TIME CMD
root       798     1  0 Feb10 ?        00:00:00 /usr/sbin/cron -f

```
All output is captured via the systemd journal service. You can see this using
```

$ journalctl --no-pager -u cron.service

```

I think you're expecting it to work differently to how it actually does.

man cron:
> 
When executing commands, any output is mailed to the owner of the crontab (or to the user named  in  the MAILTO  environment  variable  in the crontab, if such exists).


Output from cron doesn't go to syslog anymore, nor does the output from jobs it runs.

Normally for a *crontab*, you'd redirect all output to /dev/null (append >/dev/null 2>&1 to command) to stop it from mailing you all the time or redirect all output to your own log file.

---

### Post by ivo-welch on 2018-02-10
thank you, but it is not exactly what I am wondering about.  (after the 50*conf surgery, the /var/log/cron.log has the same nice output as the journalctl.)

1. I have two /etc/*crontab, one anacrontab, the other crontab.  Which one is consulted?  (I can figure this out.)  But more importantly, neither redirects to /dev/null .

2. I know my scripts are running.  where do their outputs (stdout and stderr) go?  if their output is redirected into /dev/null, can this behavior be changed in a conf file?

---

### Post by btindie on 2018-02-10
/etc/{,ana}crontab are used by different programs. Cron is the main one which consults /etc/crontab, this one should not be edited.

You can place your script in either of /etc/cron.{daily,hourly,monthly,weekly} or add a crontab to /etc/cron.d/ or use 'crontab -e' as the user the script is to run as.

Anacron appears to be invoked by cron, it's not something I've ever used before as servers run 24/7. According to *man anacron*
> 
it can be used on machines that aren't running 24 hours a day, to control daily, weekly, and monthly jobs that are usually controlled by cron


As mentioned earlier, output from a job run by cron is emailed to the user that runs it. If you don't have a sendmail alternative installed then the output is just discarded. Which is why I said output from jobs is generally redirected to /dev/null so you don't get bombarded with emails. The system crontab (/etc/crontab) file doesn't do any redirection as that's responsible for running the other ones (hourly/daily/weekly/monthly). If you want to capture the output then you'll either need to redirect the output to your own log file or in your script get that to use syslog. Read the man page for cron, it'll answer your questions.

e.g. For user 'admin' with script *myscript* in ~/bin
```

$ crontab -l
PATH=/home/admin/bin:/usr/local/bin:/bin:/usr/bin

00 00 * * *  myscript >>/home/admin/log/output.log 2>&1

```
( '>>' appends to a file instead of overwrites '>')

If your script produces output and you don't have an MTA installed you'll see something similar to the below in the journal.
> 
... CRON[10660]: (admin) CMD (myscript >> /home/admin/log/output.log)
... CRON[10659]: (CRON) info (No MTA installed, discarding output)


---

