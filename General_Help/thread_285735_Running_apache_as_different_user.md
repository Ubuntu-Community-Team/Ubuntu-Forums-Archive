---
title: "Running apache as different user"
date: 2006-10-27
forum: General Help
---

### Post by cronholio on 2006-10-27
By default, Apache runs as user www-data (configured in /etc/apache2/apache2.conf). Is there a way to change the user based on the directory, so that when executing PHP in /var/www/foo, it runs under www-data, while everything in /var/www/bar runs under a different username? Do I need to setup something like virtual hosts or is there some way to define it in a .htaccess file?

---

