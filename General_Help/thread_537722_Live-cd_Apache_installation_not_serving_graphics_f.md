---
title: "Live-cd Apache installation not serving graphics files."
date: 2007-08-29
forum: General Help
---

### Post by TIm Blokdijk on 2007-08-29
Hello,

I'm trying to use the Ubuntu live cd as a base for site development.
That probably sounds strange but "we" ([SpringRTS]("http://spring.clan-sy.com")) have a lot of developers on the Windows OS. The site runs on Linux so I'm trying to make it easy for the Windows people to run the site code on there own machine. (by using the Ubuntu live cd)

Now I'm running into this easy to replicate problem...
Boot the live cd and run "sudo tasksel install lamp-server" in a terminal to install the lamp stack.
Now start firefox and try to request any of the graphics files from the Apache default page. It will fail.
I have enough ram left so it's not running out of "disk" space. Opera and Galeon have the same problem. Any graphics from that don't come from "localhost" show up fine. So it seems to be Apache that won't send those files, php on the other hand gets parsed fine..

Any idea what is causing this? And any idea how to fix this? No need for a clean fix btw, as it's just a live cd environment.

For those interested, this is the bash code I use to set up the site on the live cd.

```
sudo tasksel install lamp-server
sudo apt-get install subversion
mkdir ~/tmp/
cd ~/tmp/
svn checkout https://spring.clan-sy.com/svn/spring/trunk/Site/
sudo rm /var/www/ -R
sudo ln -s /home/ubuntu/tmp/Site/www-root /var/www
sudo mysqladmin --host=localhost --user=root create spring
sudo mysql --verbose --user=root spring < /home/ubuntu/tmp/Site/Documentation/spring.sql
sudo mysql --verbose --user=root --execute="GRANT ALL PRIVILEGES ON *.* TO 'spring_user'@'localhost' IDENTIFIED BY 'password' WITH GRANT OPTION;" mysql
sudo cp /home/ubuntu/tmp/Site/configuration.example.php /var/configuration.php
sudo chmod 777 /etc/apache2/httpd.conf
sudo echo "Alias /wiki /var/www/w/index.php" >> /etc/apache2/httpd.conf
sudo /etc/init.d/mysql restart
sudo /etc/init.d/apache2 restart
```

---

### Post by az on 2007-08-29
Does www-data have read permissions to /home/ubuntu/tmp/Site/www-root?

---

### Post by TIm Blokdijk on 2007-08-29
I'm not quite sure, the Apache default page has the same problems so then permissions must be wrong for that to. Anyway, let me boot the live cd...

---

### Post by TIm Blokdijk on 2007-08-29
I ran the following commands after installing the lamp-server:
ubuntu@ubuntu:~$ sudo chown www-data /var/www/ -R
ubuntu@ubuntu:~$ sudo chmod 777 /var/www/ -R

Didn't solve the issue, any other ideas?

---

### Post by az on 2007-08-29
What about changing the documentroot to the default site (/etc/apache2/sites-available/default) to /home/ubuntu/tmp/Site/www-root ?  I am not able to try it out, but perhaps the fact that some parts of the filesystem are read-only (directly from the cramfs on the cd) has something to do with it?

---

### Post by mloudon on 2007-09-01
In case you haven't yet fixed this problem, see: [https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/95393]("https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/95393")

You need to set  EnableSendfile Off in apache2.conf

---

