---
title: "Stoping apache2 and mysql5."
date: 2007-05-08
forum: General Help
---

### Post by Yaffle on 2007-05-08
Hello,
I am a bit of a noob so could anyone please write me an command(s) that will stop and start mysql and apache when ran. I don't want them running when not need.

Thanks!

---

### Post by DoktorSeven on 2007-05-08
All from a terminal:

Stop Apache: sudo /etc/init.d/apache2 stop
Start Apache: sudo /etc/init.d/apache2 start
(assuming Apache2)

Stop MySQL: sudo /etc/init.d/mysql stop
Start MySQL: sudo /etc/init.d/mysql start

Keeping either from automatically starting when you boot:

look in /etc/rc2.d and find the links named SXXapache2 and SXXmysql (where XX is some number), then delete them:

sudo rm /etc/rc2.d/SXXapache2 (replace XX with the number)
sudo rm /etc/rc2.d/SXXmysql (replace XX with the number)

To restore them on boot:
sudo ln -s /etc/init.d/apache2 /etc/rc2.d/S91apache2
sudo ln -s /etc/init.d/mysql /etc/rc2.d/S89mysql

---

