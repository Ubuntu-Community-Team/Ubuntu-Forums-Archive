---
title: "Sar problem"
date: 2017-12-30
forum: General Help
---

### Post by raleigh3 on 2017-12-30
andy@7:~/Downloads$ sar
Cannot open /var/log/sysstat/sa30: No such file or directory
Please check if data collecting is enabled

```
#
# Default settings for /etc/init.d/sysstat, /etc/cron.d/sysstat
# and /etc/cron.daily/sysstat files
#

# Should sadc collect system activity informations? Valid values
# are "true" and "false". Please do not put other values, they
# will be overwritten by debconf!
ENABLED="true"
```

---

