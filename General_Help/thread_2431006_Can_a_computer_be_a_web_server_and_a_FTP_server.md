---
title: "Can a computer be a web server and a FTP server?"
date: 2019-11-10
forum: General Help
---

### Post by jasper1378 on 2019-11-10
Hello all,

 I don't know if this is a stupid question or not, but can an old desktop be a web server AND a FTP server?

---

### Post by uRock on 2019-11-10
Yes. Recommended? No.

---

### Post by jasper1378 on 2019-11-10
Why would you say that it is not recommended? This is just a hobby project.

---

### Post by jasper1378 on 2019-11-10
Also probably stupid question: if I want to have an HTML website, I would use a web server, correct?

---

### Post by uRock on 2019-11-10
> **jasper1378 said:**
> Why would you say that it is not recommended? This is just a hobby project.
Security. I wouldn't want an internet facing FTP server.
> **jasper1378 said:**
> Also probably stupid question: if I want to have an HTML website, I would use a web server, correct?
Yes. [https://help.ubuntu.com/lts/serverguide/web-servers.html](https://help.ubuntu.com/lts/serverguide/web-servers.html)

---

### Post by yancek on 2019-11-10
FTP is very insecure so if it is not connected to the internet, maybe.  I wouldn't recommend it.  If you want a web server to use on a Local Network, there are numerous sites online explaining how to do that.  Do a search for something like "installing and configuring lamp server on Ubuntu".

---

### Post by Tadaen_Sylvermane on 2019-11-11
Without delving into types of servers, a single machine can function as many services as you want without trouble. Not ideal of course, but it will work assuming things don't share the same ports to use. In my case I used to run apt-cacher-ng, transmission-daemon, mariadb-server, isc-dhcp-server, bind9, minecraft, mythtv-backend, and a few others all on the same bare metal and same ip. Now I use lxd containers to simplify. As long as the hardware can handle it, I would assume no limit to services you can run on a single machine.

---

### Post by TheFu on 2019-11-11
Plain FTP should have died in the 1990s.  Today, we use the secure version, **sftp**.  Use that instead.  sftp is included in the openssh-server package. Install that and it is enabled automatically for authenticated users. Every OS with networking has a good sftp client.

If all you want is a static website, no need for "LAMP".  Just install a web server like nginx or apache, nothing else.  Only install what is needed, not everything including the kitchen sink like a LAMP install would do.  Please.

---

