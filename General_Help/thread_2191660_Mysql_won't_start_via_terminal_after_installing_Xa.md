---
title: "Mysql won't start via terminal after installing Xammp"
date: 2013-12-03
forum: General Help
---

### Post by IniternetDominus on 2013-12-03
Hi,

I downloaded xampp at the xammp website.

Then, I did:
 
[LIST=1]
[*]tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt
[*]sudo chmod 777 -R /opt/lampp/htdocs
[*]sudo apt-get install ia32-libs
[/LIST]

Then, I start xammp with: 

/opt/lampp/lampp start

And it starts, but when I try to use mysql using: mysql -u root -p, I get:

The program 'mysql' is currently not installed.  You can install it by typing:
sudo apt-get install mysql-client-core-5.5

Isn't mysql server, and client supposed to install, and run with xammp?

Thanks for the help,

---

