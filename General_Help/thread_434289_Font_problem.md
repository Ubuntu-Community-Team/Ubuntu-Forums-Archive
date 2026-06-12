---
title: "Font problem"
date: 2007-05-05
forum: General Help
---

### Post by Buster222 on 2007-05-05
I have Apache2 and php5 running on KUbuntu 7.04. Everything works fine, but scandinavian characters are displyed as small square boxes in the browser. It is the same in all browsers, booth on Linux and Windows. Scandinavian characters displays fine in Quanta, OpenOffice, etc. Also, external webpages diplays just fine. so it must be something to do with Apache2.  By the way, I do have the line
AddCharset UTF-8 .utf8
enabled in /etc/apache2/apache2.conf
Any ideas?

---

### Post by Buster222 on 2007-05-06
For the benefit of others: it turned out that I In the file /etc/php5/apache2/php.ini had to comment out the line 
default_charset = "text/html" 
and uncomment the line 
default_charset = "iso-8859-1"

---

