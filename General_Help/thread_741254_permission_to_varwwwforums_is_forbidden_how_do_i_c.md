---
title: "permission to /var/www/forums is forbidden how do i chmod"
date: 2008-03-31
forum: General Help
---

### Post by DJ_Crash on 2008-03-31
hello again,

i have recently installed apache2,php, and mysql along with some forums that i am also about to install however im having trouble running chmod command on /forums folder can somebody show me a way to get this done?

i have tried filezilla and by using the following sudo command:

sudo chmod -R 777 <user> /var/www/forums

maybe theres another command i must add?

---

### Post by gsmanners on 2008-03-31
If you're using FTP, you'll need to make sure that the FTPd on the box specifically allows chmod for that user (the name you use for logging in).

---

### Post by cdenley on 2008-03-31
That's not the right usage. I think what you want is
```
sudo chown -R <user> /var/www/forums
sudo chmod -R 777 /var/www/forums
```
You shouldn't give everyone write access to your website, though, so you might want to use some more restrictive permissions.

---

### Post by sheffrem on 2008-03-31
indeed its really not good to allow anybody to acces your files freely. This implies that if know your website(s) it will be easy for me to modify your php,html,asp and other files. Rather give the permission to user apache and group apache as it will put some restriction execpt for you if you are root. No body can login with either apache user or group. So i advice to do this rather.

chmod -R 755 /var/www/forums

chown apache:apche /var/www/forums

---

### Post by chilinski on 2008-03-31
You may also need to make adjustments in your httpd.conf file if you intend to use virtual hosts to get to the webpages. Permissions can be set there, too.

---

### Post by cdenley on 2008-04-01
In ubuntu, there is no apache user by default. Apache is run as the user www-data, and is a member of the group www-data. I would not recommend giving www-data write permissions, since that user is probably most likely to be compromised on a webserver (web scripting exploit). Also, in ubuntu, httpd.conf is no longer used, and virtual hosts are split into seperate configuration files in /etc/apache2/sites-available.

---

