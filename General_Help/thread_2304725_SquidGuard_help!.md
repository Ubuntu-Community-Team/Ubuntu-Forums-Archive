---
title: "SquidGuard help!"
date: 2015-11-29
forum: General Help
---

### Post by SuperGeorge on 2015-11-29
i am trying to block porn AND dating sites using squid.    as of the moment, this config is only blocking porn sites and totally ignoring my dating sites set up.   Any help on why this is happening would be greatly appreciated.  Thanx guys

here's my squidguard.conf

dbhome /var/lib/squidguard/db
logdir /var/log/squidguard


dest porn {
        domainlist porn/domains
        urllist porn/urls
        logfile porn.log
        redirect [http://127.0.0.1/index.html](http://127.0.0.1/index.html)
        }
dest dating {
         domainlist dating/domains
         urllist dating/urls
         logfile dating.log
         redirect [http://127.0.0.1/index.html](http://127.0.0.1/index.html)
         }


acl {
        default {
                pass !porn !dating all
               
        }
 }
all permissions are fine for the DB's and they are loading according to the log file

---

### Post by SuperGeorge on 2015-11-29
problem solved. i was running squidguard 1.2,  i upgraded to 1.4 and it works now.  Thanx. feel free to delte post mod

---

### Post by ajgreeny on 2015-11-29
I am happy you figured it out.

Please mark as SOLVED from the Thread Tools menu at the top.

---

