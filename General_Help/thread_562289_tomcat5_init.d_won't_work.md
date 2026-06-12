---
title: "tomcat5 init.d won't work"
date: 2007-09-28
forum: General Help
---

### Post by thesheff17 on 2007-09-28
ok I have default install of the ubuntu server 6.06.1 with all updates and tomcat5 running in it.

When I run this from the local machine everything is fine:

root@test01:~# /etc/init.d/tomcat5 stop
Stopping Tomcat 5 servlet engine: .tomcat5.
root@test01:~# /etc/init.d/tomcat5 start
Starting Tomcat 5 servlet engine using Java from /usr/lib/kaffe: tomcat5.
root@test01:~#

Now when I am trying to start and stop it with a script from a remote machine I can never get the script to finish when it starts tomcat5

root@dsheffner2-desktop:/# ssh 192.168.7.165 '/etc/init.d/tomcat5 stop'
Stopping Tomcat 5 servlet engine: .............................. (killing) . (ki                                                                             lling) tomcat5.
root@dsheffner2-desktop:/# ssh 192.168.7.165 '/etc/init.d/tomcat5 start'
Starting Tomcat 5 servlet engine using Java from /usr/lib/kaffe: tomcat5.

NEVER RETURNS BACK TO root@dsheffner2-desktop:/#

I have checked the log, everything is working fine.  Tomcat5 does start but never returns to the prompt for me to continue my script.  Can anyone shed some light on this error.  Thanks in advance.

---

