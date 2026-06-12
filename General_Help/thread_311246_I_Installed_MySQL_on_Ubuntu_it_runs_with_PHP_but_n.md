---
title: "I Installed MySQL on Ubuntu it runs with PHP but not mysqladmin"
date: 2006-12-02
forum: General Help
---

### Post by Scottty on 2006-12-02
Hi 

Well I have made Ubuntu my main O/S and I have successfully installed PHP,Apache and MYSQL

I can access my MySQL with PHPAdmin however when I try to run mysqladmin with the command line 
```

 mysqladmin version

```

I get 

```

scott@scott-desktop:~$ mysqladmin version
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'user'@'localhost' (using password: NO)'


```

However if I use 
```
 
mysql -u root -p

```

I actually get the mysql prompt and I'm able to create Databases and grant
priveleges. 

Why does it work sometimes but not the other. I probably haven't set up the privilaged users correctly, however I have tried to add a user and root to the database under privileges in PHPadmin and they  actually show up.

What do you think is happening?

Thanks
Scott

---

### Post by KingBahamut on 2006-12-02
memory serving you have to specify a pass with myslqadmin. Have you not set your mysql root pass yet?

---

### Post by Scottty on 2006-12-02
I believe I've set a password for root for MySQL how do I tell for sur

I have this existing in phpadmin under privileges

> 

root  	localhost  	Yes  	ALL PRIVILEGES  Yes  	Edit 
root 	scott-desktop 	No 	ALL PRIVILEGES 	Yes 	Edit 
scott 	localhost 	Yes 	ALL PRIVILEGES 	Yes 	Edit 
scott 	scott-desktop 	Yes 	ALL PRIVILEGES 	Yes 	Edit 



I have 4 because I was trying to see  what would get it to work. I'm not sure which one is correct.

So do I have to set up a password for mysqladmin  itself and if I do. How do I do it?

Thanks
Scott

---

### Post by Scottty on 2006-12-02
I've solved the issue
I need to enter 
```

mysqladmin -u root -p 'and put the command here'

```
Everything seems to work great now.

---

