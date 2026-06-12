---
title: "Configuration capacity for SAMBA"
date: 2017-03-06
forum: General Help
---

### Post by maetoo on 2017-03-06
Hello.
I installed samba packages.
I created linux users and samba users.
How do I configuration example for first user only 50Gb free capacity for data and for second user 30Gb free capacity for data?

---

### Post by brucehohl on 2017-03-06
You need these additional packages: quota quotatool

Check out these links:
[http://superuser.com/questions/123930/how-can-i-use-quotas-in-samba](http://superuser.com/questions/123930/how-can-i-use-quotas-in-samba)
[http://computingtech.blogspot.com/2008/09/ubuntu-linux-disk-quotas.html](http://computingtech.blogspot.com/2008/09/ubuntu-linux-disk-quotas.html)

---

### Post by HermanAB on 2017-03-06
Samba is a network file system.  It doesn't actually do user quotas.

User quotas are handled by the underlying system called, wait for it, drum roll... quota.

---

