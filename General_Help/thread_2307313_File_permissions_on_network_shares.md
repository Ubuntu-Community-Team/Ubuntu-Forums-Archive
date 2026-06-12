---
title: "File permissions on network shares"
date: 2015-12-23
forum: General Help
---

### Post by petegregar on 2015-12-23
I have some older files and network shares created from other PC's

Can I select an entire directory and reset the owner?
To my current owner on the Ubuntu machine?

---

### Post by TheFu on 2015-12-24
NFS, CIFS, or some other shares?
NFS, probably yes. Clients control the permissions.
CIFS/samba, probably no. Server controls the permissions.

---

