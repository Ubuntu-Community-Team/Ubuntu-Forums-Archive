---
title: "Apache/1.3.34 (Ubuntu) &amp; mod rewrite"
date: 2007-05-13
forum: General Help
---

### Post by JettRink on 2007-05-13
I am trying to get mod rewrite working with the binary install of apache 1.3.34.

When I try to rewrite a page I get the following error in error_log:

attempt to make remote request from mod_rewrite without proxy enabled: proxy:

Browser returns the following error:
403 forbidden - You don't have permission to access /reservations.html on this server.

---

### Post by JettRink on 2007-05-14
well I just figured it out myself that you manually need to edit the modules.conf  in /etc/apache to load the proxy module as follows: 

LoadModule proxy_module /usr/lib/apache/1.3/libproxy.so

this is a BIG oversite on Ubuntu's part since mod_rewrite requires mod_proxy it should also be configured correctly in the default install of Apache when mod_rewrite is installed.

---

