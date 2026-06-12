---
title: "auditd in Ubuntu 12.04 does not register remote ssh commands"
date: 2015-06-12
forum: General Help
---

### Post by ajzach on 2015-06-12
I have auditd configured in Ubuntu 12.04:

/etc/audit/audit.rules
-a exit,always -F arch=b64 -F uid=1001 -S execve
-a exit,always -F arch=b32 -F uid=1001 -S execve
-a exit,always -F arch=b64 -F uid=500  -S execve
-a exit,always -F arch=b32 -F uid=500  -S execve
-a exit,always -F arch=b64 -F uid=0    -S execve
-a exit,always -F arch=b32 -F uid=0    -S execve

If I execute ssh user@server ls the command ls does not appear in syslog, if I login to the instance, all executed commands are registered.

Someone had the same problem?

---

