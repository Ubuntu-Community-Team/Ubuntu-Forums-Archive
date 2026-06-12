---
title: "NUT (Network UPS Tools) - sepatare syslog file"
date: 2019-08-02
forum: General Help
---

### Post by dak2019 on 2019-08-02
Hello everyone,

By default log entries geneated by NUT
are stored in /var/log/syslog file.

How can i set a sepatare file for this?

Eg. /var/log/nutlog.log

---

### Post by tryfail on 2019-11-01
dak2019,

Very briefly, the following is required when using Ubuntu 18:

The default system logger is rsyslog. Add the following to /etc/rsyslog.d/99-nut.conf 
```
:syslogtag,contains,"upsmon" /var/log/nut.log
:syslogtag,contains,"nut" /var/log/nut.log
:syslogtag,contains,"upssched" /var/log/nut.log
```

touch /var/log/nut.log
chown syslog:adm /var/log/nut.log 
chmod 640 /var/log/nut.log
systemctl restart rsyslog

---

### Post by dak2019 on 2019-11-04
> **tryfail said:**
> dak2019,

Very briefly, the following is required when using Ubuntu 18:

The default system logger is rsyslog. Add the following to /etc/rsyslog.d/99-nut.conf 
```
:syslogtag,contains,"upsmon" /var/log/nut.log
:syslogtag,contains,"nut" /var/log/nut.log
:syslogtag,contains,"upssched" /var/log/nut.log
```

touch /var/log/nut.log
chown syslog:adm /var/log/nut.log 
chmod 640 /var/log/nut.log
systemctl restart rsyslog

Briefly and professional, thanks a lot.

---

