---
title: "ksh automatically"
date: 2018-12-25
forum: General Help
---

### Post by lawrence_hickey on 2018-12-25
just got my new dell 7530 with umbuntu 16.04.  I installed ksh but how do i make terminals automatically start ksh not bash? .profile. .ksh  .bashrc ??

---

### Post by deadflowr on 2018-12-25
*Thread moved to **General Help***

See: [https://wiki.ubuntu.com/ChangingShells]("https://wiki.ubuntu.com/ChangingShells")

---

### Post by lawrence_hickey on 2018-12-25
ok answer is put exec ksh   at the end of .bashrc

---

### Post by dragonfly41 on 2018-12-25
Or toggle shell by using commands ..

```
exec bash
exec ksh
```

---

