---
title: "storage media folders are empty"
date: 2007-10-06
forum: General Help
---

### Post by figo2476 on 2007-10-06
After install wine and ntfs-3g, my kde feisty works fine. But one day after, all folders in the
'storage media' are empty. 

try:
groups hal -- no such user

sudo adduser hal plugdev -- no such user

I find that the   /etc/default/hal
-- DAEMON_OPTS= 
(nothing only this 'DAEMON_OPTS= ')

any hint

---

### Post by figo2476 on 2007-10-06
The fix:
Since my system is dual boot with xp and kubuntu, I 'sudo mount -a'. It informs that I need to do 
a clear shut down in xp.

After that the liinux system is back to normal.

---

