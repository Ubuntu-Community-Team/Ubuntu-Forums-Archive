---
title: "Strange phpMyAdmin/MySQL issue"
date: 2006-10-12
forum: General Help
---

### Post by msomers on 2006-10-12
I've been installing mythtv on my new ubuntu install (I am a newbie linux user) following [these instructions](http://hyams.webhop.net/mythtv/myth_ubuntu.html). Anyways, I got through everything working fine, including a great run of phpMyAdmin, although I had to go into terminal to actually set the phpMyAdmin password. Well, when I got to the part to actually run mythfrontend & backend, it starts spitting out a bunch of errors saying it can't connect to the MySQL database and the sort.

Anyways, I fire up firefox and type in "localhost" and click on the phpMyAdmin directory, and it spits out this error: "Cannot load mysql extension. Please check your PHP configuration. - Documentation." So I tried to find out how to install the php-MySQL package as reccomended by the documentation and ran the following command:```
aptitude install php5 php5-mysql libapache2-mod-php5 mysql-server
```in a sudo -i shell. This didn't fix the problem.

Does anyone here have any ideas? I'm very new, so if you tell me to do something in the terminal, you should probably throw in what the command is and such.

Thank you so much for the help!

---

### Post by epennings on 2006-10-12
Maybe this guide can help you setting up your LAMP(Linux,Apache,MySQL,PHP) server correctly :
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

