---
title: "Installing php-ming extension on Ubuntu 5.04"
date: 2005-05-05
forum: General Help
---

### Post by abmcr on 2005-05-05
Because the packages of php-ming librarie are not present in the repository, i have used a rpm packages with alien. For installing php-ming it is now possible to do:
1) download the libming.so deb package from 
[http://abmcr.altervista.org/libming0-devel_0.3-1_i386.deb](http://abmcr.altervista.org/libming0-devel_0.3-1_i386.deb)
(don't click over URL but copy and paste into your adress toolbar of browser)

2) download the ming.deb packages from
abmcr.altervista.org/php-ming_4.3.4-2_i386.deb
(don't click over URL but copy and paste into your adress toolbar of browser)

3)Move the ming.so into the correct directory
sudo cp /usr/lib/php/extensions/ming.so /usr/lib/php4/20020429/

3) sudo gedit /etc/php4/apache2/php.ini
and insert the follow row
extension=ming.so

4) restart Apache
sudo /etc/init.d/apache2 restart 

NB: the ming.so library is NOT compatible with the swf version 6 or 7. It is necessary to change the first rows of php script you use in this mode:

<?php
 
    // set the Flash version
    ming_useswfversion(5);


if another version is setting.
Ciao

---

### Post by macewan on 2005-07-13
[QUOTE=abmcr]Because the packages of php-ming librarie are not present in the repository, i have used a rpm packages with alien. For installing php-ming it is now possible to do:
1) download the libming.so deb package from 
[http://abmcr.altervista.org/libming0-devel_0.3-1_i386.deb](http://abmcr.altervista.org/libming0-devel_0.3-1_i386.deb)
(don't click over URL but copy and paste into your adress toolbar of browser)

2) download the ming.deb packages from
abmcr.altervista.org/php-ming_4.3.4-2_i386.deb
(don't click over URL but copy and paste into your adress toolbar of browser)

3)Move the ming.so into the correct directory
sudo cp /usr/lib/php/extensions/ming.so /usr/lib/php4/20020429/

3) sudo gedit /etc/php4/apache2/php.ini
and insert the follow row
extension=ming.so

4) restart Apache
sudo /etc/init.d/apache2 restart 

NB: the ming.so library is NOT compatible with the swf version 6 or 7. It is necessary to change the first rows of php script you use in this mode:

<?php
 
    // set the Flash version
    ming_useswfversion(5);


if another version is setting.
Ciao[/QUOTE]



do you still have these two .debs?

does anyone have a copy?

---

