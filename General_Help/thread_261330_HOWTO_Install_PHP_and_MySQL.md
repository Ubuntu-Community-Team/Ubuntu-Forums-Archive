---
title: "HOWTO: Install PHP and MySQL"
date: 2006-09-20
forum: General Help
---

### Post by textguru on 2006-09-20
I have installed a fresh copy of Ubuntu 5.10 on one of my PC. I choose server installation mode so I don't have the Gui mode. How can I install PHP and MySQL using this command line interface.

Btw, I am new to Linux, I am a Windows Server user, my apology if I ask some newbie questions. I wanted to use Ubuntu for some of our web application.

---

### Post by mssever on 2006-09-20
I use Dapper, but I suspect that the following will work for you (I'm assuming that you use/want Apache; this command will install apache if it isn't already installed):
```
sudo aptitude install php5 php5-mysql libapache2-mod-php5 mysql-server
```If you want to browse/search packages from the console, type sudo aptitude.

---

### Post by textguru on 2006-09-20
> **mssever said:**
> I use Dapper, but I suspect that the following will work for you (I'm assuming that you use/want Apache; this command will install apache if it isn't already installed):
```
sudo aptitude install php5 php5-mysql libapache2-mod-php5 mysql-server
```If you want to browse/search packages from the console, type sudo aptitude.

Thanks for the reply. I've tried to type the code that you've point but it didn't work. It is telling that it cannot find any package for php, php5-mysql, and libapache2-mod-php5. What do I need to do?

---

### Post by mssever on 2006-09-20
It might be a difference between Dapper and Breezy. Dapper is the only version of Ubuntu I've used.

You might try to change the 5 in the php stuff to a 4, if you don't mind running php4. Otherwise, do ```
sudo aptitude
``` and search for php and the php's mysql and apache packages.

You might also benefit from enabling the additional repositories:
```
sudo nano /etc/apt/soures.list
```Uncomment (remove the #s) all the lines that begin with deb. Alternately, follow the intructions [here]("http://psychocats.net/ubuntu/sources"). Save, then type ```
sudo apt-get update
``` Try installing again.

---

### Post by undertherift on 2006-09-20
Textguru:
I just finished installing ubuntu 6.06 server, and have installed 5.10 (and then turned it into a server by installing apache/php5/mysql).

But this round, i found an amazing tutorial.  Here's the link - this guy/guys go through everything that you would need in a good server(Setting up static IPs, installing mail thingies, dns servers) but you can pick and choose.  

I've currently installed php5,mysql, bind9 (dns), and apache2 on my 6.06.  

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

Good luck.  I'll check back later to see how things are going or you can PM me.

---

### Post by textguru on 2006-09-20
> **undertherift said:**
> Textguru:
I just finished installing ubuntu 6.06 server, and have installed 5.10 (and then turned it into a server by installing apache/php5/mysql).

But this round, i found an amazing tutorial.  Here's the link - this guy/guys go through everything that you would need in a good server(Setting up static IPs, installing mail thingies, dns servers) but you can pick and choose.  

I've currently installed php5,mysql, bind9 (dns), and apache2 on my 6.06.  

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

Good luck.  I'll check back later to see how things are going or you can PM me.

Thanks for the reference. Will let you know if I encounter such problem. Actually I am planning to install Draper but I cant install it (I dont know how to install it actually). But now, I have seen information from this URL [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) and I think I need to really boot from the CD before I install the server. And also, for the link that you gave, it is really helpful, I see how to install 6.06 ([http://www.howtoforge.com/perfect_setup_ubuntu_6.06)](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)).

Thanks guys, will postback if I do the wrong way.

---

