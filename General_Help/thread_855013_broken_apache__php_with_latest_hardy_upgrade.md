---
title: "broken apache / php with latest hardy upgrade"
date: 2008-07-10
forum: General Help
---

### Post by yee379 on 2008-07-10
Hi,

i did a system update; however, it appears that my php/apache setup is now broken - going to a php site results in a download prompt rather than displaying the output of the php code.

i tried doing a 

> 
aptitude purge apache2 php5 libapache2-mod-php5 libapache2-mod-php4 php4 php5 mythweb php5-mysql php-config


> 
rm -rf /etc/apache2


[QUOTE]
aptitude reinstall apache2 php5 libapache2-mod-php5 libapache2-mod-php4 php4 php5 mythweb php5-mysql php-config
[\QUOTE]

but now my apache config directory only has the sites-available and mods-available directories inside (ie no other config files or directories). replacing this with my previous configuration still results in the same error as before :(

the relevant AddHandler etc are in the configs... help?!

cheers,

---

