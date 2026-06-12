---
title: "Apache won't start!"
date: 2007-03-29
forum: General Help
---

### Post by brooky on 2007-03-29
I had XAMPP installed and was trying to configure it with Subversion. 

I've had a terrible time trying so I thought I'd remove Xampp and try the default Apache2 install.

I ran:> sudo apt-get install apache2

It installed. However [http://192.168.0.2](http://192.168.0.2) say it can't load the page. 
I try to start Apache with Webmin and it says > Failed to start apache : Apache does not appear to be running :

I'm running Ubuntu Server 6.10

I'm absolutelty desperate as a new employee starts work no Monday and I have to have the development environment up and running.

---

### Post by fanatik on 2007-03-29
are there any errors in /var/log/apache2/error.log ?

---

