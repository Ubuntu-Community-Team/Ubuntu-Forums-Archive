---
title: "Ubuntu Server &quot;Sub-Websites?&quot;"
date: 2008-01-22
forum: General Help
---

### Post by xelapond on 2008-01-22
Hello again, 

I have registered a domain name, and I was wondering if the following is possible.

If I go to [www.example.com](www.example.com) it takes me to a basic web page.
If I go to wiki.example.com it takes me to the wiki
if I go to db.example.com it takes me to the database

Each of those being on a different server.  Is that at all possible without registering more domain names?

Thanks, 

Alex

---

### Post by frankos44 on 2008-01-23
Hi

It is fairly simple to cerate virtual host files and place them into /etc/apache2/sites_available.
Once placed there you can:

$ cd /etc/apache2/sites-availabe

STOP a virtual host
$ sudo a2dissite myVirtualHost1 
$ /etc/init.d/apache2 reload

START a virtual host
$ sudo a2ensite myVirtualHost1 
$ /etc/init.d/apache2 reload

I find having virtual hosts OK but it gets tricky with SSL certificates. An alternative approach can be done under software where all the sites share the same SSL certificate and it saves having to maintain the virtual host files. I have discussed this on a previous post:

[http://ubuntuforums.org/showthread.php?t=615467](http://ubuntuforums.org/showthread.php?t=615467)

---

### Post by erichmj on 2008-01-23
You could also look into wildcard dns, and just handle sub-domains through a scripting language, like python or php.

---

### Post by frankos44 on 2008-01-23
is that essentially what i described, if not tell me more please

---

