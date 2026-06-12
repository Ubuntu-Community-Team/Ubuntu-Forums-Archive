---
title: "Deploy software to client via server"
date: 2015-08-27
forum: General Help
---

### Post by tamil4 on 2015-08-27
Is there any services to deploy applications to client via server is available on Linux .
In windows server there is an option 1

---

### Post by TheFu on 2015-08-27
Hundreds

ssh + scripts - that is how most people start out, writing little scripts.
ansible
puppet
chef

All are free for any size need.  Of course, some are backed by companies who would like you to buy the "enterprise" GUI ... but I think that is just for DoD and huge corporations. Everyone else uses the F/LOSS versions.

These aren't just for installing packages. They can manage a system completely. If you are really new to Linux coming from Windows, you need to become a power-user first. We tend to customize any solution for our systems, networks, needs. That means writing some glue scripts.

The learning curve is steep - just like with Windows, but changing your mind to get the Unix philosophy will be necessary. We don't think like you - unix people.  Don't forget that you probably spend 5+ yrs learning Windows and much of that knowledge DOES NOT transfer to Unix.

If you don't have ssh setup for ssh-key-based authentication to all the clients, do that first and get used to using ssh.

If you'd like more help, please ask.

---

