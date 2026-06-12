---
title: "logrotate send using attachment"
date: 2013-05-09
forum: General Help
---

### Post by bullet333 on 2013-05-09
Ubuntu 12.10
Squid3 3.1
Dansguardian 2.10.1.1
Postfix 2.9.6
Webmin 1.620
Logrotate [COLOR=#333333][FONT=sans-serif]3.7.8
[/FONT][/COLOR]
I have logrotate setup to send me the log files from Squid3 via email.  Even though it works just fine, the log files aren't sent as attachments but rather the entire log files contents are within the message body.  Is there a way to send these log files as attachments?

---

### Post by slickymaster on 2013-05-09
Even though I'm not completely sure because I haven't use it in years, I don't remember logrotate having the ability about sending mailing as attachments, but you could take a look at logrotate man page to confirm it.

Creating e-mail messages, including adding attachments or signatures, is the function of a mail user agent (MUA). If you have the mail user agent mutt (or can install it), it should be able to do what you want, just write a separate script to E-mail attachments using ```
mutt -s
```

---

### Post by bullet333 on 2013-05-10
Thanks for the reply, but the reason I'm using logrotate is because I don't know how to script.  I'm a linux noob.  :(

I might stop emailing the Squid log files anyways because they're available via Webmin more user friendly.  I was thinking of keeping the Squid logs but I don't think I need to.  The only other log file I'm watching is the syslog.  You think there's any other logs I should be watching on my system?  Maybe kernel?

---

### Post by tgalati4 on 2013-05-10
What files you watch depends on what is important in terms of performance of your servers.  If all you care about is uptime, then install *rwho* and *rwhod* and periodically use* ruptime* to make sure your system is up and running.  You want to make sure you don't run out of disk space (*df -h*) and you need an UPS to keep the power going.  The UPS can send emails or text messages when the power goes out.  Other than that, you really don't need all of the data in log files, until there is a problem.  You can also send the syslog data to another linux machine's syslog and filter the messages that get sent using rsyslog.conf:

```
man rsyslog.conf
```

Scripting is a useful skill to have when running servers.

---

### Post by slickymaster on 2013-05-10
> **tgalati4 said:**
> What files you watch depends on what is important in terms of performance of your servers...

[COLOR=#000000]tgalati4 is right, and besides what he has posted I would recommend you a read on [/COLOR][Linux Log Files]("https://help.ubuntu.com/community/LinuxLogFiles")[COLOR=#000000]., especially the [/COLOR][COLOR=#000000]System Logs[/COLOR][COLOR=#000000] and [/COLOR][COLOR=#000000]Application Logs items.[/COLOR]

---

### Post by bullet333 on 2013-05-13
Thanks for all the great information!  I'm currently using Monit to monitor the services, system, and disk usage.

---

### Post by slickymaster on 2013-05-13
Glad you got it working. Please[ mark your thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") if you think it provides a working solution for your problem.

---

