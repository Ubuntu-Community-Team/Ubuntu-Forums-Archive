---
title: "apache hide .php through .htaccess"
date: 2018-06-27
forum: General Help
---

### Post by daemoncesar on 2018-06-27
I am using the following code and working


```
RewriteEngine on
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME}\.php -f
RewriteRule ^(.*)$ $1.php
RewriteCond %{THE_REQUEST} ^[A-Z]{3,9}\ /(.*)\.php
RewriteRule ^ /%1 [L,R=301]



```



If the visitor types [www.mysite.com/teste]("http://www.mysite.com/teste") it works



But if he type [www.mysite.com/test/]("http://www.mysite.com/test/") back error

[HTML]Internal Server ErrorThe server encountered an internal error or misconfiguration and was unable to complete your request.
Please contact the server administrator at [no address given] to inform them of the time this error occurred, and the actions you performed just before this error.
More information about this error may be available in the server error log.[/HTML]

---

