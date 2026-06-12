---
title: "syslog rotate"
date: 2008-04-10
forum: General Help
---

### Post by jethro10 on 2008-04-10
Hi,

There's lots of info on lograotate etc but it seems a scary jump to try stuff incase it goes wrong -seems fundaments.

I want to keep more copies of the syslog, just that one as i've set it to remotley log other devices.

It would be really nice to keep the syslog files dated rather than just a few of them numbered

eg todays syslog would be kept tomorrow as syslog.20081003  rather than syslog.0

I'm stuck, can anyone help.
J

---

### Post by discorsage on 2008-04-10
This looks like it may be helpful :

[http://www.linuxforums.org/forum/redhat-fedora-linux-help/10438-logrotate-date-stamp.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/10438-logrotate-date-stamp.html)

If you are nervous about messing up your existing logs, create a test directory, create an /etc/cron.test directory, copy your daily logrotate script in and edit it making sure that the new script does not refer at all to your existing logs

---

### Post by jethro10 on 2008-04-11
> **discorsage said:**
> This looks like it may be helpful :

[http://www.linuxforums.org/forum/redhat-fedora-linux-help/10438-logrotate-date-stamp.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/10438-logrotate-date-stamp.html)

If you are nervous about messing up your existing logs, create a test directory, create an /etc/cron.test directory, copy your daily logrotate script in and edit it making sure that the new script does not refer at all to your existing logs

Right,
in /etc/cron.daily there is a syslogd file that looks like its the one, it uses syslogd-listfiles to choose it's files.
When i type that I get /var/log/syslog although the last part, syslog is not a directory so I assume it referes to the syslog file itself.

So it looks like in this syslogd file I can add a few lines to try copying a file out and dont need to worrk i'm screwing things up?

Is this assesment about right?

EDIT : Looks like if I put it just before the savelog loop, i'll get a copy of the syslog file just before the cron job does it's business, and I can extend this to put it somewhere in an archive or the like.

EDIT " : For my purposes, could I just not add my own cron job to fire off just before the logs rotate ? if so how can I ascertain this time. It would then continue to work even if ubuntu updated this in an update.

Jeff

---

