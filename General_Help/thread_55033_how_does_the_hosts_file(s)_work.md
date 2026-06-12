---
title: "how does the hosts file(s) work ?"
date: 2005-08-07
forum: General Help
---

### Post by glandula on 2005-08-07
just wondering how the hosts files work. there seems to be three of them, hosts, hosts.allow and hosts.deny

i want to use them like in windows, u know like:
 127.0.0.1  badadserver.com

should i put it all in the deny file ? should it in that case be a list of bad server with no 127.0.0.1 ? 

can i use the hosts files from for example [http://hosts-file.net/](http://hosts-file.net/) ? if so where do i put them and do i need to modify them in any way ?

thanks

---

### Post by PeP on 2005-08-07
[QUOTE=glandula]just wondering how the hosts files work. there seems to be three of them, hosts, hosts.allow and hosts.deny

i want to use them like in windows, u know like:
 127.0.0.1  badadserver.com

should i put it all in the deny file ? should it in that case be a list of bad server with no 127.0.0.1 ? 

can i use the hosts files from for example [http://hosts-file.net/](http://hosts-file.net/) ? if so where do i put them and do i need to modify them in any way ?

thanks[/QUOTE]
 just use /etc/hosts  like in windows 
host.allow and host.deny allows/deny the host to  connect to your machine.

---

