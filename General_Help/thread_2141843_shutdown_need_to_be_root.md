---
title: "shutdown: need to be root"
date: 2013-05-03
forum: General Help
---

### Post by johnpintor on 2013-05-03
i was constructing a code for shutting down all my PC's in a network (50 PC's) simultaneously.

the Code is: ssh -X -p2323 user@ip shutdown -h now

but i got this line: shutdown: Need to be root

I'm logged in as a root user but can't seem to make this code run. Help please.

---

### Post by pqwoerituytrueiwoq on 2013-05-03
just cause ssh is beign run at root does not mean the client is root
[FONT=courier new]ssh -X -p2323 root@ip shutdown -h now[/FONT]
would work
now if you run that as root you can do this
[FONT=courier new]ssh -X -p2323 172.15.14.2 shutdown -h now[/FONT]

---

