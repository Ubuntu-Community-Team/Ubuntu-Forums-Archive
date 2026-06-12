---
title: "Where are MySQL tables from old XAMPP"
date: 2013-08-25
forum: General Help
---

### Post by Galya on 2013-08-25
I had to reinstall Ubuntu and I didn't think much of the details. So I didn't export my MySQL tables. Now I have my whole old system copied, but I don't know if there is any way to copy databases to the new installation. I tried my best, I copied everything possible, but it didn't work. Tables got in place, but they are empty. Btw I use XAMPP.

I copied files from /var/lib/mysql , from /opt/lampp/var/mysql , from /opt/lampp/lib/mysql ... 

Any ideas?

---

### Post by bkline on 2013-08-27
This looks like it might get you back on the road:

[http://serverfault.com/questions/169746/how-to-rescue-data-from-mysql-only-files-on-hdd-left](http://serverfault.com/questions/169746/how-to-rescue-data-from-mysql-only-files-on-hdd-left)

(Short version: you may just need to adjust the permissions/ownership of the files.)

---

