---
title: "All .htaccess files generate 500 errors"
date: 2014-12-01
forum: General Help
---

### Post by astarmathsandphysics on 2014-12-01
I have reinstalled apache2 and am now reenabling my websites, but each enabled websites returns a black page in a browser. 
What is happening?

===
Apache 2.4.10 

===
Now think the problem may be with php.
when I try to load a page in php the broser tries to load a file

===
Every line in apache access log shows a 500 error 

===
Something to do with .htaccess
When I deleted them, my sites loaded 

===
Something to do with .htaccess
When I deleted them, my sites loaded 

===
How do I fix this so I don't get the errors? 

===
Think related to apache modules.
Am finding which apache modulkes to install.

---

### Post by CharlesA on 2014-12-01
Check the apache log in /var/log/apache2 and see what it says.

It could be something as simple as not having the rewrite module enabled or screwy permissions, but without looking at the logs, you will not know where to look.

---

### Post by mörgæs on 2014-12-02
Threads merged. Please don't create multiple threads on the same or closely related topics.

Repeat posting in the same thread is not welcome either. I have merged your eight posts into one. If you have the latest post in a thread and want to add something please use the Edit button.

---

### Post by SeijiSensei on 2014-12-02
Use of the .htaccess file is disabled by default.  Unless you are hosting sites for others who need to use an .htaccess file to control Apache options, move any directives in .htaccess into the virtual host configuration files in /etc/apache2/sites-available.

To enable .htaccess, you need to change the default "Allow Override" setting in the <Directory> stanza of each virtual host, or create a default entry for "<Directory />".  Read this for details: [http://httpd.apache.org/docs/current/mod/core.html#allowoverride](http://httpd.apache.org/docs/current/mod/core.html#allowoverride)

---

### Post by astarmathsandphysics on 2014-12-07
I fixed this problem.
I had reinstalled apache without enabling .htaccess

---

### Post by mörgæs on 2014-12-07
Please mark the thread 'solved'.

---

