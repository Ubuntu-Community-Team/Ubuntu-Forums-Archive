---
title: "Ubuntu 22.04 issues with phpmyAdmin"
date: 2024-03-01
forum: General Help
---

### Post by deck on 2024-03-01
I just upgraded my 20.04 desktop and all purpose computer in my Ham Shack to 22.04 after I finally bought a big USB backup drive and backed up my system before upgrading.

I use the system to do a multiplicity of tasks.  One of them is to host my personal website "https://www.lastfrontierinbandera.com" (this is not an advertisement).  I had installed the LAMP stack (mariadb) and WordPress on Ubuntu 20.04; then built my website on that.  When I tested out my website after the upgrade, things were broken.  I found that Apache2 had the PHP7.4 modules in "etc/apache2/mods-enabled" loaded, but /lib/apache2/modules had only libphp8.1.so .  I found out how to install the php8.1 modules in Apache.  When I went through the a2dismod php7.4, systemctl restart apache2, a2enmod php8.1, and systemctl restart apache2, my website was completely broken still.  Doing some research I found that Apache2 had issues with php 8.1, so I installed PHP 7.4 on my system and reverted to the PHP7.4 modules.  My website was back up.

I had been using phpmyadmin to manage my Mariadb instance.  When I tried to run phpmyadmin, the browser (Brave) started with trying to connect to localhost/phpmyadmin and then all of a sudden switched to trying to connect to lastfrontierinbander/phpmyadmin.  WordPress would then issue an error that the page was not available.  I went through and checked to see that the proper files were in the /etc/apache2/conf-available and /etc/apache2/conf-enabled; which they were.  I reran 'dpkg-reconfigure phpadmin' and made sure that the apache2 webserver was selected.  Still the same problem.  Next I did 'apt purge phpmyadmin' because I was thinking that maybe something was hanging around from Ubuntu 20.04 that was causing a problem.  I went so far as to reboot my system for extra assurance.  I next reinstalled phpmyadmin.  I checked for the needed files and then restarted phpmyadmin.  I got the same resuslts.  I looked at the Ubuntu page on phpmyadmin and could see no issues. 

I next checked my WordPress version which was a 6.2.x version and upgraded to the most current 6.4.x version. To see if that would help.  It didn't help.

I am currently unable to see what to do.

deck

---

### Post by dragonfly41 on 2024-03-02
These busy days I draw upon help from Phind.com in browser to supplement forum queries.
Create a carefully worded short prompt (query) thus and paste into Phind.com query box in Brave:

> Compatility issues are found in PHPMyAdmin after upgrading Ubuntu 20.04 desktop to Ubuntu 22.04.  WordPress and MariaDB are in use.

Then you can refine your questions.

---

