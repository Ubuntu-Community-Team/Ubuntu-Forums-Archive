---
title: "Mythweb Redirects Problem"
date: 2014-12-08
forum: General Help
---

### Post by thorn1 on 2014-12-08
Hi, I'm trying to figure out how to stop mythweb from automatically redirecting from root doc (/var/www) to /var/www/mythweb. I searched here and online but have not found a solution. I tried uninstalled mythweb and reinstalling apache but it still does it. I checked the index.html file and all the apache conf files without luck. There must be somewhere apache is getting the parameters.  I looked in /etc/apache2/sites-enabled/mythweb.conf and there's some parameters in there that might be causing it but I'm not sure:

 # Redirect most of the remaining URL requests to the main mythweb script.
# It will then handle any requests given to it.
RewriteRule     ^(.+)$                  mythweb.php/$1              [QSA,L]

But I'm not sure how to fix it.  Has anyone else had the same trouble before?

Thanks, Greg

---

