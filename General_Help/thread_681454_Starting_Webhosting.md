---
title: "Starting Webhosting"
date: 2008-01-29
forum: General Help
---

### Post by JuggaloN9NE11 on 2008-01-29
what version of ubuntu linux do i use to start a webhosting server? and how would i start one with php, mysql, email, perl, and everything else a normal server would contain

---

### Post by empthollow on 2008-01-29
The ubuntu that was created for this purpose is ubuntu server.  durring the install it will give you the option to install LAMP Linux Apache(web server) Mysql(database) Php.  keep in mind that there is no desktop environment and no x11 installed by default.  you can install it if you like but it is not out of the box.  As for email, [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) is a nice guide to do so.  Are you starting a web server company or doing it for personal use?

---

### Post by JuggaloN9NE11 on 2008-01-29
> **empthollow said:**
> The ubuntu that was created for this purpose is ubuntu server.  durring the install it will give you the option to install LAMP Linux Apache(web server) Mysql(database) Php.  keep in mind that there is no desktop environment and no x11 installed by default.  you can install it if you like but it is not out of the box.  As for email, [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) is a nice guide to do so.  Are you starting a web server company or doing it for personal use?


it would be personal/ for a couple friends for free

but im not good with commands so how would i get mysql and emailing software on there as well? 

can i do this with the gui version and still be just as secure?

because i can install everything perfectly fine with the gui version and it would be easier

would the gui version be as secure?

---

### Post by empthollow on 2008-01-29
you can use any ubuntu distro and to the best of my knowledge it is just as secure as ubuntu server.  the difference is that the gui will 1. possibly slow down the computer 2. allow more reasons for the system to crash simply because of all that additional sofware that is running.  To speak to reason 2, i have found ubuntu beta releases to be twice as stable and less buggy than windows final releases so i wouldn't worry about stability, especially if you are not selling web space.  

To use the gui, go to system -> administration -> synaptic
you can click on any package and start typing the name and it will take you to that package.  here are the packages you need to install to get a web server up and running.

apache2
mysql-server-5.0
php5

i am running gutsy so if you are using a different version then the package names may or may not be slightly different.  i haven't got around to messing with an email server much.  the most i did was install postfix which is a mail delivery app and i used it in conjunction with zen-cart so that i could send email.  I had no problems with it but it so only one piece of a fully functional mail system.  I was intersted enough to find the tutorial but i never got around to trying it out.

---

### Post by JuggaloN9NE11 on 2008-01-29
ok thanx alot, you help tremendously

---

### Post by empthollow on 2008-01-29
keep me posted on how it's going and let me know how the mail server works out.  OH, one other thing.  don't run ssh or if you do have a very, very secure password because i actually had someone hack my computer and use it for spam when i had my server on the www.  My ISP was not happy about this but luckly my roomate used to work the them so it got swept under the table.

---

### Post by JuggaloN9NE11 on 2008-01-29
ok thanx for the tip, and i will  keep you posted

---

