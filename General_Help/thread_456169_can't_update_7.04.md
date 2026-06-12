---
title: "can't update 7.04"
date: 2007-05-27
forum: General Help
---

### Post by rab4567 on 2007-05-27
I get an error message every time I try to update my feisity.

This is what i get - E. dpkg was interrupted you must manually run ' dpkg - configure - a' to correct the problem. E_ cache - > open () failed, please report.

What must I do?

---

### Post by taurus on 2007-05-27
Try

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
```

---

### Post by rab4567 on 2007-05-27
thanks it worked!

---

