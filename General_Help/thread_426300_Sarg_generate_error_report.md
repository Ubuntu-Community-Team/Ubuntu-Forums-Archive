---
title: "Sarg generate error report"
date: 2007-04-28
forum: General Help
---

### Post by hartunnoo on 2007-04-28
**Now generating Sarg report from Squid log file /var/log/squid/access.log and all rotated versions ..**
 
sarg -l /var/log/squid/access.log.1 
SARG: (html11) Cannot open file: /var/www/squid-reports/2007Apr27-2007Apr28/users**.. **
 
**Sarg failed! See the output above for details.**
 
**I dont know why this error occur when I try to generate a report.**

---

### Post by revertex on 2007-05-02
does /var/www/squid-reports/ exists?

the user that is issuing this command have enough permissions to read squid log and generate the report?

---

### Post by expatCM on 2007-12-21
I see this same error as well.

The user / group permissions of /var/www/squid-reports/ are root / root.

The user is not root but the logged in user.

Where to change these permissions?

---

