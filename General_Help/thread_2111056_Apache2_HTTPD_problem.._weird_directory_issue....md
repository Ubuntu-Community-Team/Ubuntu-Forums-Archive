---
title: "Apache2 HTTPD problem.. weird directory issue..."
date: 2013-01-31
forum: General Help
---

### Post by ksaul on 2013-01-31
So i have apache2, php5, mysql, phpmyadmin running on my home PC for my personal php projects and web development projects but I am running into a weird issue with access to the directories (in the Browser, NOT the filesystem)

```
<img src="/images/another/image.jpg" />
```

will not show an image even though the image exists. When i try to go to 
[http://localhost/images/another/](http://localhost/images/another/) I get an error saying I do not have access to view or access that folder.. my apache config is nothing special, if i remember correctly it is the default config (other than adding support for phpmyadmin.

example of my problem: (this is from the browser -- when viewing the website NOT when im using a file system manager)
/var/www/html/ - works/have access
/var/www/html/images/ - works/have access
/var/www/html/images/another/ - exists, but do not have access
/var/www/html/images/another/image.jpg - exists but do not have access
/var/www/html/js - works/aave access
/var/www/html/js/jquery/ - exists but do not have access
/var/www/html/js/jquery/jquery.js - exists but do not have access


can someone please help?

---

### Post by ksaul on 2013-01-31
there are no .htaccess files in any of the subdirecories

---

### Post by darkager on 2013-02-01
I'm not an expert with this, but I'll lend my help, as I've recently overcome similar issues.
Can you post the contents of your sites-enabled configuration in the /etc/apache2/sites-enabled dir?

---

### Post by SeijiSensei on 2013-02-01
If this is a vanilla installation, the default DocumentRoot is /var/www, not /var/www/html.  /var/www/html is the default on RedHat and its derivatives like CentOS.  Either move everything in /var/www/html into /var/www, or change the DocumentRoot directive in /etc/apache2/sites-available/default to /var/www/html, and change the associated <Directory> directive as well.  Then restart Apache with "sudo service apache2 restart".

---

