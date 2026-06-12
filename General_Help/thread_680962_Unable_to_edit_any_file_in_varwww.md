---
title: "Unable to edit any file in /var/www"
date: 2008-01-28
forum: General Help
---

### Post by mesh2005 on 2008-01-28
I can't create or edit or delete any file in /var/www, it is owned by www-data:
ls -ld /var/www/
drwxrwxr-x 4 www-data www-data 4096 2008-01-28 21:06 /var/www/

I added my username to the group www-data:
groups user1
user1 : user1 adm dialout cdrom floppy audio dip www-data video plugdev scanner netdev lpadmin powerdev admin

The directory /var/www/ has permissions 775, what is wrong? why I can't write?

Thank you

---

### Post by djrobthaman on 2008-01-28
If it's permissions that is the problem, you can type "alt+f2" and run "gksudo nautilus".  This will allow you to use nautilus as root (which means you're viewing all your files as root) and then you can change the permissions from there.

---

### Post by cdenley on 2008-01-28
I'm guessing the files you are trying to edit are not owned by www-data. I think this is a bad idea for security. Why not make you the owner, then allow www-data to read?

```

sudo chown -R user1 /var/www
sudo chgrp -R www-data /var/www
sudo chmod -R 750 /var/www

```

---

