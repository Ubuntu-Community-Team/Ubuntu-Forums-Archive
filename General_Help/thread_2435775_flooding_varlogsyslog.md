---
title: "flooding /var/log/syslog"
date: 2020-01-25
forum: General Help
---

### Post by 007casper on 2020-01-25
flooding /var/log/syslog

last month or so the / always ran low on disk. It was puzzling. I did bleachbit and kept going, and then it will creep up again. Root had 24.1 GB disk space, there isnt a way it was filling up.

I saw that syslog was 12.1 GB. I emptied syslog. sudo sh -c 'cat /dev/null > /var/log/syslog'

Then, it filled up in less than five minutes.
 
then, I looked up syslog. It seemed 1481 kept writing messages. I killed the process. The computer shut down, and now it cant boot. 

Please, advise. Thank you so much.

---

