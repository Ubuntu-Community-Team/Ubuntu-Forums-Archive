---
title: "Use existing Tomcat7 instance with Eclipse"
date: 2015-05-23
forum: General Help
---

### Post by Maximiliano Gasparini on 2015-05-23
Hello There!

I posted this in here, because looked at similar issue in this sub-forum. Please, in case to make a mistake, just tell me and I will delete the post and create in the right sub-forum.

The environment is:
Ubuntu 14.04 LTS.
apache2  (2.4.7-1)
PHP5       (5.5.9)
mysql      (5.5.43)
Tomcat7  (7.0.52-1) installed directory:  /USR/Share/tomcat7
Oracle Java 8
Eclipse Jave EE IDE for Web Developers Version Luna SR2 (4.4.2)  Installed directory: /opt/eclipse

Each Application works fine: 

I can access with Firefox to: localhost:8080 , loggin whit the admin user tolocalhost:8080/manager , execute the examples... Tomcat 7 works right.
Ecplise also is ok. I can create a new server Runtime, select Apache Tomcat v7.0 , especify the Installation directory, and my JRE.

..but, when I see the status in the server tab, under Eclipse, says that server is Stopped. If I try to start the server, an error message appears: server is running.
If course, if I stop the server using in Terminal: sudo service tomcat7 stop , I can start the server in eclipse, but a new instance.

All the forums and articles that I found, explain how we can start a new instance. But my question is: how can I use the Tomcat7 instance that I run outside Eclipse?

Thanks a lot!

Maxi

---

