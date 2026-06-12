---
title: "mariadb not starting"
date: 2018-09-27
forum: General Help
---

### Post by rcrahul60 on 2018-09-27
mariadb service failed because timeout exceeded
output of journalctl -xe:

Sep 27 12:22:41 tbosss kernel: audit: type=1400 audit(1538031161.267:172): appar
Sep 27 12:22:41 tbosss audit[11385]: AVC apparmor="DENIED" operation="sendmsg" i
Sep 27 12:22:41 tbosss kernel: audit: type=1400 audit(1538031161.367:173): appar
Sep 27 12:22:41 tbosss audit[11385]: AVC apparmor="DENIED" operation="sendmsg" i
Sep 27 12:22:41 tbosss kernel: audit: type=1400 audit(1538031161.467:174): appar
Sep 27 12:22:41 tbosss audit[11385]: AVC apparmor="DENIED" operation="sendmsg" i
Sep 27 12:22:41 tbosss kernel: audit: type=1400 audit(1538031161.567:175): appar
Sep 27 12:22:42 tbosss audit[11385]: AVC apparmor="DENIED" operation="sendmsg" i
Sep 27 12:22:42 tbosss audit[11385]: AVC apparmor="DENIED" operation="sendmsg" i
Sep 27 12:22:42 tbosss kernel: audit: type=1400 audit(1538031162.371:176): appar
Sep 27 12:22:42 tbosss audit[11385]: AVC apparmor="DENIED" operation="sendmsg" i
Sep 27 12:22:43 tbosss audit[11385]: AVC apparmor="DENIED" operation="sendmsg" i
Sep 27 12:22:43 tbosss audit[11385]: AVC apparmor="DENIED" operation="sendmsg" i
Sep 27 12:22:43 tbosss systemd[1]: mariadb.service: Failed with result 'timeout'
Sep 27 12:22:43 tbosss systemd[1]: Failed to start MariaDB 10.1.34 database serv
-- Subject: Unit mariadb.service has failed
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit mariadb.service has failed.
-- 
-- The result is RESULT.
Sep 27 12:22:43 tbosss sudo[11279]: pam_unix(sudo:session): session closed for u

---

### Post by plazman30 on 2018-10-09
How did you solve this?  I am having the exact same problem.  I've been trying every offered "solution"  I can find on the Internet and none of them work.

---

### Post by oldos2er on 2018-10-09
OP hasn't returned for a week. In the meantime I've removed the solved tag since no solution was shared here.

Might be best for you to start a new thread.

---

