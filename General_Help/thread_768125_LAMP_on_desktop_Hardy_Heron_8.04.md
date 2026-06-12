---
title: "LAMP on desktop Hardy Heron 8.04"
date: 2008-04-26
forum: General Help
---

### Post by nami on 2008-04-26
How do I install LAMP on my desktop PC so I can use it as a development environment?

I would like the latest versions of the following installed and setup and was wondering if it could be done with a single command line?

MySQL
PHP
Apache
SQLite
cgi
 -perl
 -python
 -C++

The last 3 should run as cgi from the browser.

Please help

---

### Post by Qwerty_ on 2008-04-26
I dont know about doing it in one line but I have followed the follow on several occasions to setup LAMP.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I am sure they should still work in 8.04

---

### Post by Naatan on 2008-04-26
well of course you can install them all with one single command;

$ sudo apt-get install mysql-server mysql-client sqlite3 apache2 php5 php5-mysql php5-sqlite3 g++

But I'm not sure if you'll be able to run perl, python and c++ as cgi from the browser by default.

---

### Post by nami on 2008-04-26
I't seems to be working but I'm not tried a test page to connect to mysql yet.  How do I configure CGI with perl, python and C++?

---

### Post by Naatan on 2008-04-26
Have you tried checking if it works out-of-the-box to begin with?

---

### Post by Mike V on 2008-04-27
Hi, I have a similar problem, I want to install a LAMP server and then on top of it the gnome desktop, can I do it both from CD?, the last time I did this on gutsy it begin to download all the desktop packages from the web and this is a no-no because of my speed connection, this way is faster and don't mess with the configurations of apache-php-mysql/gnome.

What do I need to edit when the server is installed so I only need to put the CD in the tray and do a sudo apt-get install ubuntu-desktop

---

