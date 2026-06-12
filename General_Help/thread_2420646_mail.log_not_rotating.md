---
title: "mail.log not rotating"
date: 2019-06-08
forum: General Help
---

### Post by RegUB on 2019-06-08
Our server (14.04) has the standard logrotate config, but /var/log/mail.log is not rotating so just continues to grow.

mail.err is rotating as specified below, i.e. 4 old copies on a weekly basis. Why is mail.log not doing likewise?

```
root@localhost:/tmp# cat /etc/logrotate.d/rsyslog
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

### Post by TheFu on 2019-06-08
14.04 supported ended a few months ago.
It is passed time to move to a newer LTS release.  I had to move our email server up to 16.04. Would have preferred moving to 18.04, but Zimbra doesn't support that yet.

---

### Post by RegUB on 2019-06-08
> **TheFu said:**
> 14.04 supported ended a few months ago.
It is passed time to move to a newer LTS release.  I had to move our email server up to 16.04. Would have preferred moving to 18.04, but Zimbra doesn't support that yet.

I know, but this is not a support issue as such. In any case the problem predates the end of 14.04 support. What I really need to know is whether there is anything else in the config that I should be looking for.

---

### Post by TheFu on 2019-06-08
I don't have any 14.04 anymore.  On 16.04, this is it:
```
....
/var/log/messages
{
        rotate 4
        weekly
        missingok
        notifempty
        compress
        delaycompress
        sharedscripts
        maxsize 1M
        postrotate
                /usr/lib/rsyslog/rsyslog-rotate
        endscript
}

```
Things are different in the next LTS.  It works:
```
$ ll mail.log*
-rw-r----- 1 syslog adm 13007 Jun  8 07:20 mail.log
-rw-r----- 1 syslog adm 14881 Jun  2 09:25 mail.log.1
-rw-r----- 1 syslog adm  1642 May 26 00:20 mail.log.2.gz
-rw-r----- 1 syslog adm  2507 May 20 11:15 mail.log.3.gz
-rw-r----- 1 syslog adm  1725 May 12 00:18 mail.log.4.gz

```

---

### Post by SeijiSensei on 2019-06-08
Is there a cron job to run logrotate every day? On my machines, the logrotate script resides in /etc/cron.daily.  The cron.daily scripts are invoked in /etc/crontab like this:

```

25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )

```

---

