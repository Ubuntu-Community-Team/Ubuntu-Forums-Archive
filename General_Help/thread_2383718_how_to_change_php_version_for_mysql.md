---
title: "how to change php version for mysql?"
date: 2018-01-28
forum: General Help
---

### Post by garyed on 2018-01-28
I have two versions of php on Ubuntu 16.04 ,  7.0 and 5.6
7.0 runs everything including mysql fine but 5.6 will not connect to mysql database. I want to be able to switch between versions on my computer until my site is totally updated to php 7.0 which is going to take quite a while.   
I use the a2dismod  &  a2enmod  commands & then service apache2 restart to switch between the two versions. When I test using a phpinfo file through Apache it shows the changes correctly but if I use the terminal the change does not show. In other words if I do ```
php -r 'phpinfo():'
``` in the terminal it will show php 7.0 while Apache will show php 5.6.  So I'm pretty sure that mysql is not accepting the changes done by the a2dismod & a2enmod commands. Is there a command similar to ```
service apache2 restart
``` for mysql to accept php version changes or is there a config file that needs to be edited?

---

### Post by Holger_Gehrke on 2018-01-29
The php cli executable is separate from the apache module; to switch to the 5.6 cli executable you'd use update-alternatives. 
mysql doesn't care one way or the other who or what is on the other end of the connection as long as it 'talks' the right protocol. 
BUT php 7.0 and 5.6 have separate ini-files '/etc/php/7.0/apache2/php.ini' and '/etc/php/5.6/apache2/php.ini' - so it might just be a misconfiguration of the 5.6 module.

Holger

---

### Post by garyed on 2018-01-29
Thanks,
I looked at the two php.ini files for 5.6 & 7.0 but I have no idea what would need to be added or changed to make 5.6 work with mysql. I can't remember for sure if 5.6 used to work on this computer but i think it did before I installed 7.0. I've been dealing with this for a while now.

---

### Post by dragonfly41 on 2018-01-29
This blog gives tips on setting up separate virtual hosts .. one for each version of php ..

[https://pehapkari.cz/blog/2017/03/27/multiple-php-versions-the-easy-way/](https://pehapkari.cz/blog/2017/03/27/multiple-php-versions-the-easy-way/)

[Later edit]

Noted this link buried in above blog ...

[https://github.com/leymannx/apache-multiphp](https://github.com/leymannx/apache-multiphp)

And finally ideas (perhaps) on using multiple MySQL sessions ...

[http://lasanthals.blogspot.co.uk/2012/09/running-multiple-instances-of-mysql-on.html](http://lasanthals.blogspot.co.uk/2012/09/running-multiple-instances-of-mysql-on.html)

---

### Post by garyed on 2018-01-29
Thanks ,
I'll be checking out those links but I've got to get back to work for now.

---

