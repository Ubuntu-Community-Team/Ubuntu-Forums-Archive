---
title: "Font encoding on Apache"
date: 2007-01-23
forum: General Help
---

### Post by Nonno Bassotto on 2007-01-23
I'm trying to learn PHP, so I made a standard installation of Apache+PHP. The problem is: when I visualize my web pages (no PHP yet) via Apache, some fonts with accents are not properly visualized, while they worked fine when I opened the page directly with Firefox.

It seems that it is a font encoding problem, since if I save tha page with UTF-8 encoding it works well. But in my pages the encoding is properly declared with
[HTML]
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
[/HTML]

Why is Apache assuming I'm using such an encoding? Can I change this behaviour?

---

### Post by matthewstory on 2007-01-24
this may have nothing to do with it . . . but you should make sure that you are using the mpm-prefork version of apache2 with php . . . the worker mdm doesn't work too well with PHP5, just a heads up.  In addition to this check your /etc/apache2/apache2.conf file and make sure you've got this line:

AddCharset UTF-8       .utf8

it should be in with a bunch of other addcharset directives . . . you may want to use this directive:

AddDefaultCharset UTF-8

good luck

---

