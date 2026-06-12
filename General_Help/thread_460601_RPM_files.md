---
title: "RPM files"
date: 2007-05-31
forum: General Help
---

### Post by Akina on 2007-05-31
Does Ubuntu Support RPM files? if so how do i go about installing them thx

---

### Post by jfinkels on 2007-05-31
> **Akina said:**
> Does Ubuntu Support RPM files? if so how do i go about installing them thx

Convert the .rpm to a .deb file using the program 'alien'.
```
sudo aptitude install alien
alien *filename*.rpm
```

---

### Post by taurus on 2007-05-31
Yeah but it would be better if you get the .deb extension.  However, you can install .rpm with

```
sudo aptitude install alien
alien **filename.rpm**
sudo dpkg -i **filename.deb**
```

---

