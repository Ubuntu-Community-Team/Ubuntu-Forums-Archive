---
title: "Ubuntu 'last' command show IP address"
date: 2014-08-11
forum: General Help
---

### Post by elliotbeken on 2014-08-11
Hi All,

I have a Ubuntu server with a few users who have SSH access. To see whats users have/are logged in I use the last command.

The main information I am looking to see is the username and the IP address they are logging in from, sometimes the IP is shown but other times a name is shown (E.G. 34533.yesd.virgin.net)

Is there a way i can show only the IP addresses.

Thanks

---

### Post by TheFu on 2014-08-11
**man last** 

This found the option you want  - -i

---

### Post by elliotbeken on 2014-08-11
Wow i didnt even think to use the man command !

Rookie error!

---

