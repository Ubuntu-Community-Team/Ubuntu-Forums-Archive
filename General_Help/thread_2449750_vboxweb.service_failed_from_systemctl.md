---
title: "vboxweb.service failed from systemctl"
date: 2020-09-01
forum: General Help
---

### Post by kingpenguin on 2020-09-01
I was messing around and ran systemctl status. When running this command I see that the status is degraded. When I run systemctl with out status I see that it is the vboxweb.service is failed. When I query the service it is stopped and I do not use it. Is there a way to get rid of this error as I am pretty sure I will never use the vboxweb.service as I just use the application. 
[IMG]https://i.imgur.com/H2rxGWQ.png[/IMG]

---

### Post by kingpenguin on 2020-09-01
I have ran a "journalctl -xe | grep vboxweb" and I got the following output.
[Logs]
Sep 01 17:45:44 Desktop-PC sudo[31441]:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/usr/bin/systemctl start vboxweb
-- Subject: A start job for unit vboxweb.service has begun execution
-- A start job for unit vboxweb.service has begun execution.
Sep 01 17:45:44 Desktop-PC systemd[1]: vboxweb.service: Can't open PID file /run/vboxweb.pid (yet?) after start: Operation not permitted
Sep 01 17:45:44 Desktop-PC systemd[1]: vboxweb.service: Failed with result 'protocol'.
-- The unit vboxweb.service has entered the 'failed' state with result 'protocol'.
-- Subject: A start job for unit vboxweb.service has failed
-- A start job for unit vboxweb.service has finished with a failure.
Sep 01 17:47:43 Desktop-PC sudo[31750]:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/usr/bin/systemctl start vboxweb.service
-- Subject: A start job for unit vboxweb.service has begun execution
-- A start job for unit vboxweb.service has begun execution.
Sep 01 17:47:43 Desktop-PC systemd[1]: vboxweb.service: Can't open PID file /run/vboxweb.pid (yet?) after start: Operation not permitted
Sep 01 17:47:43 Desktop-PC systemd[1]: vboxweb.service: Failed with result 'protocol'.
-- The unit vboxweb.service has entered the 'failed' state with result 'protocol'.
-- Subject: A start job for unit vboxweb.service has failed
-- A start job for unit vboxweb.service has finished with a failure.
Sep 01 17:50:22 Desktop-PC sudo[32098]:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/usr/bin/systemctl reset vboxweb
Sep 01 17:50:31 Desktop-PC sudo[32101]:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/usr/bin/systemctl restart vboxweb
-- Subject: A start job for unit vboxweb.service has begun execution
-- A start job for unit vboxweb.service has begun execution.
Sep 01 17:50:31 Desktop-PC systemd[1]: vboxweb.service: Can't open PID file /run/vboxweb.pid (yet?) after start: Operation not permitted
Sep 01 17:50:31 Desktop-PC systemd[1]: vboxweb.service: Failed with result 'protocol'.
-- The unit vboxweb.service has entered the 'failed' state with result 'protocol'.
-- Subject: A start job for unit vboxweb.service has failed
-- A start job for unit vboxweb.service has finished with a failure.
Sep 01 18:00:16 Desktop-PC sudo[32504]:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/usr/bin/systemctl disable vboxweb
Sep 01 18:38:44 Desktop-PC sudo[35994]:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/usr/bin/systemctl stop vboxweb-service
Sep 01 19:05:27 Desktop-PC sudo[37565]:    chris : TTY=pts/0 ; PWD=/home/chris ; USER=root ; COMMAND=/usr/bin/systemctl start vboxweb.service
-- Subject: A start job for unit vboxweb.service has begun execution
-- A start job for unit vboxweb.service has begun execution.
Sep 01 19:05:27 Desktop-PC systemd[1]: vboxweb.service: Can't open PID file /run/vboxweb.pid (yet?) after start: Operation not permitted
Sep 01 19:05:27 Desktop-PC systemd[1]: vboxweb.service: Failed with result 'protocol'.
-- The unit vboxweb.service has entered the 'failed' state with result 'protocol'.
-- Subject: A start job for unit vboxweb.service has failed
-- A start job for unit vboxweb.service has finished with a failure.

---

### Post by kingpenguin on 2020-09-01
I ended up just running "sudo rm /etc/systemd/system/vboxweb.service" because I do not plan on ever using the web interface. I have no idea if the issue will come back after an update to virtualbox but I will see.

---

