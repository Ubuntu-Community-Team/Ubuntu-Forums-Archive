---
title: "PHP problem"
date: 2005-08-06
forum: General Help
---

### Post by jrohde on 2005-08-06
Hi,

I've just installed my laptop with Ubuntu, and now I'm trying to install Typo3 using Apache2, MySQL and PHP4.

The test file showing phpinfo works fine, but when I try to access the Typo3 install tool, Firefox tries to download the index.php file rather than executing it. In apache2.conf the DirectoryIndex also mentions index.php, so what am I missing?

TIA,

Jakob

---

### Post by C38a7r1zvl on 2005-08-06
AddType application/x-httpd-php .php
should be sufficient  :???:

---

