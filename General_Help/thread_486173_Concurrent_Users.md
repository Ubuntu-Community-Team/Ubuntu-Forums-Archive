---
title: "Concurrent Users"
date: 2007-06-27
forum: General Help
---

### Post by paulnew on 2007-06-27
Hi All

I have the Ubuntu 7.04 Feisty Fawn DVD disc.  I wanting to know how many concurrent users the apache (LAMP) server under this OS.  So I know that Win XP Home is 5 users connecting at any one time and Window XP Professional is 10 users concurrently connected.

If anyone can advise.  I am looking at get a barebone PC and installing the DVD but need to be sure before the cost that it will allow at least 20+ to access the mini website. 

Thank you

Paul

---

### Post by dfreer on 2007-06-27
Um, linux doesn't limit how many users can connect. The windows limitation is to force businesses to use Windows Server (instead of the cheaper Windows XP home/pro).

---

### Post by meatpan on 2007-06-27
I think the question is related to apache client connections, not linux users.

If you want to view or adjust the maximum number of allowed client connections, look in the file /etc/apache2/apache2.conf. 

Before making changes, understand these options and the implications to your web server. 
 [http://httpd.apache.org/docs/trunk/](http://httpd.apache.org/docs/trunk/) has great documentation about each of the variables you will see in apache2.conf.

Here is a decent high-level explanation of some settings related to user connection managment:
[http://www.debian-administration.org/articles/188](http://www.debian-administration.org/articles/188)

---

### Post by paulnew on 2007-06-28
Thank you both for the info I will check this out.

Thank You again

---

