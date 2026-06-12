---
title: "Proftpd port"
date: 2007-02-02
forum: General Help
---

### Post by ew16301 on 2007-02-02
Im running proftpd with MYSql. When I try to connect to the server, it connects, but gives error 421. From looking at the log proftpd.mysql it show that it is defaulting to the PostgreSQL port 5234 or something. The problem is MySql is on port 3306. Is there a way to change proftpd from defaulting to PostgreSQL and make it connect to the SQL server on port 3306? Thanks in advance

*****EDIT*****

Seems I got it working. The only solution I could find was to comment out the PostgreSQL in /etc/proftpd/modules.conf

---

