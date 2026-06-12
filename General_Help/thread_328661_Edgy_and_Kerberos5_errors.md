---
title: "Edgy and Kerberos5 errors"
date: 2006-12-31
forum: General Help
---

### Post by jmoschetti45 on 2006-12-31
I just got all the required packages via apt-get, and then edited the configs (double checked that), and get this:

root@Stephanie:/etc/init.d# ./krb5-admin-server restart
Restarting Kerberos Administration Servers: kadmindkadmind: Syntax error in profile relation while initializing, aborting
.
root@Stephanie:/etc/init.d# kdb5_util create -s
Syntax error in profile relation while retreiving configuration parameters

Ideas?

---

### Post by garba on 2007-03-18
i'm having the same problem, did a search on  google but that didn't turn up anything good

---

