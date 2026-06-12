---
title: "symbolic links have default permission 777 which cannot be changed -- is this normal?"
date: 2016-11-16
forum: General Help
---

### Post by stupidquestion on 2016-11-16
When I do:

sudo ln -s /tmp/target /tmp/link



The resultant symbolic link "link" has permission 777 and owned by root:root. 
I cannot use sudo chmod to change this permission -- is this normal?

---

### Post by kpatz on 2016-11-16
Symbolic links always have 777 permissions.  Effective permissions are the permissions of the file or directory that the link points to.  If you try to chmod a symlink, you'll change the permissions on whatever the link is pointing to.

The link you created is owned by root because you used sudo when creating it.  A symlink's owner can be changed using chown -h .

---

