---
title: "too long waitig for password promt and mysql queries"
date: 2008-03-20
forum: General Help
---

### Post by swigrid on 2008-03-20
Hi,

I have minor but annoying problem. When I want to access to my ubuntu server(by ssh) from anywhere I have to wait for password promt around 13secs. This would be so annoying but, when I m accessing to mysql (on same server) through mysqlquerybrowser or mysqladministrator validation takes ages (13secs). That would be fine still, but each query what I do takes 13secs as well and it really annoys me ](*,). If I m access to mysql through myphpadmin queries are done in normal speed.  I m on LAN so I don't think so it is slowing it down...

thank you for any help

---

### Post by wormser on 2008-03-20
I had a problem like this on a BSD system.  It ended up being a DNS issue.  In the sshd config file uncomment the DNS line and change to no.  It is worth a shot.  Also, you might want to look into shared keys instead of password authentication.  There are some HowTos on the forum.

---

### Post by swigrid on 2008-03-20
thanx for reply

...access to mysql server is not related with ssh... or is it?
and I didn't find any mention about DNS in sshd_config

---

### Post by wormser on 2008-03-20
> **swigrid said:**
> I have minor but annoying problem. When I want to access to my ubuntu server(by ssh) from anywhere I have to wait for password promt around 13secs.

> **swigrid said:**
> thanx for reply

...access to mysql server is not related with ssh... or is it?
and I didn't find any mention about DNS in sshd_config

You said (by ssh).  It just sounds exactly what my problem was and that is what the solution was.  The second part of this link is what solved my issue.

[http://maestric.com/en/doc/fix-slow-ssh-connections-delays-on-mac-os-x](http://maestric.com/en/doc/fix-slow-ssh-connections-delays-on-mac-os-x)

> sudo vi /etc/sshd_config

Replace this line:
#UseDNS yes

by:
UseDNS no
Again, don't forget to remove the sharp. That's it !

Note:
May be you're not enthusiastic about hacking your SSH configuration files. Another solution is to add the IP addresses you're going to connect to (or which are going to connect to your mac) in /etc/hosts.

---

### Post by swigrid on 2008-03-20
> 
when I m accessing to mysql (on same server) through mysqlquerybrowser or mysqladministrator validation takes ages (13secs). That would be fine still, but each query what I do takes 13secs as well and it really annoys me


I didn't find dns option there, but I added it there and ssh is fine now... Just MySQL server now

thank you

---

### Post by wormser on 2008-03-20
I do not know if MySQL has the same type of option in its config but it is worth a shot.  I believe there is a bug in the DNS in the open source.  It could be effecting MySQL too.

---

### Post by swigrid on 2008-03-20
I always do, but I didn't know, they are two different problem... SSH and MySQL will have a look around it...

---

