---
title: "Thunar source installer"
date: 2006-11-02
forum: General Help
---

### Post by BleuKousuke on 2006-11-02
hi,

I've seen on the website of thunar that there is a source installer for thunar.
But I can't find it on edgy
Do i've got to install something or is it already included?
anyways I can't find it.

help, please

---

### Post by Iarwain ben-adar on 2006-11-02
Hi,
try this```
sudo aptitude install thunar       
```

If that doens't work, [try enabling the multiverse repo's]("https://help.ubuntu.com/community/Repositories/Ubuntu"), and do this
```
sudo aptitude update && sudo aptitude install thunar
```


Iarwain

---

