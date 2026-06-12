---
title: "service jboss start error"
date: 2016-08-11
forum: General Help
---

### Post by abdul225 on 2016-08-11
hi team ,
when im trying to execute service jboss start 
im facing the following error please help me resolve this issue

Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
-- 
-- Unit jboss.service has begun starting up.
Aug 11 18:47:29 abdul-Veriton-M200-A780 systemd[3522]: Failed at step EXEC spawning /etc/init.d/jboss
-- Subject: Process /etc/init.d/jboss could not be executed
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
-- 
-- The process /etc/init.d/jboss could not be executed and failed.
-- 
-- The error number returned by this process is 8.
Aug 11 18:47:29 abdul-Veriton-M200-A780 systemd[1]: jboss.service: control process exited, code=exite
Aug 11 18:47:29 abdul-Veriton-M200-A780 systemd[1]: Failed to start SYSV: JBoss AS Standalone.
-- Subject: Unit jboss.service has failed
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
-- 
-- Unit jboss.service has failed.
-- 
-- The result is failed.
Aug 11 18:47:29 abdul-Veriton-M200-A780 systemd[1]: Unit jboss.service entered failed state.
Aug 11 18:47:29 abdul-Veriton-M200-A780 systemd[1]: jboss.service failed.
Aug 11 18:47:29 abdul-Veriton-M200-A780 polkitd(authority=local)[702]: Unregistered Authentication Ag
Aug 11 18:47:33 abdul-Veriton-M200-A780 systemd-timesyncd[439]: Timed out waiting for reply from 216.
~
~
~
~
~
~
~
~
lines 1445-1469/1469 (END)
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
-- 
-- Unit jboss.service has begun starting up.
Aug 11 18:47:29 abdul-Veriton-M200-A780 systemd[3522]: Failed at step EXEC spawning /etc/init.d/jboss:
-- Subject: Process /etc/init.d/jboss could not be executed
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
-- 
-- The process /etc/init.d/jboss could not be executed and failed.
-- 
-- The error number returned by this process is 8.
Aug 11 18:47:29 abdul-Veriton-M200-A780 systemd[1]: jboss.service: control process exited, code=exited
Aug 11 18:47:29 abdul-Veriton-M200-A780 systemd[1]: Failed to start SYSV: JBoss AS Standalone.
-- Subject: Unit jboss.service has failed
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
-- 
-- Unit jboss.service has failed.
-- 
-- The result is failed.
Aug 11 18:47:29 abdul-Veriton-M200-A780 systemd[1]: Unit jboss.service entered failed state.
Aug 11 18:47:29 abdul-Veriton-M200-A780 systemd[1]: jboss.service failed.
Aug 11 18:47:29 abdul-Veriton-M200-A780 polkitd(authority=local)[702]: Unregistered Authentication Age
Aug 11 18:47:33 abdul-Veriton-M200-A780 systemd-timesyncd[439]: Timed out waiting for reply from 216.2
~
~
~
~
~
~
~
~


thanks in advance

---

