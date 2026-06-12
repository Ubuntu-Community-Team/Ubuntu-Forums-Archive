---
title: "phpmyadmin not working"
date: 2008-05-19
forum: General Help
---

### Post by mjsrose on 2008-05-19
Hi hope that someone can help me please. I have ubuntu 7.01 and have just installed Apache2, Mysql server and client and phpmyadmin.

Have /var/www with Apache2 and phpmyadmin in it, phpmyadmin seems to be a symbolic link, which i believe it should be, But when i go to Firefox and open localhost, i get the directory link which again i believe is right. But when i click on phpmyadmin i get the message you are trying to open a php file .... I believe it should just open phpmyadmin.

I presume that it is a question of permissions or maybe ownership. But i do not have a clue what to alter.

Thanks

rose

---

### Post by Thirtysixway on 2008-05-19
It sounds to me like you forgot to install php.

```

sudo aptitude install php5 libapache2-mod-php5

sudo /etc/init.d/apache2 restart

```

---

### Post by mjsrose on 2008-05-20
I reinstalled php and I am still getting the same problem

rose

---

### Post by cdtech on 2008-05-20
Did you enable the module:
sudo a2enmod php5

Then do a retart of apache:
sudo /etc/init.d/apache2 restart

---

