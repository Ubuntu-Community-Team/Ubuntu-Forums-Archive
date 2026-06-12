---
title: "Enable SSI"
date: 2005-06-28
forum: General Help
---

### Post by dfghost on 2005-06-28
How does one go about enabling SSI for Apache2?  I've already tried this in httpd.conf

<Directory "/var/www">
Options +Includes
AddType text/html .html
AddOutputFilter INCLUDES .html
AddHandler server-parsed .html

and that doesn't work.  I also tried adding: LoadModule includes_module /usr/lib/apache2/modules/mod_include.so

And that cause Apache2 to crash, so, what do i do?

Thanks in advance

---

