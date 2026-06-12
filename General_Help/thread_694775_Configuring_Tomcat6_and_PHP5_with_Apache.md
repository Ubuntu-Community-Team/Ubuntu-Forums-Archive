---
title: "Configuring Tomcat6 and PHP5 with Apache"
date: 2008-02-12
forum: General Help
---

### Post by cosmograph on 2008-02-12
It's been a long hard road but I finally got a LAMP server setup with Ubuntu 7.10 . I'm a complete newbie to servers so I'm really struggling.

I'm trying to run an application that runs a Java servlet and links into some PHP/ MySQL tables I have written.  I've setup TOmcat 6 in usr/local and it works fine and the PHP/ Mysql stuff is located in /var/www with the other html stuff and also works fine.

I've even setup mod_proxy to forward requests destined for the servlet  to Tomcat 6 with the following in my Apache2.conf file.

ProxyPass /servletfolder [http://192.168.1.200:8080](http://192.168.1.200:8080)
ProxyPassReverse /servletfolder [http://192.168.1.200:8080](http://192.168.1.200:8080)
<IfModule mod_proxy.c>
ProxyRequests Off
<Proxy *>
Order allow,deny
Allow from all
</Proxy>

That works great too, the only problem is the Java application needs to hyperlink back to the normal Apache server (2.2.4) and once you routed to Tomcat it then tries to handle the php requests.  How do I get Apache to deal with the php requests again , do I need some sort of rule  to forward *.php's to port 80?

or is it possible to have both Tomcat and php installed in the same folder and have just servlets handled by Tomcat.

I tried this 

RewriteEngine on
RewriteRule ^(.*php)$ http://192.168.1.200:80/$1 [L,P]


but it doesn't work.

Please help!

---

### Post by cosmograph on 2008-02-15
Come one guys, someone must know how to do this.

The silence is deafening. Help a struggling a newbie out.:(

---

### Post by SpaceTeddy on 2008-02-15
i don't think it is possible to do what you ask in an easy fashion. Acctually, i cannot think of any setup where that would be usefull - why use servlets AND php in the same structure. 

The only thing i can think of is that you tell tomcat to kick back into a folder which is not in the servletsfolder.... i.e. call it phpfolder. So basicially have two sites which interact with each other...

i really don't see any other way, sorry...

---

### Post by cosmograph on 2008-02-15
Hi Space teddy thanks for replying :)



The reason for running for servlets and PHP should be obvious.  I have a standard PHP/MySQL  application but I want to handle the mapping side of the application using a JAVA servlet.  I just want to refer the servlet requests to TOMCAT which I can do , but I can't then get back to handle PHP requests.

It can't be that difficult as every commerical web host that offers JAVA hosting with LAMP install manages to configure it this way.


> The only thing i can think of is that you tell tomcat to kick back into a folder which is not in the servletsfolder

Thats exactly what I want to do. How do I do it, please tell me!

---

### Post by SpaceTeddy on 2008-02-16
if i am not mistaken, the requests still pass thought the apache server... so... if you have a   href that will be outside your tomcat it should work... maybe :(

lets say your tomcat ist cofigured to redirect http://webserver/servletfolder to the tomcat... 
what happens if you put a link in the servlet container saying http://webserver/phpcontainer ?

will that still be processed by the tomcat, allthought apache (which still passes the request on) should not do so, since it is outside the proxy config ? i have no test setup here, but i don't see a reason why it should not work... 

just try to put a link in the servlet that is outside the /servletfolder (maybe you need to do absoult linking... what is ugly, but neccessary)

and now, i am out of ideas :)

---

