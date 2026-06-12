---
title: "Prevent logrotate from rotating certain logs"
date: 2006-12-11
forum: General Help
---

### Post by dualusbibook on 2006-12-11
I'm having trouble preventing logrotate from rotating my mail logs.  I have a daily cron script that runs at midnight that takes care of my mail logs.

What I have tried so far is to add an entry into /etc/logrotate.conf that would rotate the log if it reached a certain size.  The size of course is large enough that it will never reach it.  The problem is the log is still being rotated.

What I have tried currently is:
/var/log/mail.log {
missingok
daily
rotate 5
nocompress
size 100M
}

Is this the right approach?  I have been unable to find any information on the net regarding an omit command.

My mail program is postfix, and currently the logs are rotating once a week which corresponds to the top part of my /etc/logrotate.conf file.

Any thoughts or ideas would be appreciated.  Also I can provided more info if needed.

---

### Post by nwiebe on 2007-01-16
Did you get this figured out?  On Ubuntu (and Debian), all files that syslog writes to are are also roated by syslog, instead of logrotate.  Look in /etc/cron.daily/sysklogd.  Look for the line:

for LOG in `syslogd-listfiles`

any files that the command syslogd-listfiles outputs will be rotated by syslog.  You can prevent this behaviour by adding "-s" switch.  For example, I stop syslog from rotating my sendpage logs by changing the line above to this:

for LOG in `syslogd-listfiles -s sendpage`

There's another cron job, /etc/cron.weekly/sysklogd that rotates other syslog files on a weekly basis.  

[http://www.ducea.com/2006/06/06/rotating-linux-log-files-part-1-syslog/](http://www.ducea.com/2006/06/06/rotating-linux-log-files-part-1-syslog/) describes how Ubuntu uses syslog and logrotate.

Coming from a Redhat background, I found fact that syslog rotates log file to be very confusing, why not just let logrotate do that?

Nathan Wiebe

---

### Post by dualusbibook on 2007-01-16
Hi nwiebe,
I haven't gotten the mail logs to stop being rotated yet.  However I did try exactly what you are talking about.

I changed the line to read:

syslogd-listfiles --weekly -s mail.*

However when the weekly rotation runs I get an email from the cron dameon stating that an error occured with the command "syslogd-listfiles --weekly -s mail.*".

Directly from the command line I can enter my command and I get the correct output but obviously not from within the cron job.

What would you say I'm doing incorrectly?  Right now none of my weekly logs are rotated so instead I have been manually doing it.

Also it appears that multiple -s flags cannot be used. (ie. -s mail.log -s mail.err -s mail.info).  I'm not sure what else to try.

Thanks for the followup.

---

### Post by nwiebe on 2007-01-17
Hmm, this a bit weird.  The line below works for me, note that I added double quotes around mail.*

mail.* is being interred by the shell.  In this case it's list all the files that start with **mail.** in the /var/log directory and using that as the argument after -s.  Try this:

```
or LOG in `syslogd-listfiles --weekly -s "mail.*"`
```

That weird part is that I can run the above command, without the added double quotes, straight from the command line under /bin/sh (and bash), and it works fine.  Maybe /bin/sh is started with some other environment vars set when it's run from cron.

Let me know if this works.

Nathan Wiebe

---

### Post by dualusbibook on 2007-01-17
Well I feel silly.  I added the quotes and everything seems to be working aok.

I'm trying to still get the hang of these scripts and have tried writing various ones for myself.  What did the extra quotes do?

Thanks again much appreciated.

---

### Post by nwiebe on 2007-01-17
You know how when you type **ls mail*** it will show you all the files who's names start with mail?

What actually happens is the shell knows that ***** is a special character, and the shell itself expands the list of arguments to **ls** to include all the files that match the mail* pattern.

For example, say you do **ls mail*** in a directory with the following files:

mail.log
mail.err
syslog
messages

when you type **ls mail*** the shell expands **mail*** to **mail.log mail.err**.

So when the shell actually invokes the ls command, the original command **ls mail*** has been expanded into **ls mail.log mail.err**.

The shell was expanding the ***** in the **-s mail.*** in the same way.  So when the command was actually run the full command was **for LOG in `syslogd-listfiles --weekly -s mail.log mail.err mail.out**.  And as you already saw, syslogd-listfiles doesn't know how to deal with multiple arguments to **-s**.

Changing **mail.*** to **"mail.*"** tells the shell not to expand the * character to all matching file names.  It leaves the **mail.*** parameter untouched, so it gets passes to the syslogd-listfiles command in its proper form.

Nathan Wiebe

---

