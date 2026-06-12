---
title: "Apache 2 changing default.html page"
date: 2007-08-02
forum: General Help
---

### Post by Priswell on 2007-08-02
I installed Apache 2 to Ubuntu 7. I want to change the index.html page in /var/www/apache2-default/ using  Bluefish. When I try to save the file, I get the following error message: Could not write file. I chmod  744, but it still won't write. What am I missing?

---

### Post by nitro_n2o on 2007-08-02
append sudo before the command 
for example to edit with Vim 
```
sudo vim /var/www/..
```
for gui's use 
```
gksudo gedit /var/www/...
```
you need to have root privileges to edit files in /var/www and sudo will give them to u

the same for bluefish

---

### Post by Priswell on 2007-08-02
When I chmod, I am root, but it won't save.

---

