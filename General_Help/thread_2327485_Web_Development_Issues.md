---
title: "Web Development Issues"
date: 2016-06-11
forum: General Help
---

### Post by julie5 on 2016-06-11
Not sure if this is the right place but I'm new to Linux and really liking it but having trouble setting up a web development. I have installed Apache2, MySQL and PHP7. The localhost is working as this will show my apache2 page saying it working. Mysql is working and also PHP is working. I have tested this by creating a test.php and also a phpinfo in the var/www/html folder.

Everything fine so far but my issue is when i try to use ready made CMS like Joomla, its in the right folder, but its a blank page, the same goes for another Drupal, just a blank page. What am i doing wrong?

I've Google and found no answer.

---

### Post by dragonfly41 on 2016-06-11
You are not hitting the right google search pattern ...

[http://www.joomlabamboo.com/blog/how-to-joomla/how-to-fix-a-blank-screen-after-upgrading-to-joomla-3-2](http://www.joomlabamboo.com/blog/how-to-joomla/how-to-fix-a-blank-screen-after-upgrading-to-joomla-3-2)

as suggested turn on full error reporting. It can be a configuration quirk or permissions.
Also inspect your apache2 logs.

[later edit]

Here is an up to date link ... [http://forum.joomla.org/viewtopic.php?t=922729](http://forum.joomla.org/viewtopic.php?t=922729)

---

### Post by julie5 on 2016-06-12
Thanks for the link.

After looking into fixes, i purge PHP and reinstalled it and now PHP is not working. I'm just making this worse. My new question is how do i get back to the original state and purge apache2, php and MySql and start from scratch?

When i reload the php page, so tailing the apache2 error log and its not updating when the php page being reloaded

---

### Post by dragonfly41 on 2016-06-12
Oh dear ... perhaps you should just install a LAMP stack which will likely be PHP5 and not PHP7.
You can progress to using PHP7 later.

You have not clarified what distro you are using .. here are just two links I found (there are many out there on LAMP stack installation).
[https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu)
[https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04)

Since you are starting from scratch and evaluating CMS frameworks I would just add a suggestion to also try out laravel5 which requires composer to be installed.

[https://laravel.com/](https://laravel.com/)

There are many tutorials at laracasts.

[later edit]

re: purging PHP7.0 ... [http://askubuntu.com/questions/716661/how-do-i-remove-php-7-completely](http://askubuntu.com/questions/716661/how-do-i-remove-php-7-completely)

---

