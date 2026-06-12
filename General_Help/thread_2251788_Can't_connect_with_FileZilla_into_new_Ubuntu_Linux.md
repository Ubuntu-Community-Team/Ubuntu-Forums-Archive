---
title: "Can't connect with FileZilla into new Ubuntu Linux Server 14.04.1"
date: 2014-11-06
forum: General Help
---

### Post by Cecil_Champenois on 2014-11-06
Since this is nothing more than a TEST server we used root and root for the username and password. So, when we tried to connect from a WIN7 desktop into the Linux Server on the same network (wired), we could not make a connection as the authentication failed. The username and password seemed to pass though, but right after that, authentication failed.

This is an internal server, of course, with sftp://192.168.0.154, username="root", password="root", and Port="22".

We cannot access this Linux box with FileZilla. Anyone know whether there is some form of tighter security in Ubuntu version 14.04.1?

Cecil

---

### Post by ringstaart on 2014-11-06
Remote root login is probably disabled - I think it does that by default. The reason for that is that crackers will try out ip addresses with open ports and attempt to log in as root by trying common passwords.

To find out, either look in the configuration file or just try to log in with a different account.

---

