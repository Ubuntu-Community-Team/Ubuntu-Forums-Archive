---
title: "Installed Apache, no www-data user"
date: 2008-04-28
forum: General Help
---

### Post by r-mo on 2008-04-28
Hi, I just installed apache on a fresh install of hardy and it didn't create a www-data user and /var/www is owned by root.  Is this right? Is it just me?

---

### Post by justleen on 2008-04-28
thats right. default owner is root of /var/www/
you can change that to another user if you like.

---

### Post by r-mo on 2008-04-28
Ah, ok, never used to be like that, had me a bit confused
```
sudo useradd -r www-data
```
To create the user?

---

### Post by justleen on 2008-04-28
-r is not a valid option..
```

sudo useradd www-data 
``` is enough.

---

### Post by r-mo on 2008-04-28
useradd --help says:
```
 -r, --system			create a system account
```

---

### Post by justleen on 2008-04-28
that funny.. i checked the man page, and -r is not mention there..

---

