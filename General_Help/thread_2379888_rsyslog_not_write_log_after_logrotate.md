---
title: "rsyslog not write log after logrotate"
date: 2017-12-11
forum: General Help
---

### Post by redpromo on 2017-12-11
[COLOR=#000000]OS: [/COLOR]Ubuntu 16.04.3 LTS (GNU/Linux 4.4.0-101-generic x86_64)

[COLOR=#000000]rsyslog not writing logfile mail.log after logrotate,
file mail.log is empty.
[/COLOR]
[COLOR=#000000]After restart rsyslog (service rsyslog restart) mail.log starting write.

config logrotate

[/COLOR]> /var/log/mail.info/var/log/mail.warn
/var/log/mail.err
/var/log/mail.log
{
        rotate 48
        weekly
        missingok
        notifempty
        compress
        delaycompress
        sharedscripts
        postrotate
             invoke-rc.d rsyslog rotate > /dev/null
        endscript

}                                
[COLOR=#000000]

I am changed [/COLOR]postrotate in config file by this link [https://github.com/rsyslog/rsyslog/issues/1506](https://github.com/rsyslog/rsyslog/issues/1506), but it did not help.

---

