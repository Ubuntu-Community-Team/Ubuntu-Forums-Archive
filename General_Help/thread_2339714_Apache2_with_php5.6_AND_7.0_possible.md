---
title: "Apache2 with php5.6 AND 7.0 possible?"
date: 2016-10-12
forum: General Help
---

### Post by ELMIT on 2016-10-12
I have Ubuntu 15:10 with php5.6.11 installed.

A new virtual domain on that server requires php7.0. However, at least one of the existing websites requires php5.6.

Is it possible to run apache2 with both versions of php? So far I only found instructions how to upgrade to php7.0+

---

### Post by dragonfly41 on 2016-10-12
You could try phpfarm ...

[https://dbforch.wordpress.com/2010/05/21/apache2-fastcgi-multiple-php-versions-ubuntulucid-10-04/](https://dbforch.wordpress.com/2010/05/21/apache2-fastcgi-multiple-php-versions-ubuntulucid-10-04/)

although I believe there are other ways to run multiple versions of php.

---

### Post by SeijiSensei on 2016-10-12
You could run one as a cgi executable and the other using the PHP module for Apache.  I'd use 7.0 as the cgi since you'll probably have to compile it from source anyway.

Another possibility is to run two instances of Apache listening on different ports.  Set up a configuration in the standard Apache configuration for the site that needs 7.0 that redirects to the new server on the custom port.  Something like
```

<VirtualHost *:80>
ServerName newsite.example.com
Redirect / http://newsite.example.com:8080/
</VirtualHost>

```
Then bind the new instance running PHP 7 to port 8080.

---

