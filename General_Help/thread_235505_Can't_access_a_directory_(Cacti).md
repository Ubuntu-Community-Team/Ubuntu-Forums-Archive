---
title: "Can't access a directory (Cacti)"
date: 2006-08-13
forum: General Help
---

### Post by MatsB on 2006-08-13
Hi,

I've just installed Cacti on Ubuntu 6.0.6 using this guide [https://wiki.ubuntu.com/CactiHowTo](https://wiki.ubuntu.com/CactiHowTo). 

My problem now is that I can't access the /var/lib/cacti/rrd when logged in as admin user:
admin@cacti06:/var/lib/cacti$ cd rra
-bash: cd: rra: Permission denied

admin@cacti06:/var/lib/cacti$ ls -l
drwxrwx--- 2 root www-data 49152 2006-08-13 13:15 rra

During the installation Cacti, MySQL, Apache2 etc. I didn't set any password or get promted to do so for the user www-data. How can I get arround this and get access to the rra directory?

---

