---
title: "don't have permission to access index.php"
date: 2008-06-03
forum: General Help
---

### Post by jocadi on 2008-06-03
I have running UBUNTU 7.04 and installed LAMP.
On top of that I installed mediawiki and I trying to configure my new wiki and get the error on my browser

"Forbidden

You don't have permission to access /config/index.php on this server".

I use sudo Nautilus to change access rights but whatever I change it doesn't save.  I am new in Ubuntu and would like to get help how to change the acces rigths on /var/www/inteumwiki  using the terminal console.
Please help!!!

---

### Post by aysiu on 2008-06-03
**First:**
Don't use *sudo* with graphical applications. The proper command is ```
gksudo nautilus
``` not *sudo nautilus*. For more details, read [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

**Second:**
/var/www is probably owned by root, as it should be. Read more here: [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Old Marcus on 2008-06-04
If you don't want to have keep opening nautilus as root, just do
```
sudo chown user /var/www
```
Where user is your username.

---

### Post by az on 2008-06-04
> **Old Marcus said:**
> If you don't want to have keep opening nautilus as root, just do
```
sudo chown user /var/www
```
Where user is your username.

No.  The problem is not that your user is unable to access those folders, but that the web server cannot.  The permissions of the /var/www folder are irrelevant so long as the www-data user can have read-acccess to the files.  Out-of-the-box, the permissions are world-readable and owned by root.  This is desirable so that you can't have anyone write to that folder and make your webserver do things you don't want it to.

In other words, that's not your problem and don't change it; it will become a security risk.

You need to adjust your virtual host settings for that site in /etc/apache2/sites-available.  Edit the default site to point to the correct folder.

---

