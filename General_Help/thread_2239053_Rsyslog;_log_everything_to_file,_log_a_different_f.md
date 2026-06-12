---
title: "Rsyslog; log everything to file, log a different file to a remote server only"
date: 2014-08-11
forum: General Help
---

### Post by DigiAngel on 2014-08-11
Hi Everyone.

I've been having one heck of a time trying to get a file to go to a remote syslog server ONLY.  Here's my setup...a standard rsyslog.conf with one addition:

```
auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
kern.*                          -/var/log/kern.log
mail.*                          -/var/log/mail.log
*.*                             @10.1.1.1
mail.err                        /var/log/mail.err

news.crit                       /var/log/news/news.crit
news.err                        /var/log/news/news.err
news.notice                     -/var/log/news/news.notice

*.emerg                                :omusrmsg:*

daemon.*;mail.*;\
        news.err;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       |/dev/xconsole

```

This logs all messages to a remote server.  So far so good.  Now...I'd like to send a completely different log file to a different remote server.  I tried creating /etc/rsyslog.d/60-bro.conf and it contains:

```
$ModLoad imfile #
$InputFileName /media/backup/bro/current/conn.log
$InputFileTag bro_conn:
$InputFileStateFile stat-bro_conn
$InputFileSeverity info
$InputFileFacility local7
$InputRunFileMonitor
#check for new lines every second
$InputFilePollingInterval 1
local7.* @10.0.0.2:6514

```

But as soon as I restart rsyslog I see my conn.log file going to 10.1.1.1 as well.  Is there something I'm missing to get this to NOT go to 10.1.1.1?  Thank you.

---

### Post by tgalati4 on 2014-08-12
Well I learned that the "r" in rsyslog stands for Rocket-fast not Remote.  Some remote logging tips here:  [http://www.rsyslog.com/doc/master/tutorials/reliable_forwarding.html](http://www.rsyslog.com/doc/master/tutorials/reliable_forwarding.html)

Are you running *rsyslog* on both receiving servers?  This will improve message transport reliability.

Also, *.* means everything, so why would you expect conn.log not to get logged to 10.1.1.1 as well?  You would have to spell out each log file separately that you want to log to 10.1.1.1 (leaving out conn.log) or add a local filter to screen out conn.log messages (requiring extra CPU cycles to both log and screen out messages).

---

### Post by DigiAngel on 2014-08-12
Solved this with making this change:

```
*.*;local7.none      @10.1.1.1
```

Hope this helps someone somewhere.

---

