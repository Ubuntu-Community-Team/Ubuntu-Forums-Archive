---
title: "Can't SSH into server"
date: 2014-04-29
forum: General Help
---

### Post by Knute_Snortum on 2014-04-29
I am the admin of a private server.  I'm pretty new to admining.  SSH was working fine, then I upgraded to 14.04.  Something went wrong with the upgrade so I downgraded to 13.04.  Now SSH doesn't work, that is, when a remote tries to connect, the server doesn't respond.  The network card (wireless) works fine.  I can ping 8.8.8.8 without a problem. When I ps -ef | grep sshd I see the process running.  But when I sudo /etc/init.d/ssh status I get no response.  Doing a sh -x /etc/init.d/ssh status I can see that it looks like it is going to /sbin/initctl version, return 0, exit 1.  When I do a /sbin/initctl version, it spits out a version just fine.

Anyone know what could be happening?  What should I do next?

-- 
Knute

---

