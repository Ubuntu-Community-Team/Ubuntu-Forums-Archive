---
title: "Upgrade Error"
date: 2007-04-13
forum: General Help
---

### Post by MZaza on 2007-04-13
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb)
  403 Forbidden [IP: 91.189.89.8 80]

I get this error while trying to upgrade, any ideas?

---

### Post by acormack on 2007-04-14
Its not just you that is being forbidden.  I get the same thing:

akc@akcxps:/tmp$ wget [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb)
--18:20:46--  [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb)
           => `linux-image-2.6.20-14-generic_2.6.20-14.23_i386.deb'
Resolving archive.ubuntu.com... 91.189.88.31, 91.189.89.6, 91.189.89.8
Connecting to archive.ubuntu.com|91.189.88.31|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
18:20:46 ERROR 403: Forbidden.

---

