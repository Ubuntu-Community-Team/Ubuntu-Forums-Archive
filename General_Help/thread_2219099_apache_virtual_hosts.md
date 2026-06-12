---
title: "apache virtual hosts"
date: 2014-04-22
forum: General Help
---

### Post by grizdog on 2014-04-22
After praising apache in another thread, now I can't get virtual hosting to work.

I followed the (debian) instructions, and created two files in /etc/apache2/sites-available.  Let's call them one.org and two.com  one.org is my main site - two.com is an afterthought, a favor to a cousin.  As such, the root of one.org is /var/www/html while the root of two.com is /var/www/htm/mjn and that is exactly what appears in the DocumentRoot directives of the two configuration files in the sites-available directory.  I enabled these sites and disabled the default.  But when I point a browser at two.com, I get the index file in /var/www/html, the same thing I get when I look for one.org

The sites-enabled directory has only the two links to one.org and two.com so I don't see how a default file could be screwing things up.
Absolutely nothing shows up in the log files - no errors, it just serves the files.

It doesn't seem like there should be a problem with making the DocumentRoot for two a subdirectory of the DocumentRoot for one, I hope that isn't it.

All this happened after upgrading to 14.04, I am using the apache that came with the distro, I think it is 2.4

Thanks for any help

---

### Post by SeijiSensei on 2014-04-23
Post the configuration files in [noparse]```

```[/noparse] tags please.

---

