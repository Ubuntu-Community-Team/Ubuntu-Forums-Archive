---
title: "Web Server for Linux"
date: 2008-03-06
forum: General Help
---

### Post by b10nutz on 2008-03-06
I want to switch form Xp to Ubuntu and i  want to know what webservers are avilabe for linux, i need something easy to install and start just like the [appserv]("www.appservnetwork.com") for windows.
I found something, [XAMPP for Linux ]("http://www.apachefriends.org/en/xampp-linux.html#381")  but:
Here a list of missing security in XAMPP: 

The MySQL administrator (root) has no password. 
The MySQL daemon is accessible via network. 
ProFTPD uses the password "lampp" for user "nobody". 
PhpMyAdmin is accessible via network. 
Examples are accessible via network. 
MySQL and Apache running under the same user (nobody). 

and i don't think i can use this  i need mysql data base to be protected not accesible for everyone.........
 
Thx

---

### Post by Distro Jockey on 2008-03-06
Nanoweb is in the Ubuntu repos and may do what you need, but I'm not sure it is maintained much lately (latest version is 2.2.8 [2006-08-10]).
If you do a Google search for: Ubuntu LAMP  ;you should get quite a few howto's on how to set up Linux, Apache, MySQL and PHP (or Perl or Python). Apache being the web server that is probably one of the most common web servers in use.

---

### Post by redenex on 2008-03-06
Apache would be the best choice.

---

### Post by louieb on 2008-03-06
[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Doesn't get much simpler.
```
sudo tasksel install lamp-server
```

---

### Post by ayoli on 2008-03-06
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) describes how to install the lamp stack on ubuntu (even if it's wrotten for 7.04, it worked for me with 7.10).
By default mysql is bind only to localhost (unreachable by others computer on the network).
Some of the minimal config steps are also explained is this page.

---

### Post by b10nutz on 2008-03-06
Thank you all for the fast replays

---

