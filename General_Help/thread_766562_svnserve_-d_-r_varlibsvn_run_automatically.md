---
title: "svnserve -d -r /var/lib/svn run automatically"
date: 2008-04-25
forum: General Help
---

### Post by mitjab on 2008-04-25
I must manually add svnserve -d -r /var/lib/svn after each restart. How to make this automatically after each restart?

regards

---

### Post by ryanhaigh on 2008-04-27
Add it to /etc/rc.local and make that file executable as mentioned in the file.

---

