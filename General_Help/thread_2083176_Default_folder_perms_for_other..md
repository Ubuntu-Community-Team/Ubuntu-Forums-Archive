---
title: "Default folder perms for other."
date: 2012-11-11
forum: General Help
---

### Post by ioannisp on 2012-11-11
Hello. Can anyone help me out here?

I want to make a folder that everyone has rwxs permissions for this folder and every new file and folder created inside.

I also need the default perms for all new created files and folders to be 777.

Is this possible? I am very new to linux so please explain what you will suggest in the simplest way.

Thank you all.

---

### Post by papibe on 2012-11-11
Hi ioannisp.

Is this a network drive (like a samba share or a nfs export), or a local folder shared by several local users?

Regards.

---

### Post by Vaphell on 2012-11-11
> I also need the default perms for all new created **files** and folders to be **777**.

no, unless you want every single file to be executable.

---

### Post by ioannisp on 2012-11-12
It's a folder in var directory that is used as home for apache. I don't mind every file to be executable. I just have problems with php. When creating files with php file manager i can not change perms and delete them. In fact what i need is www-data user to have full perms in that folder and every new folder and file inside the root folder.

I don't know if you understood what i told...:popcorn:

---

### Post by Wim Sturkenboom on 2012-11-12
Your problem does not make sense (to me). In general, if a user is able to create files in the directory /var/www, that user should also be able to delete the files that he/she created. So are you talking about one user that creates files and another user that needs to be able to delete them?

> 
In fact what i need is www-data user to have full perms in that folder and every new folder and file inside the root folder.

Have you considered
```

chgrp www-data /var/www
chmod 775 /var/www

```
That should allow users in the group www-data to do what you want. An alternative can be setfacl which allows more fine-grained control without changing the original permissions.

---

### Post by ioannisp on 2012-11-12
Let me explain better. I have a folder that is the root folder for my domain name. I use php file manager and not ftp to manage my files. When i create a file or a folder i can read and write to that new file but i can not change perms or delete it.

Thank you

---

### Post by raja.genupula on 2012-11-12
This guide can help you
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

