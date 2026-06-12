---
title: "Time Sync not working"
date: 2020-05-22
forum: General Help
---

### Post by Only1KW on 2020-05-22
I'm on Ubuntu 18.04 still and attempting to set up time synchronization on my system for the first time.  But it's not working for reasons I don't understand and don't know how to debug:

```
username@host ~ $ sudo timedatectl set-ntp on
[sudo] password for username: 
username@host ~ $ timedatectl
                      Local time: Fri 2020-05-22 11:43:44 CDT
                  Universal time: Fri 2020-05-22 16:43:44 UTC
                        RTC time: Fri 2020-05-22 16:43:58
                       Time zone: America/Chicago (CDT, -0500)
       System clock synchronized: no
systemd-timesyncd.service active: yes
                 RTC in local TZ: no
…
username@host ~ $ timedatectl
                      Local time: Fri 2020-05-22 12:04:11 CDT
                  Universal time: Fri 2020-05-22 17:04:11 UTC
                        RTC time: Fri 2020-05-22 17:04:26
                       Time zone: America/Chicago (CDT, -0500)
       System clock synchronized: no
systemd-timesyncd.service active: yes
                 RTC in local TZ: no
```

Any idea why it won't sync even after 20 minutes?

---

### Post by lvm on 2020-05-22
No idea. I don't go with this newfangled stuff, adding '0       6       *       *       *       /usr/sbin/ntpdate pool.ntp.org>>/var/log/ntpdate.log 2>&1' to crontab works now just as fine as20 years ago.

---

