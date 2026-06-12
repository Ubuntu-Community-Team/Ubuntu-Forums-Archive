---
title: "permissions problem"
date: 2008-05-24
forum: General Help
---

### Post by gammyhand on 2008-05-24
I am trying to install typo3 on my LAMP server and it is telling me I don't have permission to view the page.

I am logged in as ralph and the details for the directory are below...what should they be?

drwxrwx--- 4 root root 4096 2008-05-24 14:49 fileadmin
-rw-r--r-- 1 root root   20 2008-05-24 15:05 phpinfo.php
lrwxrwxrwx 1 root root   15 2008-05-24 14:49 t3lib -> typo3_src/t3lib
lrwxrwxrwx 1 root root   15 2008-05-24 14:49 typo3 -> typo3_src/typo3
drwxrwx--- 4 root root 4096 2008-05-24 14:49 typo3conf
lrwxrwxrwx 1 root root   18 2008-05-24 14:49 typo3_src -> ../typo3_src-4.2.0
drwxrwx--- 2 root root 4096 2008-05-24 14:49 typo3temp
drwxrwx--- 5 root root 4096 2008-05-24 14:49 uploads

I can open phpinfo.php fine just not anything else in the folder??

---

### Post by gammyhand on 2008-05-25
Bump.

---

### Post by bwhite82 on 2008-05-25
I know a lot of folks are looking for "instant gratification", however, please familiarize yourself with permissions in linux, especially if you're running a server:
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

---

### Post by sisco311 on 2008-05-25
Did you read [this]("http://ubuntuforums.org/showthread.php?t=542893") HowTo?

I'm not sure, but I think you need to change the owner and group of the files to www-data. And add your user to the www-data group.

---

### Post by gammyhand on 2008-05-25
> **Soldierboy said:**
> I know a lot of folks are looking for "instant gratification", however, please familiarize yourself with permissions in linux, especially if you're running a server:
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

I am familiar with the permissions. That is why I am asking what is wrong. They look fine to me.

I should have said by the way, I have tried chgrp to www-data before posting and that didn't work either.

However, I didn't add my user to www-data group and that seems like a likely explanation. Thanks for the advice :)

---

### Post by p_quarles on 2008-05-25
Those permissions are not fine. The file is only readable and writable as root. Adding your user to www-data won't have any impact on the web server's ability to read the file, either. Those files should be *owned* by www-data, which is the user that operates the web server. 

The quick-and-dirty way to get this working, though, would be:
```
sudo chmod a+r /var/www/typo3conf
```

---

### Post by gammyhand on 2008-05-25
> **p_quarles said:**
> Those permissions are not fine. The file is only readable and writable as root. Adding your user to www-data won't have any impact on the web server's ability to read the file, either. Those files should be *owned* by www-data, which is the user that operates the web server. 

The quick-and-dirty way to get this working, though, would be:
```
sudo chmod a+r /var/www/typo3conf
```

I should have said everything I had tried in my first post sorry.

I have tried logging in as root (I enabled the account so I could do it through GDM) and it didn't work.

I will try the quick and dirty way. This is only my home dev server so it doesn't really matter.

I leave the web based servers to our linux professionals at work.

---

### Post by p_quarles on 2008-05-25
> **gammyhand said:**
> I have tried logging in as root (I enabled the account so I could do it through GDM) and it didn't work.
This is where you are misunderstanding: the user you are logged in as is not responsible for running the web server. In Debian and its derivatives, the Apache server is run by the user named "www-data." If that user doesn't have the right to access the files it's supposed to be serving, it won't work right. 

The files need to be owned by the web-server user, not a human user.

---

### Post by gammyhand on 2008-05-25
> **p_quarles said:**
> This is where you are misunderstanding: the user you are logged in as is not responsible for running the web server. In Debian and its derivatives, the Apache server is run by the user named "www-data." If that user doesn't have the right to access the files it's supposed to be serving, it won't work right. 

The files need to be owned by the web-server user, not a human user.

I have already said a couple of posts ago I have tried chgrp to www-data to no avail.

At work those same permissions work fine and they are assigned to www-data group and root user.

---

### Post by sisco311 on 2008-05-25
Did you log out and log in after you add your user to the www-data group?

---

### Post by p_quarles on 2008-05-25
> **sisco311 said:**
> Did you log out and log in after you add your user to the www-data group?
That would not solve the problem. 

To the OP: the Apache server needs to be restarted before system changes will take effect:
```
sudo /etc/init.d/apache2 restart
```

---

### Post by p_quarles on 2008-05-25
> **sisco311 said:**
> Did you log out and log in after you add your user to the www-data group?
That would not solve the problem. 

To the OP: the Apache server needs to be restarted before system changes will take effect:
```
sudo /etc/init.d/apache2 restart
```

---

### Post by Gunman1982 on 2008-05-25
When you did this chgrp did you write sudo in front of it or did you execute it as root. And what did the command respond, didn't work isn't really a helpfull information.

---

