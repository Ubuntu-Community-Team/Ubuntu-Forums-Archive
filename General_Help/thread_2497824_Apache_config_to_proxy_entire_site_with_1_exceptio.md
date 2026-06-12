---
title: "Apache config to proxy entire site with 1 exception"
date: 2024-05-19
forum: General Help
---

### Post by john163 on 2024-05-19
I have a website [www.example.com]("http://www.example.com")  on a hosting provider.  We use that provider because it has a simple  site builder my wife uses to maintain the site.  Moving off of it isn't  an option for this exercise.

 I want to create an Apache proxy that can accept traffic for [www.example.com]("http://www.example.com")  that will simple pass all requests along to that hosted site, which is a  vhost so hostname must be retained.  I want to do this so I can use  that proxy to add TLS (the hosting provider won't let us without  charging triple - yes, they suck, but again, leaving isn't an option).   And in order to create a Let's Encrypt cert for the site, I need the  acme challenge process to find a specific file with specific content,  but I cannot upload to the site itself (again, yes, they suck, no, we  can't leave)  So I did a RewriteRule that catches that request and  redirects it to a file on my web server, but it displays as [http://my-server.com/blah](http://my-server.com/blah) instead of [URL="http://www.example.com/path/to/file"]http://www.example.com/path/to/file
[/URL]
 What I've got so far:

 ```
<VirtualHost *:80>
    ServerName [www.example.com]("http://www.example.com")
    ServerAlias exxample.com
    RequestHeader set Host "www.example.com"
    ProxyPreserveHost on
    ProxyPass / [http://192.168.193.133](http://192.168.193.133) # IP of providers vhost
    ProxyPassreverse / [http://192.168.193.133](http://192.168.193.133)
    RewriteEngine On
    RewriteRule /path/to/file [http://my-server.com/ssp-acme-challenge](http://my-server.com/ssp-acme-challenge)
</VirtualHost>
```

 I need to get this working with HTTP only first so I can solve the  challenge file issue.  Then I want to fix to force all traffic to https  and create a vhost for :443

---

### Post by currentshaft on 2024-05-19
:80

---

### Post by john163 on 2024-05-19
> **currentshaft said:**
> For the first part, perhaps this would work:

ProxyPass / [http://www.example.com:80/](http://www.example.com:80/)
ProxyPassReverse / [http://www.example.com:80/](http://www.example.com:80/)

Problem is, [www.example.com](www.example.com) needs to resolve to the IP of the host my apache2 is running on.  I need to direct traffic to the IP of the hosting server but include a header that says "www.example.com" because it's a vhost and will barf on just the IP.

> For ACME, have you thought about using a DNS-based challenge instead?

No!  certbot was just prompting me for the web chalenge.  I'll look at how to force a DNS challenge. 

Great thought, thank you!

---

