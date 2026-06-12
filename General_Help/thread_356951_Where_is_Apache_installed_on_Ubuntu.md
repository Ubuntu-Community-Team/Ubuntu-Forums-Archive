---
title: "Where is Apache installed on Ubuntu?"
date: 2007-02-09
forum: General Help
---

### Post by sri1025 on 2007-02-09
I can't  find the place where Apache Web Server is installed on Ubuntu.

Thanks,
-- Srikanth

---

### Post by taux on 2007-02-09
Apache config files are in /etc/apache
Apache log files are in /var/log/apache
Apache libs are in /usr/lib/apache
Other files can be in /usr/share/apache, /var/lib/apache

Also you can always use command "locate apache" to get more info where your program files are.

---

