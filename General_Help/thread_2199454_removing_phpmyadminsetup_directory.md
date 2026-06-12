---
title: "removing /phpmyadmin/setup directory"
date: 2014-01-14
forum: General Help
---

### Post by pedenski on 2014-01-14
hi, im having issues with my web server, a 3rd party scanning application program detects that my /phpmyadmin/setup should use basic authentication over HTTPS when accessing the page. 

its too troublesome to do all the configurations, creating .htaccess, allowing SSL and some others..

since this directory is the only one being detected as a possible vulnerability, can i just remove the directory so it'd would solve the problem?

going to the http://<ip>/phpmyadmin/setup contains some configuration that i usually dont care much about. 

what are the probable implication if i remove this directory?

---

### Post by 101ravikant on 2014-01-14
In order if you remove the directory than your database might got tamperd and all configuration with your website to your database become invalid however you may try an attribution in case if you wana try with it.



[COLOR=#d3d3d3]________________________________________________________________________________________________________________________________________[/COLOR]
**How to [Free Recover Your Linux OS]("http://www.windows8downloads.com/win8-free-recover-linux-data-ndxnnwqk/") in three steps ?**

---

### Post by Habitual on 2014-01-14
create an /phpmyadmin/setup/.htaccess file and include:
```
<IfModule mod_rewrite.c>
RewriteEngine On
order deny,allow
deny from all
allow from ip1
</Files>
```
where ip1 is your IP. You can have as many as necessary "allow from"s as you need.
See [http://corz.org/server/tricks/htaccess.php?page=all](http://corz.org/server/tricks/htaccess.php?page=all)

---

