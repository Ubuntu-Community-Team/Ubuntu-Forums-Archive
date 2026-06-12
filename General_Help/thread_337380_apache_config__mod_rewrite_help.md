---
title: "apache config / mod_rewrite help"
date: 2007-01-12
forum: General Help
---

### Post by notatoad on 2007-01-12
i am trying to get mod_rewrite working on my localhost. i had my html in ~/code/website/ and an alias so that my site showed up at [http://localhost/website](http://localhost/website)
my .htaccess looked like this:
```

RewriteEngine on
RewriteRule ^testing$ rewrite.php
```

[http://localhost/website/testing](http://localhost/website/testing) gave me a 404 error saying it couldn't find /home/kyle/code/website/rewrite.php, but [http://localhost/website/rewrite.php](http://localhost/website/rewrite.php) worked just fine. i assumed that this was just something funny with aliases, so i moved my code to the apache default location, /var/www/website so i didn't need to use an alias. now, using the same .htaccess file, mod_rewrite doesn't work at all. what gives?

---

