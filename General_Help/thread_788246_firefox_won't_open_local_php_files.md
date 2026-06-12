---
title: "firefox won't open local php files"
date: 2008-05-09
forum: General Help
---

### Post by evanct on 2008-05-09
this is ff 3 beta 5, but i tried it with ff 2 and the same thing happened. and it's ubuntu 8.04.

a firefox window pops up and i get a prompt asking me if i want to open with... the php file or save it. if i choose to open it with firefox, nothing happens.

i have php5 installed. php files work with all other browsers(edit: galeon doesnt work either). anyone know what to do?

---

### Post by ibuclaw on 2008-05-09
Rename the files from **foo.php** to **foo.php.html**.

I just tried this and that seemed to work for me.
PHP files were opening in gedit, whereas with the  "html" suffix added, it had them opened in firefox, no noticeable problems.

Regards
Iain

---

### Post by rickh57 on 2008-05-09
In order for locally stored php files to open in a browser, a web server must be running and it must be configured to treat the php files as programs to run, rather than just text files. In Ubuntu, it is easy to install apache/php/mysql.

---

