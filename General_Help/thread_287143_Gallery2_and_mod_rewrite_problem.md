---
title: "Gallery2 and mod_rewrite problem"
date: 2006-10-28
forum: General Help
---

### Post by megadyptes on 2006-10-28
I've just installed Gallery2 on Edgy running Apache2, php5 and mySQL5. Everything seems to have gone okay with the install, but I'm having difficulty getting the URL Rewrite module to activate.

It says that Apache mod_rewrite cannot be detected, yet [COLOR="Blue"]rewrite.load[/COLOR] is present in [COLOR="Purple"]/etc/apache2/mods_enabled[/COLOR].

Any ideas?

---

### Post by SeanTater on 2006-10-31
try restarting apache:

```
sudo /etc/init.d/apache2 force-reload
``` and try again.

---

### Post by jimmygoon on 2006-10-31
sudo a2enmod rewrite
sudo /etc/init.d/apache2 force-reload

---

### Post by PriceChild on 2006-10-31
> **jimmygoon said:**
> sudo a2enmod rewrite
sudo /etc/init.d/apache2 force-reloadI've found this method always works, wheras manually moving around the files doesn't :(

---

### Post by matthewstory on 2006-10-31
have you issued the RewriteEngine On directive in the gallery2 directory?

---

