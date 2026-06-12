---
title: "Error Configuring Bacula in Ubuntu"
date: 2015-10-17
forum: General Help
---

### Post by dantezyates on 2015-10-17
I'm configuring bacula with mysql-server in ubuntu 14.03 server first part went well im following these two tutorials [LINK]("https://www.digitalocean.com/community/tutorials/how-to-install-bacula-server-on-ubuntu-14-04") and [LINK]("https://www.digitalocean.com/community/tutorials/how-to-back-up-an-ubuntu-14-04-server-with-bacula") and as i was saying first part went well , second part went well too but at last part when im checking /etc/bacula/bacula-dir.conf before restarting the server i'm getting this error 

"17-Oct 04:34 bacula-dir: ERROR TERMINATION at inc_conf.c:411Config error: Keyword Pool not permitted in this resource
            : line 1, col 5 of file /etc/bacula/conf.d/pools.conf
Pool {"
i followed the tutorial exactly and this pools.conf checked out first time but giving this error now i have no idea why and im using both ubuntu 14.03 server one for server and one for client in virtualbox. Thanks for reading please help

---

