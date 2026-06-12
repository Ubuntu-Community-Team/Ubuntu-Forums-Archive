---
title: "Cannot change permissions"
date: 2008-02-28
forum: General Help
---

### Post by zumbi77 on 2008-02-28
I cannot figure out how to change the permissions to my second harddisk. I figured out how to mount it automatically, but now all my files are writeprotected. I would like to have the same rights as on my first harddisk. 

How do I change this?

---

### Post by can8dnSix on 2008-02-28
on the mount side
# sudo chmod 777 /mount/d_drive or whatever it is called.
 to open all permissions.

BUT, you also have to do this on the /dev/hd**

** represents the drive hdb1? or whatever it is,.
#sudo chmod 777 /dev/hd**

That should do you right.

---

### Post by zumbi77 on 2008-02-28
Thank you. Made my day.

---

