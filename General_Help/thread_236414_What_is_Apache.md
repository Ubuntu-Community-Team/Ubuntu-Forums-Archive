---
title: "What is Apache?"
date: 2006-08-14
forum: General Help
---

### Post by UltraSonicSite on 2006-08-14
So I was surfing the web when I saw a webpage that talks about apache. It said something along the lines of it being a server, and that I could host my  own website for free. Now, assume I am the noobiest person here, I know absolutely nothing about running servers, and please answer these questions:

1. What exactely can I do with apache?
2. If I have my own server does that mean I can have my own free domain name?
3. Can I host an entire website on it for other people to connect to through the internet on it?
4. Are there any tutorials for the newbies like me out there? That work on apache2.



----Thanks----
23meg

---

### Post by 23meg on 2006-08-14
> 1. What exactely can I do with apache?You can serve files via the HTTP protocol locally and on the internet.
> 2. If I have my own server does that mean I can have my own free domain name?No, only your own hosting space.
> 3. Can I host an entire website on it for other people to connect to through the internet on it?Yes.
> 4. Are there any tutorials for the newbies like me out there? That work on apache2.[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by UltraSonicSite on 2006-08-14
5. How do I install LAMP?

---

### Post by Mr_Congeniality on 2006-08-14
on a unrelated note, wasn't that one guy from "The Matrix" named "Apache"?

---

### Post by UltraSonicSite on 2006-08-14
> **UltraSonicSite said:**
> 5. How do I install LAMP?
Scratch that.

---

### Post by UltraSonicSite on 2006-08-14
> **Mr_Congeniality said:**
> on a unrelated note, wasn't that one guy from "The Matrix" named "Apache"?

Dunno, on an unrelated note, I'm watching the matrix right now.

---

### Post by Mr_Congeniality on 2006-08-14
lmao what a cowink-e-dink!

---

### Post by UltraSonicSite on 2006-08-14
6. How do I set a root password for MySQL?
7. How do I create a database for MySQL?
8. How do I create a username and password for MySQL?

---

### Post by 23meg on 2006-08-14
Install [PHPMyAdmin]("http://www.phpmyadmin.net/") ```
sudo apt-get install phpmyadmin
```and type [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) in your browser.

---

### Post by UltraSonicSite on 2006-08-14
9. Can I set these details from [http://localhost/phpmyadmin/?](http://localhost/phpmyadmin/?) If so, what is the default login to change the info. If not, which configuration file has the details?

---

### Post by 23meg on 2006-08-14
You should be able to. I haven't done it myself in Ubuntu but install PHPMyAdmin and see.

---

### Post by UltraSonicSite on 2006-08-14
10. What is the account name and password for the login menu?

---

### Post by kaens on 2006-08-14
If you haven't set a password for php, the username and pass should both be blank.

You might want to check out [xampp](http://www.apachefriends.org/en/xampp.html)

It comes with everything you need to set up a webpage (minus a domain name of course) - Apache, PHP, MySQL, phpmyadmin, a few other things. It's a really simple install, and the install process is lined out step-by-step on their site.

---

### Post by cptnapalm on 2006-08-15
default user: admin
there is no default password.

You are trying to set up a MySQL server backed webpage on your first outing?

---

### Post by jimmygoon on 2006-08-15
Just as a heads up, my ISP blocks all HTTP access to my PC, not just port 80... any type of HTTP Request coming at my PC is blocked so... yea...

---

### Post by UltraSonicSite on 2006-08-15
Actually, I'll just settle with [http://www.lifelesspeople.com](http://www.lifelesspeople.com) lol

Too complicated for me.

---

