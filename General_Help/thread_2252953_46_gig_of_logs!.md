---
title: "46 gig of logs!"
date: 2014-11-16
forum: General Help
---

### Post by ddhuy on 2014-11-16
I just made the partition Ubuntu is bigger, to 110GB, but nog it is full again and when I check with Disk Usage Analyser I see my /var/log is 46GB. I already installed logrotator, but how can I check if it is working and do I need to configure it in some way? When I go down into /var/log/ with Disk Usage Analyser I see the biggest file is only 10MB, so it must be there are a whole lot of log files. My system is becoming unresponsive because it is almost 100% full. How do I remedy this?

---

### Post by ddhuy on 2014-11-16
OK, I looked a bit deeper and my kern.log is 13GB and syslog is 4GB, and logrotates keeps one backup. How do I set my logrotate to not grow these so big?

---

### Post by ddhuy on 2014-11-16
OK, getting closer to the cause, but still don't know what to do.

When I put > tail -f /var/log/kern.log in the terminal, I see the text flashing by incredibly fast, most are of this type
> Nov 16 10:50:03 dimi-ThinkPad-xx-xxxx kernel: [ 8114.659924] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S

Same for syslog. Something to do with wifi. Could it be that I am running an Ad-Hoc wifi from my Ubuntu laptop? And if so, how can I make it not write that much to log?

---

### Post by bapoumba on 2014-11-16
Would you be using a firewall or some other utility that would log every network info ?

---

### Post by ddhuy on 2014-11-16
As far as I know I'm not using a firewall. Just connected with ethernet cable. I noticed that now that I switched off the Ad-Hoc network the logs aren't filling up anymore. So must have been realted to that. Just would like to know how I can use Ad-Hoc network without it filling up my logs and hard drive.

---

### Post by nerdtron on 2014-11-16
Actually by default syslog will be rotated daily and kern.log will be rotated each week. It seems your network card is logging too much.
You can see the config below but I don't think you need to edit it. What you need to find out is why your system logs too much on kern.log and syslog.
```
kenneth@nerdtron:/etc/logrotate.d$ cat rsyslog 
/var/log/syslog
{
    rotate 7
    daily
    missingok
    notifempty
    delaycompress
    compress
    postrotate
        reload rsyslog >/dev/null 2>&1 || true
    endscript
}

/var/log/mail.info
/var/log/mail.warn
/var/log/mail.err
/var/log/mail.log
/var/log/daemon.log
/var/log/kern.log
/var/log/auth.log
/var/log/user.log
/var/log/lpr.log
/var/log/cron.log
/var/log/debug
/var/log/messages
{
    rotate 4
    weekly
    missingok
    notifempty
    compress
    delaycompress
    sharedscripts
    postrotate
        reload rsyslog >/dev/null 2>&1 || true
    endscript
}


```

---

### Post by ddhuy on 2014-11-16
Yes, my logrotate for syslog is the same as yours.

---

### Post by bapoumba on 2014-11-16
You may want to look for iwlwifi logging to syslog and kern.log, for ex this older thread, and see why it is constantly logging :
[http://ubuntuforums.org/showthread.php?t=2141892](http://ubuntuforums.org/showthread.php?t=2141892)
[http://crunchbang.org/forums/viewtopic.php?id=18848](http://crunchbang.org/forums/viewtopic.php?id=18848)

---

