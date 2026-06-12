---
title: "PhP Script gets downloaded"
date: 2007-03-06
forum: General Help
---

### Post by jeisma on 2007-03-06
hi!

i want to run apache/mysql/php on my xubuntu 6.10 desktop, however, im stumped with this problem that i have not encounterd to other ubuntu editions/versions.

when i try to [http://localhost/test.php](http://localhost/test.php), the browser (ff) instead prompts to download the script.

/etc/apache2/apache2.conf file has this:

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

i tried to add this:

Include /etc/apache2/mods-available/php4.load 
Include /etc/apache2/mods-available/php4.conf

also tried *.load and *.conf

but the browser prompts to download any php script.


any ideas how to work this out?


thanks!


joey

xubuntu 6.10
apache2
php4

---

### Post by nickweb on 2007-03-06
have u tried creating a .htaccess in the root directory saying php files are php files?

i.e

add only ONE of the 2 lines below..

```
AddType x-mapp-php5 .php
AddHandler application/x-httpd-php5 .php
```

---

