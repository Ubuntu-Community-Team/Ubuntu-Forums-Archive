---
title: "Systat error every 10 minutes??"
date: 2007-09-19
forum: General Help
---

### Post by JCorrea920 on 2007-09-19
My system log shows an error every 10 minutes of a CRON command that is _[COLOR="Red"]NOT[/COLOR]_ listed under ```
sudo crontab -e
```

/var/log/syslog:
```
Sep 14 11:15:01 server1 /USR/SBIN/CRON[15707]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
```

I googled it and found that debian linux had some sort of issue with systat and reccommended these packages:

[http://www.parisc-linux.org/~carlos/debian-work/sysstat/]("http://www.parisc-linux.org/~carlos/debian-work/sysstat/")

I am not sure exactly what to do with all these packages. Or which ones will apply to my Ubuntu LTS software. Has anyone seen this before?

jcorrea920

Dell PowerEdge SC420
Ubuntu 6.06 LTS Server
kernel 2.6.15-23-386

---

