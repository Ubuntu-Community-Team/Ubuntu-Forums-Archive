---
title: "error installing apache on edgy"
date: 2006-11-02
forum: General Help
---

### Post by vjoe on 2006-11-02
Hi,

I just installed ubuntu and went through the upgrade process to the latest release.  Then I went to install apache with:

sudo apt-get install apache

I get:
[...]
Setting up apache (1.3.34-2) ...
dpkg: error processing apache (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 apache
E: Sub-process /usr/bin/dpkg returned an error code (1)

any ideas what I'm missing or how I can futher debug this?

---

### Post by hhavel on 2006-11-02
I went installed apache2 with webmin.  ([http://www.webmin.com/download.html](http://www.webmin.com/download.html)) Use the debian package to install webmin.  It was very simple that way.  So many useful things at your fingertips.

---

### Post by ickyb0d on 2006-11-05
vjoe : i actually just installed edgy.  I had the same problem.  however... i just ran "sudo apt-get install apache" again after receiving the error, and everything seemed to install fine.

---

### Post by xphelanx on 2006-11-08
I also ran into this problem and did just as ickyb0d did and it worked just perfectly.

---

