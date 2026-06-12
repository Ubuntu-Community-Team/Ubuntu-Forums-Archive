---
title: "NFS folder share with password, is possible?"
date: 2008-07-01
forum: General Help
---

### Post by ruipedroca on 2008-07-01
Hi,

With Samba i know it is possible to share a folder so someone in the LAN can point the file manager to smb://ip-address and login, but what about NFS?
Is it possible? If so, how can I do it?

Regards

---

### Post by ruipedroca on 2008-07-07
Come on, guys! Please give it a try!

---

### Post by chunderbunny on 2008-07-07
No, NFS doesn't really support any kind of security beyond filtering out IP addresses. If you want to use authentication you will need to set up a SAMBA share.

---

### Post by ruipedroca on 2008-07-21
Thanks!

---

