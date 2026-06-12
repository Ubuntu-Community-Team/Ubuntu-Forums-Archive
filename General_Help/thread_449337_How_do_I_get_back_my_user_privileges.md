---
title: "How do I get back my user privileges?"
date: 2007-05-20
forum: General Help
---

### Post by padmanabh on 2007-05-20
I changed some of my user privileges by mistake and now i can't perform some administrative tasks....i cant even see the "users and groups" menu i used to see before...:D

Is there any way to get those back? (I use Feisty...)...I can however do "sudo" but the command on which i do it(...say synaptic/aptitude) does not allow it anymore ....

Also, although i can't login to GDM as root, I CAN however start a root shell in console with "su" ...is that of any help?...how do i get back my previous privileges?:(

---

### Post by zvacet on 2007-05-20
Boot in recovery mode and type this

```
adduser your_user_name admin
```

---

### Post by padmanabh on 2007-05-20
gee...that was simple...thanks...:D

---

