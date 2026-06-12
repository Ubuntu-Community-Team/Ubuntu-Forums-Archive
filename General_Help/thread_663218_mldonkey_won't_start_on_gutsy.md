---
title: "mldonkey won't start on gutsy"
date: 2008-01-09
forum: General Help
---

### Post by kochakaden on 2008-01-09
I can't get mldonkey to start.  when I run  /etc/init.d/mldonkey-server start, it says:

Starting MLDonkey: mlnet.

But nothing actually starts:

 ps ax |grep mlnet
 9267 pts/0    R+     0:00 grep mlnet

and the logfile is empty:

 ls -l /var/log/mldonkey/
total 0
-rw-r--r-- 1 root root 0 2008-01-09 19:15 mlnet.log


Has anyone gotten mldonkey running on the latest ubuntu?

---

### Post by lukedoomer on 2008-02-01
I got same problem. but until now, cannot figure out what happened and how to solve this problem.
Hope someone would help this?

---

### Post by tubaman on 2008-02-09
Start it manually and see if there are any errors:
sudo -u mldonkey /usr/bin/mlnet

---

