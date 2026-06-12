---
title: "Server/domain help"
date: 2007-06-13
forum: General Help
---

### Post by Thirtysixway on 2007-06-13
I'm trying to make it so I can setup more than one website with ubuntu.

I have it right now where you go to my ip and it has a site under /var/www but i need it so i can add domains like example.com and example2.com and have them be different. I already have the domains.

I'm new to setting up things like this, so if anyone can help me it would be great. do i have to install something like dns software?


I got subdomains working from a tutorial, but i don't know how to do .com domains.
help please?


I have apache2, php5, mysql, and phpmyadmin installed.

---

### Post by toomij on 2007-06-13
If you can resolve your domains .com 

# nslookup example.com

then you just need configure your apache works like "Named Based Virtual Host" [http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

if you don't can to resolve your domains, well you need setup your DNS server.

---

