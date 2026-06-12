---
title: "MySQL management like Navicat"
date: 2017-10-07
forum: General Help
---

### Post by chris137 on 2017-10-07
Hey,
I'm looking for a MySQL management tool like Navicat, where I can view and edit data in my database.
Navicat just really does this nicely but $300 is rather costly for private purposes, 14-days trials are annoying and the Lite version was discontinued.

I just haven't found anything comparable.
I saw people recommending MySQL Workbench. I don't seem to understand this software because I don't see a GUI-way of editing data.
It's not that I'm unable to use a database without a GUI, I just don't want to.

There seeems to be quite a lot of SQL-software but after a few I got tired of trying.
Squirrel SQL was the latest which I didn't even get to run.

---

### Post by SeijiSensei on 2017-10-07
[phpMyAdmin]("https://www.phpmyadmin.net/") is a PHP-based administrative front-end for MySQL. It's in the Ubuntu repositories.

I often use Microsoft Access with the [MySQL ODBC connector]("https://dev.mysql.com/downloads/connector/odbc/") for this purpose.

---

### Post by chris137 on 2017-10-07
phpMyAdmin is not the most ideal solution, as I want to administer databases on at least two different servers so I'd have to install it on those servers.
Also, it's still not as straight-forward as Navicat is.

Regarding ODBC, I assume you mean libreOffice Base? Or are you actually running MS Access on Ubuntu?
I just tried installing ODBC but failed somehow..

---

### Post by SeijiSensei on 2017-10-07
No, I'm talking about running Access on Windows.  And LibreOffice Base doesn't come close to Access, last I looked.

I run Access in a VirtualBox virtual machine when I need it.  Access gets [decent ratings](https://appdb.winehq.org/objectManager.php?sClass=application&iId=12) in terms of compatibility with Wine, but I prefer to use a VM.

---

### Post by chris137 on 2017-10-07
I'm running Navicat on a VM currently but firstly it's annoying to always start Windows to check something in my database and secondly I'd prefer a software which I can (legally) use longer than 14 days.
I've been using Navicat for ages now which got me pretty spoiled I guess.

---

### Post by dragonfly41 on 2017-10-07
I have used webmin to manage localhost and remote resources including MySQL.
But you will read cautions  that installing webmin can lead to attacks so login authentication is vital.

Recently I  have started learning about the possibilities of using ansible for automation of both localhost and remote servers.

If you have SSH keys on your local development system you have to install SSH server on each of your remote servers.
Then you can automate remote MySQL servers as described here ..

[http://docs.ansible.com/ansible/latest/mysql_db_module.html](http://docs.ansible.com/ansible/latest/mysql_db_module.html)

In fact I now use webmin for some localhost development and ansible for remote server instance automation.

---

