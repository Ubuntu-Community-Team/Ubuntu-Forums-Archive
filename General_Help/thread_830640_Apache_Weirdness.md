---
title: "Apache Weirdness"
date: 2008-06-16
forum: General Help
---

### Post by rockstarrem on 2008-06-16
Hello,

I'm having an error here, whenever I browse for a PHP file in my apache directory in a browser it asks me if I want to open it with Windows, I'm not sure how to fix this. Here's a screenshot: [http://ubuntuforums.org/attachment.php?attachmentid=74202&stc=1&d=1213596344](http://ubuntuforums.org/attachment.php?attachmentid=74202&stc=1&d=1213596344)

Please help me, I just want to run a LAMP server :(.

EDIT: I am sorry but I just made a stupid mistake. I just restarted the server :P.

---

### Post by NikoC on 2008-06-16
Did you install php?

---

### Post by fragos on 2008-06-16
Assuming you install the LAMP package you have Apache2, PHP and MySQL. You do however have to tell apache to use PHP. In /etc/apache2 there is an empty file httpd.conf. Place the following lines in that file and you should be OK.

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

---

