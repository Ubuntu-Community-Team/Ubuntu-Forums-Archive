---
title: "unable to connect to mysql remotely while &quot;bind-address = 0.0.0.0&quot;"
date: 2013-10-22
forum: General Help
---

### Post by odror on 2013-10-22
OS: Ubuntu 13.10

I set the bind-address to 0.0.0.0 in my.cnf

I restarted mysql, but outside access is still blocked.

When I type:  netstat -tnl | grep 3306

I get:

tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN

I should be getting:

tcp        0      0 0.0.0.0:3306          0.0.0.0:*               LISTEN

Is there anything else that I am missing

Thanks

---

