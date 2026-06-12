---
title: "MySQL host name my network"
date: 2015-02-04
forum: General Help
---

### Post by huffmanp on 2015-02-04
I wanted to test MySQL 5.5 with FileMaker, and my internet hosting company is running 5.1.   So I went to my Unbuntu PC on my office LAN,  downloaded MySQL 5.5,  and got it running. The MySQL monitor starts up at a terminal, and I loaded in some test data from an old MySQL course. I found a MySQL admin tool at the Ubuntu Software Center, Emma, and it works well. I defined the connection to the MySQL host as localhost host, and I can see my new tables and data. 

But I'm not sure if my new installation is serving on my LAN.  Moving to a Windows 7 machine,  I can see my Ubuntu PC in Network.  I have a MySQL admin program running on Windows called Navicat.  But when I try to define a new connection in Navicat, I just get 'Can't connect to MySQL server on 192.168.3.31'  Tried the host name in the connection as well.  I can't test it with FileMaker until I verify that my new instance is reachable.  Is there another way to test without depending on Navicat?

---

### Post by SeijiSensei on 2015-02-04
By default, MySQL only listens on the localhost interface, 127.0.0.1.  To change this you need to edit /etc/mysql/my.cnf and replace "bind-address = 127.0.0.1" with "bind-address = *" so it will listen on all interfaces.  Then restart MySQL with "sudo service mysql restart".

---

### Post by huffmanp on 2015-02-04
Oooo, that's better.  Now I get a message "Host  192.168.3.16 is not allowed to connect to this MySQL server"  But I've seen that before.  I need to give this new install a list or a range of hosts that are allowed to attach.

Got it. Granted a new user @'%' and I'm in business.  Now to see if FileMaker can connect. [http://forums.filemaker.com/posts/6e6e60efa3](http://forums.filemaker.com/posts/6e6e60efa3)

 Thanks for the help.

---

