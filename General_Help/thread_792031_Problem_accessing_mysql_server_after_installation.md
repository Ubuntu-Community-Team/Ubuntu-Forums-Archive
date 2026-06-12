---
title: "Problem accessing mysql server after installation"
date: 2008-05-12
forum: General Help
---

### Post by barefootsanders on 2008-05-12
Hey all,

I'm trying to set up LAMP on my desktop (Ubuntu - Hardy Desktop) to do some small development work.  Now I've done this before in fiesty but for some reason it's not going as smooth.  I installed apache php mysql and phpmyadmin which all install successfully.  I can go to localhost/phpmyadmin and view the login but there is no root account/password.  I tried to do:
```
mysqladmin -u root password yournewrootpassword
```
However I get:
```
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
```
in response.  Did I/am I doing something wrong?  Any help would be much appreciated.

-Barefoot

---

### Post by Monicker on 2008-05-12
Try putting the new password in quotes:

```
mysqladmin -u root password "yournewrootpassword"
```



If that does not work, verify the password is indeed blank.

```
mysql -u root -p
```


Press enter when prompted.  If the password is blank it will let you connect.

---

### Post by barefootsanders on 2008-05-12
Thanks for the quick response.  The quotes didnt work but when i ran 
```
mysql -u root -p
```
it prompted my for a password.  I put it in and it worked. I don't really know what went wrong but thanks!

---

