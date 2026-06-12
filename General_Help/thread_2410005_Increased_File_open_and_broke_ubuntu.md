---
title: "Increased File open and broke ubuntu?"
date: 2019-01-09
forum: General Help
---

### Post by supremespre on 2019-01-09
Long story short. I used the following commands to increase file open limit

```
echo "fs.file-max=100000" >> /etc/sysctl.conf && sysctl -p
```

```
echo "* soft nofile 1000000" >> /etc/security/limits.conf
echo "* hard nofile 1000000" >> /etc/security/limits.conf
```
```
echo "session required pam_limits.so" >> /etc/pam.d/common-session
```

restarted, and can now not access it unless it is in rescue mode, I have already fixed the limits.conf, but i believe i am missing a step or two as she still won't boot up regularly.


Ubuntu 16.04

---

