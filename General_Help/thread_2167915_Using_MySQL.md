---
title: "Using MySQL"
date: 2013-08-15
forum: General Help
---

### Post by stewart2 on 2013-08-15
I have MySQL running but I (that is, the user I am logged in as) have no rights. Neither do I have rights to grant rights to anyone else. I cannot log in as "-u root" as this demands a password (in spite of documentation saying it doesn't). I need someone to tell me how to move forward. I've been at this for a week now!
How to: create a user that has rights to create a user, that will have all rights.
Thanks,
Stewart

---

### Post by Lars Noodén on 2013-08-15
When you installed the package mysql-server did you set the mysql root password?  The installation process reminds you to twice. You can connect like this:

```

mysql -u root -p mysql

```

It will prompt for the password, but if you have no password yet just press return.  It would be a good idea to set the password if it was not set during the installation.

```

mysqladmin -u root password 'foobar'

```

---

### Post by stewart2 on 2013-08-15
I think the problem is that I did set a password during installation, and now I don't remember what it is! If the installation prompted me for one then I will have put in one. I'll try a few others! At the moment it asks for a password, and I always get Access Denied. Sounds like it may be my fault.
 Thanks for the quick reply.

---

### Post by stewart2 on 2013-08-15
Hey hey! I tried a few, and found one that worked! Success.

---

