---
title: "Where's the Apache manual?"
date: 2005-07-01
forum: General Help
---

### Post by jnoreiko on 2005-07-01
I've just installed apache and apache-doc with apt-get.

[http://localhost/](http://localhost/) shows me a directory listing with one entry, apache2-default/ 
Following that gets me to the Apache test page. Clicking on the link for the documentation in that page takes me to [http://localhost/manual/](http://localhost/manual/) ... which is a 404 :(

Is this an ubuntu or a gnome bug? And where are the docs?

---

### Post by Lunde on 2005-07-01
[QUOTE=jnoreiko]I've just installed apache and apache-doc with apt-get.

[http://localhost/](http://localhost/) shows me a directory listing with one entry, apache2-default/ 
Following that gets me to the Apache test page. Clicking on the link for the documentation in that page takes me to [http://localhost/manual/](http://localhost/manual/) ... which is a 404 :(

Is this an ubuntu or a gnome bug? And where are the docs?[/QUOTE]
 Just download it from [www.apache.org](www.apache.org) and save it in /manual/

---

### Post by Lunde on 2005-07-01
[QUOTE=Lunde]Just download it from [www.apache.org](www.apache.org) and save it in /manual/[/QUOTE]
 Sorry... 
$ sudo apt-get install apache2-doc

I think this installs it in the correct directory. If not, just

$ sudo ln -s /path to doc /var/www/where you want the manual

---

