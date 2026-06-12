---
title: "finding log entries from a week ago"
date: 2013-12-04
forum: General Help
---

### Post by bphillips2 on 2013-12-04
I have a process that is set by cron to run every hour.  It last ran on 11/30/2013 @ 5:00pm, then failed when trying to run at 6:00pm the same day.  Is there a way I can see a log of everything on the computer between that hour to see what may have caused this?

I have looked at /var/log/syslog but it doesn't go back farther than about a day.

Thanks,
Brad

---

### Post by steeldriver on 2013-12-04
logrotate should have saved the immediately preceding syslog as /var/log/syslog.1, and a few even earlier ones which will be gzipped - you can view even the gzipped ones without explicitly gunzipping them using 'less', or search them directly with zgrep e.g.

```
zgrep 'CRON' /var/log/syslog.?.gz
```
or
```
zgrep '*yourprocess*' /var/log/syslog.?.gz
```
or
```
zgrep 'Nov 27' /var/log/syslog.?.gz
```

etc.

---

### Post by Lars Noodén on 2013-12-04
You also have older entries in /var/log/syslog.1and in /var/log/syslog.2.gz through /var/log/syslog.7.gz,  by default.  You 
can set /etc/logrotate.d/rsyslog to retain more, if you have the need and the space.  

[less](http://manpages.ubuntu.com/manpages/saucy/en/man1/less.1.html) is able to read the gzipped files just fine.  You can search for a pattern by pressing slash (/) and then entering the pattern.  

If you're going to try grep, you have to run zgrep on the gzipped files.  To use awk, you have to use zcat or something similar.

```

zgrep "^Nov 28" /var/log/syslog.7.gz | less
zcat /var/log/syslog.5.gz | awk '$1=="Nov" && $2==29 && $3>"11:00:00"{ print }' | less

```

---

### Post by bphillips2 on 2013-12-04
Thanks guys!

I couldn't get your commands to work, so I just unzipped the files.  I appreciate the help!

---

### Post by Lars Noodén on 2013-12-05
If you use the -cd options with [gunzip / gzip](http://linux.die.net/man/1/gzip) then you can leave the original file intact.

```

gzip -cd /var/log/syslog.2.gz | less

```

But "less" should be able to read the gzipped files as they are, at least later versions of "less" can do that.

---

