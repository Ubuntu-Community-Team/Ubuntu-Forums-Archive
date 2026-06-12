---
title: "Can't Delete User in Xubuntu 12.10"
date: 2012-11-25
forum: General Help
---

### Post by AmazingDinnerBoi on 2012-11-25
Hey, I'm new to the forums, and have a problem with Xubuntu 12.10. I  accidentally messed up the top panel and decided to create a new user.  Now every time I go to my settings to delete that account, it asks me  for the root password. It never made me set up a root password in the  Xubuntu 12.10 setup! Can someone help me with this problem? :confused:

---

### Post by Elfy on 2012-11-25
Use your password. 

Your password gives you root rights assuming yours was the first account.

---

### Post by AmazingDinnerBoi on 2012-11-25
It just says the authentication attempt is wrong. And BTW, I'm trying to delete the first account.

---

### Post by steeldriver on 2012-11-25
Did you give admin permissions to your new user account when you created it? if not, you will need to log in as your original user and do that first

```
sudo gpasswd --add *yournewuser *sudo
```If you can't access the original account any longer, you will need to boot to the recovery console and fix things from there

---

