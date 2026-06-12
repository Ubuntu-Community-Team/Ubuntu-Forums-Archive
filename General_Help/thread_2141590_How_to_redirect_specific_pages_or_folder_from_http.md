---
title: "How to redirect specific pages or folder from http to https"
date: 2013-05-03
forum: General Help
---

### Post by varuvictory on 2013-05-03
Hello All,

I want to redirect specific pages or folder from http to https not whole site..

I am using ubuntu 12.04LTS... please explain me.

I am using .htaccess file for support the apache2.

---

### Post by SlugSlug on 2013-05-03
[http://www.htaccessredirect.net/](http://www.htaccessredirect.net/)

---

### Post by Lars Noodén on 2013-05-03
Welcome to the forums.

If you have access to Apache2's configuration files in /etc/apache2/sites-enabled/ then you don't have to mess with .htaccess.  The file .htaccess is used only in occasions you aren't able to change the configuration file directly.  When you change the configuration file, you have the advantage that all the changes are in the same place.

That said, the way to change the configuration file is to use the module [rewrite](https://httpd.apache.org/docs/2.2/rewrite/).  First turn on the module if it is not already on.

```

sudo a2enmod rewrite
sudo service apache2 restart

```

Then you can make your changes to your configuration file.  The changes go in between the <VirtualHost> tags to apply to the whole site, or between <Directory> tags to apply to a certain directory.

```

RewriteEngine on
Redirect /old.html /new.html

```

---

