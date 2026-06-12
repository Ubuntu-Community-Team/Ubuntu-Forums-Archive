---
title: "Citrix Receiver is not working"
date: 2020-04-27
forum: General Help
---

### Post by mouahed-elnahali on 2020-04-27
I tried many videos or user guide, nothing is working for Citrix receiver and I really need it for my work while I was working. It's a must have for me on my new computer build. As without I must stick to Windows.

---

### Post by ebuck on 2020-04-28
> **mouahed-elnahali said:**
> I tried many videos or user guide, nothing is working for Citrix receiver and I really need it for my work while I was working. It's a must have for me on my new computer build. As without I must stick to Windows.

After you install citrix receiver create the symlink as below . Try that. 

root@GamingPC:/opt/Citrix/ICAClient/keystore# ls -la
total 32
drwxr-xr-x  4 root root  4096 Jan 26 23:17 .
drwxr-xr-x 15 root root  4096 Jan 26 23:15 ..
**lrwxrwxrwx  1 root root    14 Jan 26 23:17 cacerts -> /etc/ssl/certs**
drwxr-xr-x  2 root root 20480 Jan 26 23:16 cacerts.bk
drwxr-xr-x  2 root root  4096 Jan 26 23:15 intcerts

---

