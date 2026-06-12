---
title: "What is diffrence between mods"
date: 2020-06-25
forum: General Help
---

### Post by Hotchilli on 2020-06-25
I am about to install a python package written in 2012 in apache2 which requires mod-python but since mod-python is outdated now then it has been suggested to install mod-wsgi
What is the main diffrence between these two packages?

---

### Post by dino99 on 2020-06-25
libapache2-mod-wsgi

The mod_wsgi adapter is an Apache module that provides a WSGI (Web Server Gateway Interface, a standard interface between web server software and
web applications written in Python) compliant interface for hosting Python based web applications within Apache. The adapter provides significantly
better performance than using existing WSGI adapters for mod_python or CGI.

This package provides module for Python 2.X.

---

### Post by Hotchilli on 2020-06-25
Thankyou 
The python package written in 2012 does just that in fact it provides a email interface and the old but still used sometimes interface for usenet.
The package can be found here
pyanon.sourceforge.net

---

