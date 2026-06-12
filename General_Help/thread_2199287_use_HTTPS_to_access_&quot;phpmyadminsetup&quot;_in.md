---
title: "use HTTPS to access &quot;phpmyadmin/setup&quot; in ubuntu"
date: 2014-01-13
forum: General Help
---

### Post by pedenski on 2014-01-13
Im using my ubuntu server as a webserver and my company regularly hires a 3rd party vendor to diagnose/scan our servers for vulnerabilities.

Their recommendation is to "*Use Basic Authentication over an HTTPS connection*" for accessing **[http://ip/phpmyadmin/setup](http://ip/phpmyadmin/setup)** apparently, i was not aware that there are such links aside from (**[http://ip/phpmyadmin](http://ip/phpmyadmin)**)


ive read somewhere that i can force HTTPS using .htaccess using snippet below

```
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}

```

locating .htaccess shows 3 results related to phpmyadmin, which are:
```
/usr/share/phpmyadmin/libraries/.htaccess
/usr/share/phpmyadmin/setup/frames/.htaccess
/usr/share/phpmyadmin/setup/lib/.htaccess

```

Ive tried adding the snippet inside /usr/share/phpmyadmin/setup/lib/.htaccess then restarted apache. but im still able to access it over http.

anyone knows how to properly use HTTPS over phpmyadmin access?

---

### Post by dargaud2 on 2014-01-13
You mean you have phpmyadmin in /var/www and would like to access is both over http and https, with a rewrite rule so that http is changed to https ?

It might be better to move the phpmyadmin directory outside of the default apache directory and configure it manually in /etc/apache2/sites-available/default-ssl.conf

---

### Post by pedenski on 2014-01-13
hi thanks for the reply. i dont have phpmyadmin in /var/www/. 

mostly on **/usr/share/phpmyadmin**, **/var/lib/phpmyadmin**, **/etc/phpmyadmin**

what specific phpmyadmin directory should i move? there seems to be many directories where it resides.

---

