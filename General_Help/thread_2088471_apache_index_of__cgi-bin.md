---
title: "apache index of / cgi-bin/"
date: 2012-11-26
forum: General Help
---

### Post by LuniTux on 2012-11-26
Hello,

I have an apache2 server that hosts multiple websites using sites-available/sites-enabled. If I goto myaddress.com, I get the **Index of /** page. I want this page to redirect to [www.myaddress.com](www.myaddress.com). I tried using the method stated on [http://serverfault.com/questions/120488/redirect-url-within-apache-virtualhost]("http://serverfault.com/questions/120488/redirect-url-within-apache-virtualhost") but neither method would work.

Any help would be appreciated.

Thanks,

---

### Post by efflandt on 2012-11-27
Why not simply make either name work?

Within the VirtualHost

ServerName [www.myaddress.com]("http://www.myaddress.com")
ServerAlias myaddress.com

To use mod_rewrite in .htaccess, if **AllowOverride** is not simply **All**, it would have to include **FileInfo**.  Using .htaccess files can also slow down a server vs. putting directives in server configuration.  [http://httpd.apache.org/docs/2.4/mod/core.html#allowoverride](http://httpd.apache.org/docs/2.4/mod/core.html#allowoverride)

This link shows how to use another virtual host to redirect unwanted names without having to use mod_rewrite, or how to use mod-rewrite if you want to: [http://httpd.apache.org/docs/2.4/rewrite/remapping.html#canonicalhost](http://httpd.apache.org/docs/2.4/rewrite/remapping.html#canonicalhost)

---

