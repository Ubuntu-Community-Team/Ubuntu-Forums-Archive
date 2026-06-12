---
title: "how to hide the user list on login"
date: 2013-06-30
forum: General Help
---

### Post by H15 on 2013-06-30
Is there a way to hide the list of users you see on login??? like insted of it sowing the users it asks u to know and type the name of the accounts???

---

### Post by Cheesemill on 2013-06-30
Run the following commands...
```
sudo /usr/lib/lightdm/lightdm-set-defaults --hide-users true
sudo /usr/lib/lightdm/lightdm-set-defaults --show-manual-login true
```

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

---

### Post by H15 on 2013-07-01
Sweet thx thats what I am looking for will try it as soon as I get on tonight

---

### Post by H15 on 2013-07-02
Ok it works but how do i change the back ground from the pink blurr to something more ummm ....... thinking....... kick @$$

and I tryed whats on the wiki you linked but it dosnt work there is nothing in the .conf that talks about backgrounds

---

