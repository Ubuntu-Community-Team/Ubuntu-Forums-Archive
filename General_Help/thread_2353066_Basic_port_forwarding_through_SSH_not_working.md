---
title: "Basic port forwarding through SSH not working"
date: 2017-02-18
forum: General Help
---

### Post by Gottier on 2017-02-18
Local machine is Ubuntu 14.04 desktop with LAMP (MariaDB on port 3306). Remote machine is unknown linux LAMP type server accepting SSH connections on port 2233.

So I do this in terminal:

ssh -L 3307:xxx.xxx.xxx.xxx:3306 -p 2233 [email]me@remoteserver.com[/email] -N

But when I try to connect to the remote server MySQL (127.0.0.1 and port 3307) it is obvious that I am getting errors from local MariaDB. I say this because if I stop MariaDB on the local machine, the error messages change.

I do get a prompt on the remote server if I leave off the -N, and I can connect with a standard SSH connection just fine. Are there things to look for that would be holding back the port forwarding? Is my command right?

---

### Post by oldos2er on 2017-02-18
Duplicate of [https://ubuntuforums.org/showthread.php?t=2353064](https://ubuntuforums.org/showthread.php?t=2353064) closed.

---

