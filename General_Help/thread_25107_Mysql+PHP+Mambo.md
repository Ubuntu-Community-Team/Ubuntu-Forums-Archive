---
title: "Mysql+PHP+Mambo"
date: 2005-04-09
forum: General Help
---

### Post by tevfik on 2005-04-09
Fatal error: Call to undefined function: mysql_connect()

download
[http://de.archive.ubuntu.com/ubuntu/pool/universe/p/php4-universe/php4-universe-common_4.3.10-10ubuntu3_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/p/php4-universe/php4-universe-common_4.3.10-10ubuntu3_i386.deb)
and
[http://de.archive.ubuntu.com/ubuntu/pool/universe/p/php4-universe/php4-mysql_4.3.10-10ubuntu3_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/p/php4-universe/php4-mysql_4.3.10-10ubuntu3_i386.deb)


Konsole
sudo dpkg -i php4-universe-common_4.3.10-10ubuntu3_i386.deb
sudo dpkg -i php4-mysql_4.3.10-10ubuntu3_i386.deb

Try to uncomment the following line in /etc/php4/apache2/php.ini:

extension=mysql.so

Mysql support

---

