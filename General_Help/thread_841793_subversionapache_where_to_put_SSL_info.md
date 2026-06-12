---
title: "subversion/apache where to put SSL info?"
date: 2008-06-26
forum: General Help
---

### Post by KingTermite on 2008-06-26
I'm trying to set up a subversion server at work using Ubuntu (7.10).

I've finally got a basic server working, no authentication over webdav. Now I want to add SSL security.

I'm a little confused by different things I see at different websites.

Put SSL info where?

dav_svn.conf file like this site shows:
[http://alephzarro.com/blog/2007/01/07/installation-of-subversion-on-ubuntu-with-apache-ssl-and-basicauth/](http://alephzarro.com/blog/2007/01/07/installation-of-subversion-on-ubuntu-with-apache-ssl-and-basicauth/)

Apache vhost file like this site shows?
[http://www.netmojo.ca/blog/2007/05/03/subversion-webdav-osx/](http://www.netmojo.ca/blog/2007/05/03/subversion-webdav-osx/)

httpd.conf file like this site shows?
[http://ist.uwaterloo.ca/security/lib-proxy/howto/ssleay/](http://ist.uwaterloo.ca/security/lib-proxy/howto/ssleay/)

I'm confused about how to go about doing the SSL certificate.

---

### Post by datajelly on 2008-09-05
I could be wrong, but I think httpd.conf is for use in Windows?

In any case, I would recommend placing it inside your virtual host. This is how we've set it up and it's been working well. (Well, we aren't running Subversion through Apache, but we do have SSL running on Apache.)

[http://blog.datajelly.com/2007/12/using-apache-for-ssl-offloading-and.html]("http://blog.datajelly.com/2007/12/using-apache-for-ssl-offloading-and.html")

---

### Post by datajelly on 2008-09-05
My apologies, I do see an httpd.conf file in Ubuntu but for me it is empty. Instead, my SSL information is placed under a virtual host inside the file sites-enabled/000-default.

---

