---
title: "Ubuntu - systemd &amp; tomcat.service - status faild"
date: 2019-07-01
forum: General Help
---

### Post by christian-loeffler on 2019-07-01
hi all

i've got a few of ubuntu (16.04 & 18.04) systems with the problem, that the status for 
tomcat.service - is faild (systemctl 
**but its running**
...
[HTML]systemctl status tomcat
&#9679; tomcat.service - LSB: Start daemon at boot time
   Loaded: loaded (/etc/init.d/tomcat; bad; vendor preset: enabled)
   Active: failed (Result: timeout) since Mo 2019-07-01 10:19:40 CEST; 16min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 715 ExecStart=/etc/init.d/tomcat start (code=exited, status=0/SUCCESS)
   CGroup: /system.slice/tomcat.service

tomcat.service: PID file /var/run/tomcat.pid not readable (yet?) after start: No such file or directory
Jul 01 10:19:40 pbrade1604.p-und-c.de systemd[1]: tomcat.service: Start operation timed out. Terminating.
Jul 01 10:19:40 pbrade1604.p-und-c.de systemd[1]: Failed to start LSB: Start daemon at boot time.
Jul 01 10:19:40 pbrade1604.p-und-c.de systemd[1]: tomcat.service: Unit entered failed state.
Jul 01 10:19:40 pbrade1604.p-und-c.de systemd[1]: tomcat.service: Failed with result 'timeout'.[/HTML]

after restarting the service
*systemctl* shows

[HTML]systemd-ask-password-plymouth.path                           loaded active     waiting         Forward Password Requests to Plymouth Directory Watch
systemd-ask-password-wall.path                               loaded active     waiting         Forward Password Requests to Wall Directory Watch[/HTML]

after a few minutes, systemd get the timeout and the status loaded faild faild

need help! 
:icon_frown:

---

