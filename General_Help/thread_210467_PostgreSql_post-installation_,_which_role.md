---
title: "PostgreSql post-installation , which role ??"
date: 2006-07-06
forum: General Help
---

### Post by quedigg on 2006-07-06
Hello fellows,
I've installed postgreSql ,from synaptic, however, after installation ,i didn't manage to know which role(user) is installed ?neither root nor my user account was defined as a "role".

on Mysql, there was a debian generated file , where credentials are located ,
What about Postgre ??


regards,
QueDigg

---

### Post by amerigo5 on 2006-07-09
You should have postgres role/account.  Try the commands below:

#sudo su postgres
#psql

---

