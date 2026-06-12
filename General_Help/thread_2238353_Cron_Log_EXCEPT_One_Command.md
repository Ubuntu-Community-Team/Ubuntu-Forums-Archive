---
title: "Cron Log EXCEPT One Command"
date: 2014-08-07
forum: General Help
---

### Post by wewantutopia on 2014-08-07
Hello all,

I have a custom cron setup that works great for an old laptop I have running as a file server.  I also have logging working fine too.  Has been good for a long time.  One of the things I have cron do is kill vino server in the middle of the night and a minute later restart it since it is prone to stop working when I need it.  The only problem is, since I have logging running, it logs the vino session when I access the server.  I now have a mail file that is 19 GB big!

I like this setup and don't want to use x11vnc or any other ssh/vnc program

Is there a way I can run the start vino-server command without logging that one operation?  Thanks!

Here is that section of crontab

```
51 02 * * * killall vino-server

52 02 * * * DISPLAY=:0.0 /usr/lib/vino/vino-server
```

---

### Post by tgalati4 on 2014-08-07
A couple of points:

Do you have to use a vnc server?  Can't you use X-forwarding with ssh to perform whatever functions you need on the server?

Normally, daily cronjobs are put in /etc/cron.daily.  Take a look at those scripts.  You can create a script and put it in there and it will get run daily.  You can use >/dev/null at the end of the command to dump the output to the bit bucket.  The server itself may write to the log file, so you will have to look at its settings.

You can use a variation:   >/dev/null 2>&1   [http://www.xaprb.com/blog/2006/06/06/what-does-devnull-21-mean/](http://www.xaprb.com/blog/2006/06/06/what-does-devnull-21-mean/)

>/dev/null will dump normal output (called Standard Output, channel 1) to the bit bucket.  Errors (Standard Error, channel 2) should get logged to the system log as any normal cronjob message.

>/dev/null 2>&1 will dump errors (channel 2 back into channel 1) and normal output into the bit bucket.

---

### Post by wewantutopia on 2014-08-07
It set this up using ```
EDITOR=gedit crontab -e
``` not by adding a script to /etc/cron.daily

Can I just change my crontab to read like this:

```
51 02 * * * killall vino-server

52 02 * * * DISPLAY=:0.0 /usr/lib/vino/vino-server >/dev/null 2>&1
```

I enabled the stand alone cron log with this:

```

[LIST=1]
[*]Edit /etc/syslog.conf and uncomment the line starting withcron.*
[*]Run /etc/init.d/sysklogd restart
[*]Run /etc/init.d/cron restart
[/LIST]

```

---

