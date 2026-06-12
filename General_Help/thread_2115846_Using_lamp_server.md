---
title: "Using lamp server"
date: 2013-02-14
forum: General Help
---

### Post by sharatsn123 on 2013-02-14
I am unable to create files in var/www
I think thats where apache searches for files to display..
Pls help..

---

### Post by tydfil on 2013-02-14
You can create a symlink. Make a directory called public_html in your home directory. Open a terminal and type.

sudo ln -s /home/USER/public_html /var/www  replace USER with your user name.

public_html now appears to be in the www folder and is available to Apache, but is in reality in your user space and accessible to you there.


In your browser localhost/public_html to see your website or localhost/public_html/FILENAME.

---

### Post by sharatsn123 on 2013-02-17
thanks tydfil

---

