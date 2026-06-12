---
title: "Basic Linux Support with some SQUID thrown in!"
date: 2008-04-12
forum: General Help
---

### Post by grrrshn on 2008-04-12
Running Ubuntu Server I installed SQUID to use as a Proxy server.  I wanted to test the server and I ran the following command to look at the access.log:

Sudo tail -f /var/log/squid/access.log

I can see all the clients are working perfectly however I am still seeing the log file and I do not know how to get back to the prompt to work on the server more.  

I know this is probably a no-brainer, however I have no clue as to how to get out of the log file.  I still want the file to be there so I can check it peridocally!

Thanks for being here

grrrshn

---

### Post by NcScZ on 2008-04-12
"Control C" will break out of the tail command

---

