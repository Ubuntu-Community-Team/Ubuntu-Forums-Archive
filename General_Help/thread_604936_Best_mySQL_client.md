---
title: "Best mySQL client"
date: 2007-11-06
forum: General Help
---

### Post by iamPatrick on 2007-11-06
What are the best  MySQL clients available for Ubuntu/linux?

I've been using MySQL Query Browser/Tool but its rubbish (lacks features, crashes, annoying interface). In windows I'm a fan of SQLyog and am tempted to just use Wine to get myself set but there has to be something better which is native.

So whats out there guys?

---

### Post by NT4usB on 2007-11-06
Not sure if this is what you're looking for. My MythTV setup uses mysql DB and installs apache2 and phpmyadmin so I can mess around in it using my browser.
They're in the repositories.

---

### Post by iamPatrick on 2007-11-06
um, I don't think thats what I want. At least I'd hate to have to install MythTV just to edit some tables. Hah.

I'm looking for database management apps.

---

### Post by KCPokes on 2007-11-06
> **iamPatrick said:**
> um, I don't think thats what I want. At least I'd hate to have to install MythTV just to edit some tables. Hah.

I'm looking for database management apps.

I think the point was that you could use Apache and PhpMyAdmin for supporting your MySQL instances rather then a complete MythTV install.  PHPMyAdmin is better then any of the pure GUI based (standalone) tools that I've used.

---

### Post by iamPatrick on 2007-11-06
Ok, now I understand!
Honestly I'm not interested in installing a web server just to get at some databases but I'll play with it.

Which of the standalone tools do you like best?

---

### Post by KCPokes on 2007-11-06
> **iamPatrick said:**
> Ok, now I understand!
Honestly I'm not interested in installing a web server just to get at some databases but I'll play with it.

Which of the standalone tools do you like best?

Personally I don't use any standalone tools.  Normally the box that I'm working on is not local, thus I get used to either using a web interface (webmin or phpmyadmin) or I just use a terminal and standard mysql commands.  Its not going to be the most attractive approach for most people but after years of only having SSH access through the firewalls you get used to it.  Plus I found, like you said, that most of the tools were a bit bloated and made simple things more confusing then they had to be.

---

### Post by iamPatrick on 2007-11-06
Knew I couldn't be the only one:
[http://lists.mysql.com/mysql/205616](http://lists.mysql.com/mysql/205616)

---

### Post by KCPokes on 2007-11-07
Funny that I was actually reading through this morning and came across this post:

[http://ubuntuforums.org/showthread.php?t=125911&page=2](http://ubuntuforums.org/showthread.php?t=125911&page=2)

It is in regards to DBDesigner ([http://www.fabforce.net/dbdesigner4/index.php](http://www.fabforce.net/dbdesigner4/index.php)), which I haven't used bu it looks really promising, if you can get past the installation challenges.

---

### Post by ruz322 on 2007-11-07
Are you looking to run queries or just administer the server itself? MySQL comes with several tools that they put out themselves that do a really good job of it. phpmyadmin works really well in the web interface.

---

### Post by ruz322 on 2007-11-07
Those tools are packages mysql-admin and mysql-navigator. Sorry i didn't post that in the last one. Install them using apt-get, they will auto-register in the gnome menu.

---

### Post by iamPatrick on 2007-11-12
@ruz 
I'm looking to create and edit tables. No server management.
I tried using official MySQL apps already but really couldn't stand them.

@KCPokes
Thanks! I'm going to try this out.


So far I've been getting by using SQLyog through Wine, which works great.

---

