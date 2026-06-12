---
title: "Apache PHP page not shwoing"
date: 2007-09-01
forum: General Help
---

### Post by Yodude on 2007-09-01
I recently se up Apache to serve a page ( bandwidth monitor "cacti" ). I installed PHP and the apache PHP module, restarted Apache, but the page is still not showing, it's being treated as a file to download by firefox, can someone please help me ? :(

---

### Post by jamvegan on 2007-09-01
In /etc/apache2/mods-available/ there should be a file called php5.conf and another called php5.load.  In /etc/apache2/mods-enabled/ there should be links to those files.  Are the files and the links present?

Also, are you accessing the page via a URL (such as [http://localhost/whatever.php](http://localhost/whatever.php)), or are you trying to open it by choosing File->Open File... in Firefox?

---

