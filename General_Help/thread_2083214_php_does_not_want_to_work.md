---
title: "php does not want to work?"
date: 2012-11-11
forum: General Help
---

### Post by workaround on 2012-11-11
php does not want to work?
I call this page:
[http://localhost:8080/index.php](http://localhost:8080/index.php)
and I get:
**[SIZE=2]It works from workdir directory and from php![/SIZE]**

[SIZE=2]This is the [SIZE=2]code:[/SIZE][/SIZE]

[CODE]

---

### Post by workaround on 2012-11-11
I lost the info I wanted to post and when I re-edited it got lost again?
Why does not want to post?

---

### Post by workaround on 2012-11-11
I can run PHP from command line like "... hello ..." and etc but it will not display any "phpinfo" and it will not run in the web brouser?
If I install the php module I get the
```

"/usr/local/apache2/modules/libphp5.so: undefined symbol: unixd_config"

```error! 
I tried to run:
```
sudo apt-get remove --purge apache2 php5 mysql-server-5.0 phpmyadmin
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server
sudo apt-get install phpmyadmin

```but that does not help to resolve the problem!
What am I having than?:confused:

---

### Post by Doug S on 2012-11-12
> **workaround said:**
> I lost the info I wanted to post and when I re-edited it got lost again?
Why does not want to post?I think the fourms are done in vbulliten. Apparently, there is at least one key sequence that gets interpreted as "delete everything that follows". I found it the hard way, and found it seriously annoying. 
 
[Reference thread]("http://ubuntuforums.org/showthread.php?t=1724517").

---

### Post by pkadeel on 2012-11-12
> **workaround said:**
> I can run PHP from command line like "... hello ..." and etc but it will not display any "phpinfo" and it will not run in the web brouser?
If I install the php module I get the
```

"/usr/local/apache2/modules/libphp5.so: undefined symbol: unixd_config"

```error! 
I tried to run:
```
sudo apt-get remove --purge apache2 php5 mysql-server-5.0 phpmyadmin
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server
sudo apt-get install phpmyadmin

```but that does not help to resolve the problem!
What am I having than?:confused:
**[NOTE:] Before going through the method described below, try accessing your localhost without mentioning the port i.e. 8080. I guess it shall work.**

Don't put everything in one install command. Go step by step.
First become su in terminal so that you don't have to enter sudo with each command.

MySQL installation will ask to set root password so chose something to use as MySQL root user's password.
After apache2 install you shall be able to browse localhost without any port because it will be configured to listen on default port 80
```

sudo su
apt-get install mysql-server mysql-client
apt-get install apache2
apt-get install php5 libapache2-mod-php5
service apache2 restart
apt-get install php5-mysql php5-curl php5-gd php5-imap php5-mcrypt php5-ming php5-tidy php5-xmlrpc php5-xsl
service apache2 restart
exit

```

---

### Post by workaround on 2012-11-12
It tells me I need this file: libphp5.so!?
```

apache2: Syntax error on line 239 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: cannot open shared object file: No such file or directory


```what should create the file?:confused:

---

### Post by workaround on 2012-11-12
OK, I removed the PHP5 and libapache2-mod-php5 and reinstalled it again and "Well!" it is working! I was  getting really tired of it, spending so much time on it and missing just bits that can make it so complicated.
Thank YOU VERY MUCH!
:popcorn:

---

