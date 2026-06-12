---
title: "Problem with MySQL"
date: 2008-01-20
forum: General Help
---

### Post by william5271 on 2008-01-20
Trying to set up a LAMP server. Apache, and PHP5 is working, but can't get mysql to work. I installed it using webmin (apt-get), and while it is running and I can edit my databases and users, my php script (Joomla!) can't detect mysql. Any ideas?

the page I am having problems with is on the first page of the Joomla installation script: [http://opportunity.dynalias.net/](http://opportunity.dynalias.net/)

Any help would be appreciated.

William

---

### Post by simwiz on 2008-01-21
hi, im also trying to find a solution. 

im taking that php hsant been compiled for MySQL support? 

try phpinfo(); in your php script and search for MySQL lowwer or upper case! If there isnt a mysql module then you know php cannot parse these mysql functions.

---

