---
title: "file permissions when uploading to server"
date: 2007-08-22
forum: General Help
---

### Post by het.idee on 2007-08-22
I have a debian webserver at work. I use windows with winscp at the moment to upload everything I need, and all the permissions are correct.
However, I want to switch to Ubuntu on my work-laptop. When I try to upload files with FTP or SSH, Ihave to chgrp them before they can be used by the webserver. 

Is there a way to upload my files without having to change permissions on the server?

---

### Post by pmg on 2007-08-22
If you chgrp the directory into which you load the files to the right group, and then set to sgid bit:
**chmod g+rwxs *dirname***
then any file written into that directory will inherit the group owner from the directory.

---

### Post by now-or-never on 2007-08-23
I dont think there is a possibility without a prompt ...
You need to have prmission for access to server...

---

### Post by HermanAB on 2007-08-23
You have to change the settings of the FTP server so that it will force the owner and group to a preset value.  The permissions can be set using the sticky bit on the upload directory as mentioned above.

Cheers,

H.

---

