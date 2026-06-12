---
title: "Test environment for PHP and web development"
date: 2005-06-21
forum: General Help
---

### Post by mglukhovsky on 2005-06-21
I've been working a lot lately with CMS (Content Management System) and PHP scripts. It's a pain to have to connect via FTP to the server every time I want to test the script or view the changes in the CMS.

In Windows I used to test my Mambo sites with something called [MSAS](http://www.mambosolutions.com/main/content/view/13/59/) which was a "local web server application with preinstalled Mambo 4.5.2, Apache, PHP, MySql and phpMyAdmin." Is there any way I can set up the same type of local web server so that I don't have to upload my updates each time and can work on my sites w/o an Internet connection? I see software like PHP and mySQL in the Ubuntu repos, but I don't know how to configure it so that I can use them locally in the manner I described.

Any ideas?

---

### Post by xy77 on 2005-06-21
quick dirty installation guide:

```

$ sudo apt-get install apache2 mysql-server libapache2-mod-php4 php4-mysql phpmyadmin
# phpmyadmin is not strictly necessary, but useful
# if necessary
$ sudo /etc/init.d/apache2 restart
$ sudo /etc/init.d/mysql restart

```

open [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) in browser

This should open the phpmyadmin interface to your mysql db. You should set a password to limit access to server.

get Mambo.x.y.z.tar.gz and extract it to /var/www/
```

$ tar xvfz Mambo.x.y.z.tar.gz
$ sudo mv Mambo.x.y.z /var/www/mambo

```

follow the installation instructions. You will have to set some permissions for files below /var/www/mambo




If you are in a multiuser environment, you may want to enable apaches userdir, i.e. you can access the directory /home/username/public_html as [http://localhost/~username/](http://localhost/~username/)

Please report any problems. If you need help configuring /etc/apache2/apache2.conf, check the manual or post questions here.

Hope this helps.

Greetings,
  David (xy77)

---

### Post by mglukhovsky on 2005-06-21
Thanks so much for replying... I tried this on a test machine, and it worked well enough. But someone tipped me off to Xampp, which simplifies the installation and is easily installabe/removable/upgradeable- it is a "developers testbed", which was exactly what I was looking for. Thanks so much for all your help, but take a look at Xampp!

[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html) (Link to Xampp)

---

