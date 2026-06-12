---
title: "making php in linux....hassle"
date: 2005-08-10
forum: General Help
---

### Post by tanix on 2005-08-10
I just installed apache, php, mysql onto my computer(running ubuntu only) and for anyone familiar with programming/html/apache...etc i have this question for you.

when i make a .php doc in gedit and try to save it to my /opt/lammp/htdocs folder it wont let me...it seems like i have to be logged in as root to save a doc in this location...is there anyway to get around this since it is a hassle.

any questions on what i mean please let me know.

---

### Post by tanix on 2005-08-10
can anyone help me or was my post too unclear

---

### Post by Aksu on 2005-08-10
The default folder for Apache document-root is admin-only, so what I did was, that I changed the deafult root-folder to point to my homedirectory instead of /var/www

You can change that in apache config-file, that you will find inside Apache-folder.

---

