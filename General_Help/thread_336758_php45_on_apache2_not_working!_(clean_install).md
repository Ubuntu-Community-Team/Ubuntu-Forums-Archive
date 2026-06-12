---
title: "php4/5 on apache2 not working! (clean install)"
date: 2007-01-12
forum: General Help
---

### Post by Nite23 on 2007-01-12
i just made a clean install of Edgy, 64bit version. First thing i did was to install LAMP with apt-get...
apache works with html, but whenever i want to view a php file, instead of showing generated content, firefox want to download it...
so i tryed to uninstall php5 and install php4.. then reinstall apache... nothing helps... 
i also looked to apache config files, and mod directory,  and everything seems to be in place... 

please help me, i already lost a lot of time with this, and it makes me really mad...  :mad:

---

### Post by Nite23 on 2007-01-12
solved... i completely removed everything, and installed again, and now it works 

i think problem was that i installed both packages apache2-mpm-worker and apache-mpm-prefork...  apache2 selects worker by default as it's dependency, but php5 needs prefork

---

