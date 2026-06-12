---
title: "which log file for sysctl.conf errors?"
date: 2019-04-20
forum: General Help
---

### Post by rattskjelke on 2019-04-20
If there is something wrong in */etc/sysctl.conf* or */etc/ufw/sysctl.conf* which log file would contain the error messages?

---

### Post by TheFu on 2019-04-20
Check the all ...

```
sudo egrep -i 'error|warn' /var/log/*g
```
Any lines shown will begin with the specific filename, so you can check it for more details above and below the actual issue.

---

