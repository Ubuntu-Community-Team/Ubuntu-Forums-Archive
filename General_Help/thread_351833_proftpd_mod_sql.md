---
title: "proftpd mod_sql"
date: 2007-02-02
forum: General Help
---

### Post by ew16301 on 2007-02-02
Im trying to get protftpd working with SQl. When I restart the server, it gives me "Unkown directive SQLLogFile", which I disocvered is because I didnt compile proftpd with the module. Is there any way to add in that module without reinstalling proftpd. I tried editing modules.conf, adding in mod_sql.c, but it didnt work...not sure if it should. Thanks in advance.

---

### Post by ew16301 on 2007-02-02
*****EDIT******

Fixed it. Its seems "Include /etc/proftpd/modules.conf" was not in my proftpd.conf.

---

