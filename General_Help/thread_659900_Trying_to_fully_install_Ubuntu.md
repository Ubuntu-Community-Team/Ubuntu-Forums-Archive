---
title: "Trying to fully install Ubuntu"
date: 2008-01-06
forum: General Help
---

### Post by Kodge on 2008-01-06
Im trying to install Ubuntu over my windows partition so I can give that space to my current install of Ubuntu.
However I can't access Gparted. It says that only root can access it, and I thought you didn't have to log in to root in Ubuntu ( Currently using 7.10 )

---

### Post by luisromangz on 2008-01-06
Prefix the command you are going to use with sudo when you are asked for root privileges.

---

### Post by knutschr on 2008-01-06
You must open it as root
```
gksu gparted
```

---

