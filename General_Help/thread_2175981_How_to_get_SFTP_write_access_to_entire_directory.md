---
title: "How to get SFTP write access to entire directory"
date: 2013-09-22
forum: General Help
---

### Post by linfan on 2013-09-22
I made a new group and user and added the user to have RW permissions in /var/www/ but I cannot upload or make changes in its subdirectories so I have to add access to each directory so:

chown -R :ftpuser /var/www/cms/ 
chmod -R g+rw /var/www/cms/

I'd rather be able to control the entire /www with my user ftp and its group ftpuser.

---

### Post by Lars Noodén on 2013-09-22
Do you mean that new directories aren't getting the right permissions?  That should be fixable by setting the SetGUID bit.

```

sudo chgrp -R sftpusers /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

```

---

