---
title: "Actions on user login and logout."
date: 2007-05-05
forum: General Help
---

### Post by Joe_Bishop on 2007-05-05
I want to do something on user login and then logout. How can I do this?
Usually, I log in through GDM, but sometimes I use console login.

---

### Post by bettlebrox on 2007-05-05
You can use .login & .logout.

---

### Post by Joe_Bishop on 2007-05-06
No, this method doesn't work - I placed files .login and .logout into ~, and add to both lines like
```
echo "aaaaaaaa" > /home/user/Desktop/aaaa
```
but no file appears on the desktop

---

