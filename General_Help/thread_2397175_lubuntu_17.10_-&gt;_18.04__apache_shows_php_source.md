---
title: "lubuntu 17.10 -&gt; 18.04 : apache shows php source code instead of processing the php"
date: 2018-07-26
forum: General Help
---

### Post by ReneVeerman on 2018-07-26
i googled it, but can't find what's wrong with my apache setup since the upgrade.. :(

apachectl configtest comes out clean

and i can't find the loadmodule command that loads up php.
all of the google search results for 'apache shows php source code' seem a bit outdated, dealing with php5 and such..

---

### Post by ReneVeerman on 2018-07-26
a2enmod php7.2 

fixed it :D

---

