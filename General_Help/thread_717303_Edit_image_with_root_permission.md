---
title: "Edit image with root permission"
date: 2008-03-06
forum: General Help
---

### Post by psychofish25 on 2008-03-06
I want to edit some of my desktop icons to make them look cleaner, yet it always says permission denied, even when I use sudo to move them to my desktop, I cannot save my changes. How can I change the permissions of the images so I can edit them.

Thanks,
Jordan

---

### Post by boeing777 on 2008-03-06
terminal:

sudo nautilus

will give you full root power file browser

---

### Post by m.musashi on 2008-03-06
Not sure, but if you used sudo to move them then root still owns them. Try using chown to make you the owner (but don't chown the originals).

```
sudo chown username:username /path/to/file
```

---

### Post by m.musashi on 2008-03-06
> **boeing777 said:**
> terminal:

sudo nautilus

will give you full root power file browser

gksudo nautilus would be a bit safer for a gui app.

---

