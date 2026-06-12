---
title: "mounting samba share with user write access"
date: 2006-12-17
forum: General Help
---

### Post by citrusfizz on 2006-12-17
hey all

i have a share on another computer that i want to be able to make changes in the mount with a regular user...

meaning if i open up a konqueror and go to the share i want to me able to creat directories and write and what not..

so far the only think i can do is open up konqueror as root  and that works 
i have tried this trick

sudo chmod ug+s /usr/bin/smbumount
sudo chmod ug+s /usr/bin/smbmnt

trick  but it doesn't seem to work 
but then i i get this 
libsmb based programs must *NOT* be setuid root.

any help would be appreciated

---

### Post by ayoli on 2006-12-17
i have smbmnt suidroot and it works, make sure you haven't suidroot on /usr/bin/smbmount. when smbmount is suidroot it gives you the error message you had

---

### Post by citrusfizz on 2006-12-17
how do i set it back?

---

### Post by ayoli on 2006-12-17
> **citrusfizz said:**
> how do i set it back?

```
sudo chmod u-s /usr/bin/smbmount
```

---

