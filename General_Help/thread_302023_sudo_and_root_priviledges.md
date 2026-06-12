---
title: "sudo and root priviledges"
date: 2006-11-18
forum: General Help
---

### Post by juantovarm on 2006-11-18
Something quite strange happened, i have 2 users in my pc, "juan" and "casa". I installed ubuntu as "juan", "casa" came later. In the terminal when i use sudo it asks me for "juan" 's password. today i logged in as "casa" and again used sudo, when i typed juan's password it gave me an error, so i typed casa's password and it worked.... Isn't sudo only supposed to work with the 1st user's password? BTW i checked user and groups and "casa" doesn't have admin priviledges...

Thanks
Juan

---

### Post by taurus on 2006-11-18
As long as a user belongs to groups adm & admin, that user can use sudo no matter when you've created that user.  So, you can either find out by running "id" (without the " ") at the prompt or look in /etc/group.

```
id
-or-
cat /etc/group
```

---

