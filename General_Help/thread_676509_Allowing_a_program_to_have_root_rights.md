---
title: "Allowing a program to have root rights"
date: 2008-01-23
forum: General Help
---

### Post by werg on 2008-01-23
Hi, I posted this earlier but it seems as though my thread was forgotten into oblivion. I have a program that needs to be able to create and erase files in a certain directory. Problem is, it doesn't have the necessary access. I really just want to authorize the program to do whatever it needs to in that directory. How do I do that?

Thanks

---

### Post by Borbus on 2008-01-23
You shouldn't run the program as root. Just give it the necesasary permissions. Set the directory chmod 777 if you have to.

You can use sudo, but it isn't recommended to use sudo unless you really have to.

---

### Post by nemilar on 2008-01-23
**DON'T** set the directory to 777.  That will let any user at all modify/delete the files.  

If the program is running as a specific user, then change the ownership of the directory to that user.

For example, Apache runs as www-data, so you would do:

```
chown www-data [directory] 
```

---

### Post by LaRoza on 2008-01-23
> **werg said:**
> Hi, I posted this earlier but it seems as though my thread was forgotten into oblivion. I have a program that needs to be able to create and erase files in a certain directory. Problem is, it doesn't have the necessary access. I really just want to authorize the program to do whatever it needs to in that directory. How do I do that?

Thanks

If you just have to run an app as root, use sudo or gksudo. Becareful, with great power comes great responsibility.

---

