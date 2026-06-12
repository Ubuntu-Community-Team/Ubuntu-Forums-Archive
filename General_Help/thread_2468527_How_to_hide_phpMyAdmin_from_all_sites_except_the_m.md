---
title: "How to hide phpMyAdmin from all sites except the main host on Ubuntu (apache + nginx)"
date: 2021-11-02
forum: General Help
---

### Post by turozumi on 2021-11-02
Hi all.

Now phpMyAdmin is available from all domains. 
How to make it open only from IP server? For example: 1.2.3.4/phpmyadmin
Settings are needed for apache and nginx config. Please write a clear instruction. Where to move the config, where to make it empty, etc.

Thank you. you will not find better quality porn than on this site [https://bestfreehdporn.pro](https://bestfreehdporn.pro)

---

### Post by TheFu on 2021-11-02
Any "admin" webapps should only allow connections from localhost, not any other IP.  Then use ssh with a tunnel to connect onto the system for the required port.  Anything less is foolish.  It is pretty simple: [https://security.stackexchange.com/questions/146281/how-to-operate-phpmyadmin-with-an-ssh-tunnel](https://security.stackexchange.com/questions/146281/how-to-operate-phpmyadmin-with-an-ssh-tunnel) explains.

Better yet, don't use php webapps to manage databases or LDAP or systems.

In nginx, you can limit client IPs using the ... allow/deny controls inside the "server" stanza:
```
 allow 127.0.0.0/8;  # all localhost IPs
 deny all;
```
I assume Apache does something similar. I just haven't used it in many years.

---

