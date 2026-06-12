---
title: "How to open working directory in nautilus from terminal..."
date: 2008-01-24
forum: General Help
---

### Post by ntowakbh on 2008-01-24
This doesn't compare with any tutorial I've seen here, but I am still posting it because it took me awhile to figure it out. So it's more of a tip.

I tried the following:
```
nautilus pwd
pwd | nautilus
```
neither of those worked, and I finally was able to figure out how to do it.

```
nautilus $(pwd)
```

---

### Post by K.Mandla on 2008-01-25
Moved to General Help.

---

### Post by Azaphan on 2008-01-25
Try "nautilus . " .

---

