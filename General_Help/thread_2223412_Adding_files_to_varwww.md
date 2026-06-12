---
title: "Adding files to /var/www"
date: 2014-05-10
forum: General Help
---

### Post by josephdaniel2 on 2014-05-10
Hello, everyone
I just installed LAMP using 'tasksel' so I was trying to add php files to '/var/www/' and I couldn't.Not sure how to set the permission right to paste files into '/var/www/'.
Any help will be appriciated!
Thank you!


Additinal Info
```
grumpycat@grumpycat:~$ ls -l /var/www
total 4
-rw-r--r-- 1 root root 177 May 11 06:50 index.html

```

---

### Post by aysiu on 2014-05-10
When you say *paste*, do you mean with a point-and-click user interface? If so, you can try ```
gksudo nautilus &
``` If you're on a command-line only server, you can edit that file using sudo: ```
sudo nano /var/www/index.html
``` Or, you can take ownership of /var/www: ```
sudo chown -R grumpycat /var/www
```

**More Info**: [https://help.ubuntu.com/community/ApacheMySQLPHP#Using_Apache](https://help.ubuntu.com/community/ApacheMySQLPHP#Using_Apache)

---

### Post by josephdaniel2 on 2014-05-10
It works! Thank you so much!! :D I will mark this thread as solved. :)

---

