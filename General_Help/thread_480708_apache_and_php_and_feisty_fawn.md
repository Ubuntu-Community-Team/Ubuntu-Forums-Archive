---
title: "apache and php and feisty fawn"
date: 2007-06-21
forum: General Help
---

### Post by ritesh on 2007-06-21
Hi all Ubuntu Users,

I am trying to design a web query interface for my data in MySQL database through PHP5, when I tried to install Apache web server according to UbuntuGuide ([http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server)...its](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server)...its) showing an error when i issued the following command on the terminal:
command: sudo /etc/init.d/apache2 restart
Result: * Forcing reload of web server (apache2)...                                                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (no pid file) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

Now, i never did server setup before so there error output is looking to me like some Jupiter alphabets........
So my question is:
a) What should I do to setup my Apache webserver  correctly.
b) Any online tutorial or reference material will be highly appreciated...

I am using Ubuntu Feisty Fawn with 64 bit processor........
Thanks once again for ur help.....

---

### Post by ritesh on 2007-06-21
I tried some of the help topics and now when I am giving the commands...

ritesh@helix:/etc$ sudo apt-get install libapache2-mod-php5 && sudo /etc/init.d/apache2 restart
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libapache2-mod-php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 70 not upgraded.
 * Forcing reload of web server (apache2)...                                                                                  httpd (no pid file) not running
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs


Its showing me this....
Thanks

---

### Post by dpcamp on 2007-06-21
it looks like you haven't set up a ip addess yet. if you have a GUI set it up in there under system | Administration | Network

otherwise your going to need to use the [ifconfig]("http://en.wikipedia.org/wiki/Ifconfig") command

---

### Post by ritesh on 2007-06-21
ok...so what i do after giving ifconfig command.....i mean to say how do I really configure it........

---

### Post by ritesh on 2007-06-21
i have a wired ethernet connection........

---

