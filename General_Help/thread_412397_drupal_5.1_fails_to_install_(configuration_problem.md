---
title: "drupal 5.1 fails to install (configuration problem?)"
date: 2007-04-18
forum: General Help
---

### Post by Askrates on 2007-04-18
I have tried again and again to install drupal 5.1 from the repositories, but no luck so far.

Maybe someone from the friendly Ubuntu community can help?

I have a working LAMP install running on Feisty with all updates.

Drupal installs fine using apt-get, but in the final part of the install process after I have entered the MYSQL Password, I get this error:

...
dbconfig-common: writing config to /etc/dbconfig-common/drupal-5.1.conf
Replacing config file /etc/drupal/5.1/sites/default/dbconfig.php with new version
granting access to database drupal51 for drupal51@localhost: success.
verifying access for drupal51@localhost: success.
creating database drupal51: success.
verifying database drupal51 exists: success.
dbconfig-common: flushing administrative password
dpkg: error processing drupal-5.1 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 drupal-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)

Help!?

---

### Post by Askrates on 2007-04-18
Found out myself. Apparently, you can't install it just like that.

There is a great guide here for people having the same trouble:
[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

Cheers

---

### Post by nairod on 2007-05-16
but the link for the drupal installation refers to drupal 4.7. Tried changing the link to download, didn't work out very well... and in any case, where do you look for the files? they are not in /var/www/drupal ... there is no drupal folder there... it's under usr/share ... HELP please!

---

### Post by az on 2007-05-16
> **nairod said:**
> but the link for the drupal installation refers to drupal 4.7. Tried changing the link to download, didn't work out very well... and in any case, where do you look for the files? they are not in /var/www/drupal ... there is no drupal folder there... it's under usr/share ... HELP please!

That howto covers 5.1

[https://help.ubuntu.com/community/Drupal#head-c55ea134d6f49e680d65147b8844e526065fd4e2](https://help.ubuntu.com/community/Drupal#head-c55ea134d6f49e680d65147b8844e526065fd4e2)


Remove the drupal packages first, though.

sudo apt-get remove drupal-5.1

---

### Post by jingo811 on 2007-05-21
I installed an older malfunctioned Drupal version via Synaptic.  I seem to get the same or similar error.
So I uninstalled it via Synaptic and got this error how can I clean it completely before following your Drupal install guide?
```

(Reading database ... 99731 files and directories currently installed.)
Removing drupal ...
dpkg: error processing drupal (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 drupal
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```


**Second analysis:**
It seems it was entirely cleaned if I tried to uninstall Drupal a second time on Synaptic.  There might not be any problem anymore.  Now I'll try follow your install guide.

---

### Post by skelleton on 2007-05-22
Try first to complete remove mysql and drupal...via synaptic package manager, i did have the same issue...

then i installed it like this...and after i did the below i surf in to [http://localhost/drupal](http://localhost/drupal) and there it was, working :-)

First installed all the components php, mysql etc.
then i created a root password for mysql wit "mysqladmin -u root password "yournewpassord"
after that i try to connect to the mysql db to check if everything worked out like this: mysql -u root -p
if you connect to the mysql db then you are good to go for the drupal installation...

i choose synaptic package manager for the installation...while installing it starts i wizard so drupal can fix whit mysql... first you will get a question if you want to configure mysql, choose yes of course, then you will choose the database,(mysql) then it will ask for a password. Now that you have set the mysql root password like we did a the very beginning it will install drupal with no problem...just put that password and hope that you remember what password you did assign :-) now choose a mysql drupal database password twice and you should be fine with the installation.

good luck... hope it works for your to.
sorry about the text aim tired and got up early tomorrow.

/skelleton

---

### Post by satellite360 on 2007-05-30
Installed Drupal 5.1 on my local Ubuntu box following this guide:
[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

However, when I go to my localhost page I get a long list of warnings starting with the following:
```

Warning: Table 'databasename.access' doesn't exist query: SELECT CASE WHEN status=1 THEN 0 ELSE 1 END FROM access WHERE type = 'host' AND LOWER('127.0.0.1') LIKE LOWER(mask) ORDER BY status DESC LIMIT 0, 1 in /path/includes/database.mysql.inc on line 172

Warning: session_start() [function.session-start]: Cannot send session cookie - headers already sent by (output started at /path/database.mysql.inc:172) in /path/includes/bootstrap.inc on line 811

...

```
and a single fatal error:
```

Fatal error: Call to undefined function block_list() in /path/includes/theme.inc on line 1013

```
I checked the database in phpMy Admin and it exists but contains no tables.

Grateful for any advice on how to get this working.

Thanks

====================================================

This problem was solved quite simply by loading up the install.php page ([www.example.com/install.php](www.example.com/install.php)) in the browser.  This should load up automatically but for some reason wasn't on my system.

---

