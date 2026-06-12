---
title: "Syslog messages from remote host to Gnome desktop"
date: 2007-01-06
forum: General Help
---

### Post by btrotter on 2007-01-06
I have a Linksys router that I have set up to forward Syslog messages to my Ubuntu 6.10 desktop.
I have edited:
/etc/init.d/sysklogd and added 
SYSLOGD="-r -u syslog"

/etc/default/syslogd and added
SYSLOGD="-r"

I then ran "sudo /etc/init.d/sysklogd restart"

This has made it so I see messages appearing in the /var/log/messages file such as:

Jan  6 03:04:32 192.168.1.1 syslogd started: BusyBox v0.60.0 (2005.02.05-17:17+0000)
or
Jan  6 03:24:33 192.168.1.1 -- MARK --

I also see a lot of messages appearing in /var/log/syslog


In order to read these messages, I have to do a "more /var/log/syslog"

I would like to have something that I could run in Gnome which showed the contents of /var/log/syslog, and refreshed when the file refreshed. Or maybe a program written specifically for interpreting the output of syslog. 

Any ideas?

Thanks for your help.

---

### Post by Slim Odds on 2007-03-09
Simple answer: tail -f /var/log/syslog

---

### Post by LinuxGuyInVA on 2008-01-16
Try [FONT="Courier New"]xconsole.[/FONT]  I've used it for years (first on SunOS 4.1 believe it or not :shock:) and it still works nicely in Ubuntu.  To install:

> apt-get install xconsole

You may want to add this line to your [FONT="Courier New"]/etc/syslog.conf[/FONT] file:

```
daemon.*;mail.*;\
        news.err;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       |/dev/xconsole

```

if it's not already there.  Works like a charm for me.  

Now if I can only figure out a way to get syslogd on my Ubuntu server to put the dd-wrt logs from my linksys into a separate file (short of installing syslog-ng)...

 - Pat

---

