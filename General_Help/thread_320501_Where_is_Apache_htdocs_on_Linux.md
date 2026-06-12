---
title: "Where is Apache htdocs on Linux"
date: 2006-12-17
forum: General Help
---

### Post by Scottty on 2006-12-17
Hello

I have successfully installed Apache web server on Ubuntu. When I used to run apache on windows I stored my online content in htdocs. However when I try and do a search I can't find it anywhere on the filesystem. Does it use a different directory on Linux?

thanks
Scott

---

### Post by ayoli on 2006-12-17
default apache document root under linux is usually /var/www (you need to grant root privileges to write in this dir, use sudo)
if you use userdir module you can also store them to ~/public_html

---

### Post by chalex on 2006-12-17
For any debian package, the documentation goes into /usr/share/doc/package_name/

Why not just use the online documentation? [http://httpd.apache.org/docs/](http://httpd.apache.org/docs/)

---

### Post by az on 2006-12-17
> **Scottty said:**
> Hello

I have successfully installed Apache web server on Ubuntu. When I used to run apache on windows I stored my online content in htdocs. However when I try and do a search I can't find it anywhere on the filesystem. Does it use a different directory on Linux?

thanks
Scott

****Edit:
Whoops!  I think I misunderstood your question.  I guess I dunno.  What do you mean by storing content in htdocs?


*******
Install apache2-doc

There is no need for the docs to be installed on a production server, so the packages are split up accordingly.

---

### Post by Scottty on 2006-12-17
Basically I just wanted to know what file to save my html and php pages to view on Localhost with my apache web server. 

So would that be /var/www/ ?

Thanks
Scott

---

### Post by chalex on 2006-12-17
You should look at /etc/apache2/apache2.conf and see what the DocumentRoot is set to.  e.g. `grep DocumentRoot /etc/apache2/apache2.conf`

You should also read the documentation for the package in /usr/share/doc/apache2/ because it will explain things like this.

---

### Post by tminuszero on 2006-12-17
Yes, /var/www is the answer you're looking for. You can always manually make a htdocs folder and then, as chalex wrote, change your apache configuration to that if that makes you more comfortable.

---

