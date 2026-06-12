---
title: "how do I get my graphical log-in back? [Resolved]"
date: 2007-01-16
forum: General Help
---

### Post by Schick on 2007-01-16
Hello. After yesterday's updates (who knows what...) I don't see the graphical log-in screen. Instead I have to log in in text mode and then I have use startx. How do I get the graphical log-in back? Can anybody help? Thanks, Christian

---

### Post by taurus on 2007-01-16
```
sudo aptitude update
sudo aptitude install gdm
sudo /etc/init.d/gdm start
```

---

### Post by Schick on 2007-01-16
Excellent. Thanks a lot!

---

### Post by taurus on 2007-01-16
> **Schick said:**
> Excellent. Thanks a lot!

Got your gdm back then!

---

