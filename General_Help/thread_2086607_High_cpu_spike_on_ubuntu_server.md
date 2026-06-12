---
title: "High cpu spike on ubuntu server"
date: 2012-11-21
forum: General Help
---

### Post by smerfy on 2012-11-21
Hello everyone - I believe this is the correct place to post this, but if not, please let me know.

I'm having cpu spikes every 30 minutes on my ubuntu web server.  It seems to coincide with this cron job.
09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib$




Here's what the syslog says right around each spike.

Nov 21 16:09:01 ip-10-0-0-55 CRON[29357]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/$
Nov 21 16:09:50 ip-10-0-0-55 CRON[29356]: (CRON) info (No MTA installed, discarding output)

I'm wondering if the server is timing out because it's trying to send an email and no MTA is setup?  Can someone point me in the right direction?

Thank you
Nick

---

### Post by 2F4U on 2012-11-21
And what is /usr/lib/php5/maxlifetime used for? I don't think that the absence of a MTA is causing the problems, since cron detects it and so I would assume that it doesn't attempt to contact the MTA.

---

### Post by smerfy on 2012-11-21
It says this in /etc/cron.d/php5.  

# /etc/cron.d/php5: crontab fragment for php5
#  This purges session files older than X, where X is defined in seconds
#  as the largest value of session.gc_maxlifetime from all your php.ini
#  files, or 24 minutes if not defined.  See /usr/lib/php5/maxlifetime

# Look for and purge old sessions every 30 minutes

I'm not sure this is causing the cpu spikes, but here's my amazon ec2 cpu charts below..  It's like clockwork every 30 minutes.
[http://screencast.com/t/R4UNAeD7IEU](http://screencast.com/t/R4UNAeD7IEU)

I'm new to troubleshooting cpu utilization on linux, so I'm not sure how to really dive into it.

---

### Post by drmrgd on 2012-11-21
It looks like those lines are truncated (hence the '$' at the end).  Can you show us the rest of the lines?

I'm wondering if there's something in that find command that's somehow hogging a lot of resources.

---

### Post by smerfy on 2012-11-21
Sorry about that, here's the whole command.

#09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ]  && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth  -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) !  -execdir fuser -s {} 2>/dev/null \; -delete

I commented it out to test and the utilization spikes stopped.  See here.
[http://www.screencast.com/t/XaWNd4zJlvM](http://www.screencast.com/t/XaWNd4zJlvM)

It's odd because this seems to be a common command for php5 with apache because it's on other web servers I have but is not causing the spikes.

**I don't plan on leaving the command commented out in case it would cause other issues, but I wanted to make sure that was the issue.

---

### Post by smerfy on 2012-11-21
I know with 100% certainty that this command is causing the 2-3 minute 100% cpu spikes.  I ran it as root and it did the same thing.

[ -x /usr/lib/php5/maxlifetime ]  && [ -d /var/lib/php5 ]  && find /var/lib/php5/ -depth  -mindepth 1 -maxdepth 1 -type f  -cmin +$(/usr/lib/php5/maxlifetime) !  -execdir fuser -s {}  2>/dev/null \; -delete

My other servers don't have issues with this, but they likely don't have as many sessions on them.  However, it seems extreme for this to run at 100% utilization.  The server is not that heavily trafficked...

Thank you SO much for your help everyone!

---

### Post by smerfy on 2012-11-21
I think I may have just found the solution here:
[http://serverfault.com/questions/422723/ubuntus-garbage-collection-cron-job-for-php-sessions-takes-25-minutes-to-run-w](http://serverfault.com/questions/422723/ubuntus-garbage-collection-cron-job-for-php-sessions-takes-25-minutes-to-run-w)

I just removed the fuser from the command and it runs in a fraction of a second.. ;)

Can one of you experienced users tell me if there's any reason to not remove the fuser from that command?

Thanks!

---

### Post by drmrgd on 2012-11-21
If you run it without the '2>/dev/null' bit, you might get some clues as to what's going on.  That will direct the stdout to the terminal rather than /dev/null.   I see that I have these files on my server (preconfigured so I don't actually know what's going on with them), but I don't have a cron job like you have.  So, I'm a little out of my league here.  Perhaps an Apache expert will know a little better why that seems to be hanging things.

---

### Post by Thisguy128512 on 2012-11-21
I noticed that it says in the link you posted that due to a bug in Debian (core files in Ubuntu are Debian-based) fuser in that cron job will run on all sessions, which can take a very very long time. So I don't see any reason not to take it out of the command.

EDIT: Found this.

"It sounds like the bug in fuser was that an  earlier version forked but then was never reaped upon completion,  leaving thousands of fuser processes in a zombie state  consuming memory, which leads to a server crash. I think that has  already been fixed in the version of psmisc that I'm using"

Perhaps updating psmisc is the issue? Your other servers may have a different version of it, which would cause them to behave better.

---

### Post by smerfy on 2012-11-22
I'll do that! Thank you so much everyone for the help!  If today is your Thanksgiving have a great & Happy Thanksgiving! ;)

---

