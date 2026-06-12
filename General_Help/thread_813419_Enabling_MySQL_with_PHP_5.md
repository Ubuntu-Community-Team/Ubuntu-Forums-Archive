---
title: "Enabling MySQL with PHP 5"
date: 2008-05-30
forum: General Help
---

### Post by totemg on 2008-05-30
How do I set up MySQL with PHP 5 in Ubuntu? I have read that I can move mysql.so into a place where PHP can find it. I don't have a mysql.so and I don't know where PHP can find it. I have PHP, Apache, and MySQL installed. Can someone tell me how to enable MySQL to work with PHP?

---

### Post by Monicker on 2008-05-30
If you installed the Ubuntu packages for mysql and php you shouldn't have to do anything else to make it work.  Are you having problems with a particular php script that is trying to connect to mysql?  If so, what error messages are you seeing?

---

### Post by Kinnza on 2008-05-30
try this:

gksudo gedit /etc/php5/apache2/php.ini

Now we are going to have to uncomment the following line by taking out the semicolon (;).

Change this line:

;extension=mysql.so

To look like this:

extension=mysql.so

---

