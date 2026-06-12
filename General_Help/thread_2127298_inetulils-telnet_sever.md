---
title: "inetulils-telnet sever"
date: 2013-03-19
forum: General Help
---

### Post by rocketrrt on 2013-03-19
First I know telnet is not secure but does not matter in this case local network. no outside access, no Internet, nothing.

I have had telnet-server package install and working.  I wanted to get rid of the host name on the login message(due to screen size only 20 chars).  What I found was to use the use inetutils-telnet server package (can put -h in /etc/inetd.conf) but after install when I try to connect, it connects and I get escape character message and it waits for about 5 sec and then connection closed by foreign host.  It never asks for login or password?  Not sure what to look at.  I have not put -h in as of yet.

Any ideas would be helpful.


Thanks

---

