---
title: "Executing .php5 files with php 5"
date: 2006-07-03
forum: General Help
---

### Post by caspian on 2006-07-03
I know this is a dumb question, but I can't figure it out.

Apache executes .php files with php 5, but just sends .php5 files to the browser in plain text.

How can I tell Apache to also execute .php5 files with php 5?

Thanks.

---

### Post by mlind on 2006-07-03
[QUOTE=caspian]I know this is a dumb question, but I can't figure it out.

Apache executes .php files with php 5, but just sends .php5 files to the browser in plain text.

How can I tell Apache to also execute .php5 files with php 5?

Thanks.[/QUOTE]

You probably need to add new mime type to /etc/apache2/mods-enabled/php5.conf
(or php5.load)

---

### Post by motionsiren on 2006-07-03
try adding this to your apache's conf:

```

AddType application/x-httpd-php .php5
AddType application/x-httpd-php-source .php5s

<IfModule dir_module>
    DirectoryIndex index.html index.htm index.php **index.php5**
</IfModule>


```

You may also want check your php.ini and make sure the shorttags are turned on, if you're using them.

however... the httpd.conf stuff is scattered about now to make it 'easier'...  O_o just stick it in the httpd.conf
btw, i very much do not like the splut up httpd conf stuff. put it back.

---

### Post by caspian on 2006-07-04
Thanks!

I got it set up. Thanks again for your help :).

---

