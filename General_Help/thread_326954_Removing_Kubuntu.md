---
title: "Removing Kubuntu"
date: 2006-12-28
forum: General Help
---

### Post by drito on 2006-12-28
I have installed Kubuntu 6.10. Then I added Gnome using:

```
sudo aptitude install ubuntu-desktop
```

Now I am not able to configure Konqueror settings for users, I can do it only for root, so I want to get rid off Kubuntu desktop, and use only Ubuntu. But when I tried:

```
sudo aptitude remove kubuntu-desktop
```

nothing happened. Is it because I installed Kubuntu first so I can't remove it and stay with Gnome only?

---

### Post by meng on 2006-12-28
It is because kubuntu-desktop wasn't installed using aptitude. Solution here:
[www.psychocats.net/ubuntu/puregnome](www.psychocats.net/ubuntu/puregnome)

---

### Post by drito on 2006-12-28
Thanks a lot!

---

