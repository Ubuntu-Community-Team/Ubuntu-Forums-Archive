---
title: "gethostbyaddr(xxx.xxx.xxx.xx2) failed: 1"
date: 2014-11-04
forum: General Help
---

### Post by bobptz on 2014-11-04
In the syslog I get the following errors every five minutes:
```
Nov  4 04:05:02 server1 sendmail[11182]: gethostbyaddr(xxx.xxx.xxx.xx2) failed: 1
```

xxx.xxx.xxx.xx2 is the SECOND IP address of the VPS.  I have msmtp, not postfix.  ubuntu 12.04 server.

This is my /etc/hosts file:
127.0.0.2 server1
127.0.0.1 localhost.localdomain localhost
# Auto-generated hostname. Please do not remove this comment.
xxx.xxx.xxx.xx1 server1.surf-anonymous.info  server1
::1 localhost.localdomain localhost

xxx.xxx.xxx.xx1 is the FIRST IP address of the VPS.

Do I have to add anything there?

---

### Post by bobptz on 2014-11-21
2 weeks later and I cannot solve it myself.  

I thought this is a very trivial matter for somebody who knows linux.

---

