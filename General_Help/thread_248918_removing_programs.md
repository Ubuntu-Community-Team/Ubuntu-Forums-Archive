---
title: "removing programs"
date: 2006-09-01
forum: General Help
---

### Post by amirji on 2006-09-01
hi

i was wondering how do you go about removing a program/application i downloaded, off my computer, say ogle?

cheers

---

### Post by taurus on 2006-09-01
Open a terminal, Applications -> Accessories -> Terminal, and type

```

sudo aptitude remove ogle
(use the same password that you use to log in...)
-or-
sudo apt-get remove ogle

```

---

