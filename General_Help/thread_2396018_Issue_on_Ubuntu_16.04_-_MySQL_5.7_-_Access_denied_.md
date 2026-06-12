---
title: "Issue on Ubuntu 16.04 - MySQL 5.7 - Access denied with all new users excluding root"
date: 2018-07-10
forum: General Help
---

### Post by pteamp on 2018-07-10
Hi ALL, 

I have set up new server with Ubuntu 16.04 and installed LEMP on it with MySQL 5.7. Everything is good excluding with MySQL login. 

I can login with "root" by [**mysql -u root -p**] on command line or phpMyAdmin. But I don't want to use root, I have created new users like
```
bill with hostname=localhost and grant basic permissions
bill2 with hostname=% and grant full permissons

```when I tried to connect from command line or phpMyAdmin, I got error: 
```
ERROR 1045 (28000): Access denied for user 'bill'@'localhost' (using password: YES)
ERROR 1045 (28000): Access denied for user 'bill2'@'localhost' (using password: YES)
mysqli_real_connect(): (HY000/1045): Access denied for user 'bill'@'localhost' (using password: YES)
mysqli_real_connect(): (HY000/1045): Access denied for user 'bill2'@'localhost' (using password: YES)

```

I tried research more time but I haven't fixed problem yet. Could you provide me any solutions, please? Thanks so much!

Best regards, 
Pteam Tech

---

