---
title: "mysql doesn't recognise my password"
date: 2008-03-06
forum: General Help
---

### Post by LeJimster on 2008-03-06
Hi Guys/Gals,

I'm really stumped here, I've just installed mysql server and it asked me to set a password up, which i did. But when I try to enter mysql using the command

```
mysql -u root -p
```

and entering the password..

I get this error message
```

ERROR 1045 (28000): Access denied for user 'mysql'@'localhost' (using password: YES)
```

I tried resetting my password with the command:
```
sudo dpkg-reconfigure mysql-server-5.0
```

Which didn't help me. I've also tried uninstalling using:
```
sudo apt-get remove --purge mysql-server-5.0 mysql-server mysql-common
```
and then reinstalling mysql, but it just gives me the same error message :'(.

:( help please!

P.S. I'm running Ubuntu 7.10

---

### Post by MaxDaisy on 2008-03-19
The answer you are looking for can be found here
[http://ubuntuforums.org/showthread.php?t=634943&highlight=error+1045](http://ubuntuforums.org/showthread.php?t=634943&highlight=error+1045)

---

